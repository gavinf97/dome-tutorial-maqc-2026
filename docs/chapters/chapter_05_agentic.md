---
tags:
    - agentic AI
    - agent skills
    - frontier models
    - DOME Agent Skill
---

# 5. Agentic AI Skills for DOME

**What happens when you give a frontier model the tools, not just the prompt.**

---

!!! overview "Overview"

    **Questions:**

    - What does an "agent skill" add over a single LLM call like DOME Copilot?
    - What does the DOME Agent Skill actually do, phase by phase?
    - How does it produce DOME *and* OSAI output in one pass?
    - What does the extra capability cost, and who can realistically access it?
    - How much should I trust the output?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Explain the difference between a single-shot LLM annotation and an agentic pipeline
    2. Walk through the eight phases of the DOME Agent Skill
    3. Weigh the accuracy, cost and accessibility trade-offs against DOME Copilot
    4. State accurately what has and has not been validated about this approach

    **Time:** 10 minutes

    **Prerequisite:** [Chapter 3 — DOME Copilot](chapter_03_copilot.md) and [Chapter 4 — OSAI](chapter_04_osai.md)

---

## From a model call to an agent

[DOME Copilot](chapter_03_copilot.md) does one thing very efficiently: it takes
the text you give it and returns a structured annotation. The **agentic**
approach changes the shape of the problem — instead of one model call over one
document, a frontier model is given **tools** and left to chain them:

``` mermaid
flowchart LR
    A[DOI or URL] --> B[Resolve metadata<br/>CrossRef, EuropePMC, arXiv...]
    B --> C[Fetch full text<br/>+ supplementary files]
    C --> D[Extract text]
    D --> E[Fill 21 DOME fields<br/>with source provenance]
    E --> F[Inspect linked<br/>code repository]
    F --> G[Suggest OSAI<br/>ecosystem components]
    G --> H{Human review}
    H --> I[Submit to<br/>DOME Registry]
```

Three things follow from that shape:

1. **Ground-truth metadata comes from APIs, not the model.** Title, authors,
   journal, DOI, PMID are resolved through CrossRef, Zenodo, arXiv, bioRxiv and
   Europe PMC — so they are looked up, not recalled, and cannot be hallucinated.
2. **Supplementary material is in scope.** Many DOME fields — data splits,
   hyperparameters, evaluation files — live in supplementary PDFs rather than the
   main text. An agent can fetch and read them.
3. **DOME and OSAI in one pass.** Once the gaps are known, the agent queries the
   [OSAI ecosystem list](chapter_04_osai.md) and returns concrete components that
   would close each one. Copilot does not do this.

A frontier model's large context window is what makes this practical: the whole
paper, its supplementary files and the schema can be held at once, which reduces
the number of amendments a human has to make afterwards.

## The DOME Agent Skill

[**`gavinf97/dome-agent-skill`**](https://github.com/gavinf97/dome-agent-skill)
is an open implementation of exactly this — v0.1.0, CC BY 4.0, public
[@farrell2026skill]. The deterministic API and file work is done by six small
Python CLIs; the DOME field extraction is done by the agent reading the paper.

### The eight phases

| # | Phase | What happens |
|---|---|---|
| 1 | **Input** | Paper URL/DOI, any code repository links, and which schema version to target (default v2.0.0) |
| 2 | **Resolve metadata** | `resolve_publication.py` — CrossRef → Zenodo → arXiv → bioRxiv/medRxiv → Europe PMC, cross-referenced via the NCBI ID Converter |
| 3 | **Fetch full text** | `fetch_fulltext.py` — Europe PMC full-text XML plus supplementary files, filtered to documents under 20 MB |
| 4 | **Extract text** | `extract_pdf_text.py` — PyMuPDF, with page markers so findings stay citable |
| 5 | **Fill 21 DOME fields** | The agent reads the text and fills the schema, guided by a per-field extraction guide |
| 6 | **External check** | `inspect_external_link.py` — one API call plus README for a linked repo. Deliberately lightweight: no cloning, no walking the file tree |
| 7 | **Notes & compliance summary** | Provenance breakdown, remaining gaps, and OSAI-grounded improvement suggestions via `suggest_osai_components.py` |
| 8 | **Human review & submit** | The full entry and summary are presented for correction. `submit_registry.py --dry-run` first, always |

### What makes the output trustworthy

**Source provenance on every field.** Each filled field is tagged with where the
evidence came from:

- `paper` — stated in the manuscript itself
- `supplementary:<filename>` — found in supplementary material
- `external:<url>` — found only in a linked repository

That last tag matters more than it looks. DOME assesses **what the paper
discloses**, not what a linked repo happens to contain. A field that could only
be filled from GitHub is explicitly called out in the summary as *"not disclosed
in the paper itself"* — which is a DOME finding, not a DOME pass.

**Explicit anti-hallucination rules.** The skill is instructed never to invent a
publication detail, dataset size, metric value, licence or URL; if the evidence
is not in the API response, the paper, the supplementary files or the external
check, the field stays `null`. It is likewise forbidden from recalling OSAI
recommendation definitions from memory — it must read the source.

**Nothing is submitted without you.** Phase 8 requires explicit human
confirmation, and a dry run is shown first.

## The trade-off, stated plainly

Neither route is simply better. They optimise for different things.

| | **DOME Copilot** | **DOME Agent Skill** |
|---|---|---|
| Engine | Mistral Small 3.1 24B, self-hostable | Frontier model (Claude or comparable) |
| Scope | Main text → DOME fields | DOI → metadata, full text, supplementary, linked repo → DOME **+ OSAI** |
| Speed | ~2 min | ~5–15 min |
| Cost per paper | Very low; compute-efficient | Higher — you pay for frontier model tokens |
| Accessibility | Web UI, nothing to install | Needs Python 3.10+, a terminal and an agent platform |
| Scales to a corpus | **Yes** — this is its purpose | Not economically, at present |
| Human amendments needed | More | Fewer, in practice |
| Published benchmark | **Yes** [@farrell2026copilot] | **No** — see below |

!!! tip "Choosing between them"
    Annotating a hundred papers to build registry coverage? **Copilot.**
    Producing the best possible report for one paper — likely your own — and you
    want OSAI recommendations too? **The agent skill.** Neither removes the human
    review step.

## Status: what has and has not been shown

!!! warning "Status: community prototype — human review is required"
    The DOME Agent Skill is **v0.1.0**. Its helper scripts are implemented and
    tested against live metadata APIs, but the end-to-end pipeline has **not been
    formally validated by expert human assessment**, and the registry-submission
    step has not yet been exercised end-to-end against the production API. There
    is no automated test suite and no programmatic JSON Schema validation; schema
    conformance currently relies on the agent following the shipped schema and
    field guide. Unlike [DOME Copilot](chapter_03_copilot.md), **no published
    benchmark exists for it yet**.

    In practice, output quality with current frontier models is high — the design
    deliberately grounds every field in retrieved evidence rather than model
    recall. But that is a design argument, not a measurement. Every generated DOME
    report must be **read and corrected by a human before it is submitted, cited
    or trusted**. Treat it as an accelerator for curation, never a replacement
    for it.

This is stated deliberately, not defensively. Benchmarking an agentic pipeline
against expert curation is exactly the kind of work the MAQC community does well
— and it is an open invitation.

---

## Sources and further reading

- **The skill**: [gavinf97/dome-agent-skill](https://github.com/gavinf97/dome-agent-skill) — CC BY 4.0, v0.1.0 [@farrell2026skill]
- **Install and run it**: [Chapter 8 — Route C](chapter_08_route_agent.md)
- **Agent Skills documentation**: [docs.claude.com — Agent Skills](https://docs.claude.com/en/docs/claude-code/skills)
- **OSAI ecosystem list** (queried in Phase 7): [BioComputingUP/OSAI_ecosystem](https://github.com/BioComputingUP/OSAI_ecosystem)

---

**Next:** [Chapter 6 — Route A: Manual via the DOME Registry](chapter_06_route_manual.md)
