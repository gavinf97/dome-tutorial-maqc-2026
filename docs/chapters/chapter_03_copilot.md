---
tags:
    - DOME Copilot
    - LLM
    - human-in-the-loop
    - curation
---

# 3. DOME Copilot

**PDF in, structured draft DOME report out — in about two minutes. Then a human reviews it.**

---

!!! overview "Overview"

    **Questions:**

    - Why does DOME curation need accelerating at all?
    - What does DOME Copilot actually do, and what model is behind it?
    - How good are its annotations compared to expert human curation?
    - Where does the human stay in the loop, and why is that not negotiable?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Explain the curation bottleneck that motivates automated DOME annotation
    2. Describe the Copilot pipeline from PDF submission to downloadable JSON
    3. Interpret the reported benchmark results, including their limits
    4. Identify which DOME fields need the most careful human checking

    **Time:** 10 minutes

    **Prerequisite:** [Chapter 1](chapter_01_dome.md) and [Chapter 2](chapter_02_registry.md)

---

## The bottleneck

Manual DOME annotation is careful work. A curator reads the paper, hunts through
supplementary material, and fills 21 fields — typically 30 to 90 minutes per
publication, and longer for an unfamiliar subfield.

Meanwhile the AI/ML life-science literature grows faster every year. The initial
DOME Registry community curation effort retrieved **over 4,000 candidate
articles** from Scopus, of which experts could annotate only a random subset
[@attafi2024registry]. That gap is structural: expert curation does not scale to
the corpus, and a registry that only ever covers a sliver of the literature
cannot answer field-level questions about reporting quality.

!!! tip "The framing that matters"
    The goal is not to remove the human. It is to change what the human spends
    their time on — from *transcription* to *judgement*.

## What DOME Copilot does

[DOME Copilot](https://dome-copilot.ifca.es/) extracts structured reports of AI
methods using a large language model to help interpret manuscripts
[@farrell2026copilot]. You give it a publication PDF; it returns a draft DOME
annotation as structured JSON, ready for human refinement and deposition in the
[DOME Registry](chapter_02_registry.md).

<div class="flow">
  <div class="flow-step"><b>Publication PDF</b><small>+ supplementary PDFs</small></div>
  <div class="flow-step"><b>DOME Copilot</b><small>DOI optional, for metadata</small></div>
  <div class="flow-step"><b>Draft annotation</b><small>structured JSON</small></div>
  <div class="flow-step flow-human"><b>Human review</b><small>read and correct every field</small></div>
  <div class="flow-step"><b>DOME Registry entry</b><small>deposited and citable</small></div>
</div>

### Under the hood

| | |
|---|---|
| **Model** | Mistral Small 3.1 24B Instruct (2503.10) — an intermediate-sized LLM |
| **Why that model** | Chosen to deliver results at speed while remaining highly capable at text summarisation and structuring — the trade-off that makes corpus-scale annotation affordable |
| **Throughput** | ~2 minutes per annotation from PDF submission, varying with document size |
| **Benchmark** | n = 222 publications (Dataset A) |
| **Prompt refinement** | System prompts improved from v0 to v2 through expert curator observation on a subset of n = 30 |
| **Agreement with humans** | BERTScore against human annotations mostly falls in the **0.35–0.50** interquartile range (1.0 = identical semantic match), indicating stable semantic similarity |

!!! info "Reading the BERTScore honestly"
    A BERTScore IQR of 0.35–0.50 indicates *stable semantic similarity*, not
    equivalence. Copilot reliably lands in the right territory for a field; it does
    not reliably produce the exact statement an expert curator would write. That is
    precisely why the human review step exists — and why the reported number is
    worth stating plainly rather than glossing.

## Where humans stay in the loop

Copilot drafts; a person decides. In practice the review effort concentrates in
predictable places:

- **Fields the paper never states.** Copilot works from the manuscript. If the
  paper is silent on redundancy reduction between splits (DOME 1.3), the correct
  output is a gap — and a draft that confidently fills it is the thing you are
  reviewing *for*.
- **Numbers.** Dataset sizes, parameter counts and metric values are worth
  checking against the source every time.
- **Availability fields.** URLs, licences and repository links (1.4, 2.8, 3.4,
  4.5) need verification that the resource actually exists and is accessible.
- **Anything that would change a reader's judgement.** If a field would alter
  how someone assesses the method, read the paper's own words for it.

!!! warning "Never deposit an unreviewed annotation"
    A machine-drafted DOME entry that nobody has checked is worse than no entry:
    it looks authoritative and carries the Registry's credibility. The Registry's
    `isAiGenerated` flag exists so that provenance is recorded — it is not a
    substitute for review.

## When to reach for Copilot

**Good fit:** annotating many papers; building registry coverage for a subfield;
getting a fast first pass on a paper you will then correct; no local setup
possible; cost matters.

**Less good fit:** a single high-stakes paper where you want the richest possible
report — for that, see [Chapter 5](chapter_05_agentic.md), which gives you DOME
*and* OSAI in one pass at higher cost per paper.

The practical, click-by-click walkthrough — including the shared workshop login —
is in **[Route B — DOME Copilot](chapter_07_route_copilot.md)**.

---

## Sources and further reading

- **Try it**: <https://dome-copilot.ifca.es/> (shared workshop login on the [Session Assets](../assets.md) page)
- **The preprint**: Farrell G, Attafi OA, Fragkouli S-C, Heredia I, Fernández Tobías S, Harrison M, Hermjakob H, Jeffryes M, Obregón Ruiz M, Pearce M, Pechlivanis N, López García A, Psomopoulos F, Tosatto SCE. *DOME Copilot: Making transparency and reproducibility for artificial intelligence methods simple.* bioRxiv, 19 April 2026. [doi:10.64898/2026.04.16.718888](https://doi.org/10.64898/2026.04.16.718888) [@farrell2026copilot]
- **Source code**: [IFCA-Advanced-Computing/dome-copilot](https://github.com/IFCA-Advanced-Computing/dome-copilot)
- **Technical issues**: <contact@dome-ml.org>

---

**Next:** [Chapter 4 — Open and Sustainable AI (OSAI)](chapter_04_osai.md)
