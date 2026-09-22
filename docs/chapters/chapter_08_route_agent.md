---
tags:
    - hands-on
    - agent skills
    - Claude
    - VS Code
    - installation
---

# Route C — Agent Skills

**Install the DOME Agent Skill into your agent of choice, point it at a DOI, and review what comes back.**

---

!!! overview "Overview"

    **Questions:**

    - How do I install the DOME Agent Skill?
    - Does it only work with Claude, or with any agent?
    - What do I need on my machine before I start?
    - What does a run look like, and what do I check afterwards?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Install the skill by whichever route fits your setup
    2. Run a DOME assessment from a DOI and read the resulting entry plus summary
    3. Interpret the source-provenance tags on each field
    4. Understand what is required before anything is submitted to the Registry

    **Time:** 35 minutes (hands-on exercise)

    **Prerequisite:** [Chapter 5](chapter_05_agentic.md) · Python 3.10+ · a terminal

---

!!! warning "Status: community prototype — human review is required"
    The DOME Agent Skill is **v0.1.0**. Its helper scripts are implemented and
    tested against live metadata APIs, but the end-to-end pipeline has **not been
    formally validated by expert human assessment**, and the registry-submission
    step has not yet been exercised end-to-end against the production API. There
    is no automated test suite and no programmatic JSON Schema validation. Unlike
    [DOME Copilot](chapter_03_copilot.md), **no published benchmark exists for it
    yet**.

    Output quality with current frontier models is high in practice, but every
    generated DOME report must be **read and corrected by a human before it is
    submitted, cited or trusted**. Treat it as an accelerator for curation, never
    a replacement for it.

---

## The repository

Everything lives in one public repository:

**<https://github.com/gavinf97/dome-agent-skill>** — CC BY 4.0, v0.1.0

```
dome-agent-skill/
├── SKILL.md                  # the 8-phase instructions the agent follows
├── references/               # DOME schemas v1.0.0 & v2.0.0, field guide,
│                             #   entry template & example, OSAI guidelines
├── scripts/                  # six standalone Python CLIs
│   ├── resolve_publication.py
│   ├── fetch_fulltext.py
│   ├── extract_pdf_text.py
│   ├── inspect_external_link.py
│   ├── suggest_osai_components.py
│   ├── submit_registry.py
│   └── requirements.txt
└── .claude-plugin/           # plugin + marketplace manifests
```

!!! tip "It is not Claude-specific"
    `SKILL.md` is **plain Markdown** and the scripts are **plain Python CLIs that
    print JSON to stdout**. Nothing in the pipeline requires a particular vendor.
    Any agentic platform that can read a file and run a shell command can follow
    it — the Claude Code path below is simply the one with a one-command installer.

---

## Install

=== "Claude Code — fastest"

    Two commands inside a Claude Code session:

    ```
    /plugin marketplace add gavinf97/dome-agent-skill
    /plugin install dome-agent-skill@dome-marketplace
    ```

    The repository is a self-hosted plugin marketplace, so this is the shareable
    path — anyone can run these two commands, no manual file placement needed.

=== "Manual — any Claude session"

    Clone the repository into your skills directory:

    ```bash
    # Personal — available in every project:
    git clone https://github.com/gavinf97/dome-agent-skill.git \
      ~/.claude/skills/dome-agent-skill

    # Or project-scoped — available only inside one project:
    git clone https://github.com/gavinf97/dome-agent-skill.git \
      <your-project>/.claude/skills/dome-agent-skill
    ```

    !!! info "Local installs are local"
        A skill placed in `~/.claude/skills/` or `<project>/.claude/skills/` is
        discoverable only by you on that machine — it is **not** visible to anyone
        else, even though the repository is public. Use the marketplace path above
        to actually share it with colleagues.

=== "VS Code — Gemini, GitHub Copilot, ChatGPT/Codex"

    Any agentic coding assistant in VS Code (or a similar editor) can run this.
    Clone the repository somewhere in your workspace:

    ```bash
    git clone https://github.com/gavinf97/dome-agent-skill.git
    cd dome-agent-skill
    pip install -r scripts/requirements.txt
    ```

    Then wire it to your agent:

    | Agent | How to connect it |
    |---|---|
    | **Gemini Code Assist / Gemini CLI** | Add `SKILL.md` as context, or copy its content into `GEMINI.md` in your workspace root |
    | **GitHub Copilot (VS Code, agent mode)** | Copy `SKILL.md` into `.github/copilot-instructions.md`, or attach it as context in Copilot Chat |
    | **ChatGPT / Codex** | Add `SKILL.md` as `AGENTS.md` in the repository root, or paste it into a project's custom instructions |
    | **Any other agent** | Tell it: *"Follow the instructions in `SKILL.md`. The scripts in `scripts/` are your tools."* |

    The agent needs two abilities: **read files** and **run shell commands**. That
    is all.

    !!! tip "Prompt that works with any agent"
        > Follow `SKILL.md` in this repository to assess the paper at
        > `<DOI or URL>` against the DOME recommendations. Use the scripts in `scripts/`
        > for the API and file work. Show me the entry JSON and the notes summary
        > before submitting anything.

=== "Scripts only — no agent"

    The six CLIs are usable directly if you would rather do the field extraction
    yourself:

    ```bash
    python scripts/resolve_publication.py "10.1038/s41592-021-01205-4"
    python scripts/fetch_fulltext.py --outdir work --pmcid PMC8340003 --doi 10.1038/s41592-021-01205-4
    python scripts/extract_pdf_text.py work/supp_1.pdf --out work/supp_1.txt
    python scripts/inspect_external_link.py "https://github.com/BioComputingUP/dome-registry"
    python scripts/suggest_osai_components.py "no containerised environment" --top 3
    python scripts/submit_registry.py entry.json --dry-run
    ```

    Each prints JSON to stdout and logs to stderr, so they compose cleanly into
    your own pipeline.

---

## Setup — needed for every route above

```bash
# Python 3.10 or newer
python3 --version

# Three dependencies only: requests, PyMuPDF, PyYAML
pip install -r scripts/requirements.txt
```

### Optional environment variables

| Variable | When you need it |
|---|---|
| `GITHUB_TOKEN` | Not required. Raises the GitHub API rate limit for the external-link check in Phase 6 |
| `DOME_REGISTRY_TOKEN` | Only for the final submission step. Log in at [registry.dome-ml.org](https://registry.dome-ml.org/) with LS Login, retrieve your JWT, then `export DOME_REGISTRY_TOKEN="..."` |

!!! info "No Docker, no services"
    There is deliberately nothing to stand up. Three Python packages and a terminal.

---

## Running it

Once installed, just ask in natural language:

> Assess this paper for DOME compliance: `https://doi.org/10.1038/s41592-021-01205-4`

Or, with more context supplied up front:

> Generate a DOME entry for DOI `10.1093/gigascience/giae094`. The code is at
> `https://github.com/BioComputingUP/dome-registry`. Use schema v2.0.0.

The agent will work through the [eight phases](chapter_05_agentic.md), then stop
and show you two things.

### What you get back

**1. The entry JSON** — conforming to dome-schema v2.0.0 (or v1.0.0 if you asked
for it), ready for the Registry.

**2. A notes and compliance summary** — *not* part of the submitted JSON, containing:

- **Provenance breakdown** — which fields came from `paper`,
  `supplementary:<file>`, or `external:<url>`. Read this first
- **Remaining gaps** — fields left `null`, with a one-line reason for each
- **Improvement suggestions** — concrete [OSAI ecosystem components](chapter_04_osai.md)
  that would close each significant gap, cited by name, URL and OSAI
  recommendation code

!!! warning "`external:` is a finding, not a pass"
    A field the agent could only fill from a linked GitHub repository is tagged
    `external:<url>` and flagged as *not disclosed in the paper itself*. That is a
    **DOME gap**, correctly identified — the recommendations assess what the publication
    discloses. Do not quietly promote those fields to `paper`.

### Submission

Nothing is submitted without you. Phase 8 requires explicit confirmation, and a
dry run comes first:

```bash
python scripts/submit_registry.py entry.json --dry-run   # shows exactly what would be sent
python scripts/submit_registry.py entry.json             # actually sends it
```

---

## When to choose this route

**Good fit:** one paper you care about, likely your own; you want DOME **and**
OSAI recommendations together; supplementary material matters; you already work
with an agentic assistant.

**Poor fit:** annotating at corpus scale (cost), no Python available, or a
context where sending the paper to a frontier model is not acceptable — use
[Route B](chapter_07_route_copilot.md) or [Route A](chapter_06_route_manual.md).

---

## Sources

- **The skill**: [gavinf97/dome-agent-skill](https://github.com/gavinf97/dome-agent-skill) [@farrell2026skill]
- **Agent Skills docs**: [docs.claude.com — Agent Skills](https://docs.claude.com/en/docs/claude-code/skills)
- **Claude Code plugins**: [docs.claude.com — Plugins](https://docs.claude.com/en/docs/claude-code/plugins)
- **The schema it targets**: [BioComputingUP/dome-schema](https://github.com/BioComputingUP/dome-schema)

---

**Next:** [Further Resources](../follow_up_training.md)
