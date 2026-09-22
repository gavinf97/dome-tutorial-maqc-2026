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
    4. Know what the skill does not yet do

    **Time:** 35 minutes (hands-on exercise)

    **Prerequisite:** [Chapter 5](chapter_05_agentic.md) · Python 3.10+ · a terminal

---

!!! warning "Prototype — v0.1.0"
    Not yet benchmarked or validated. Frontier models give promising results and
    more capability than [DOME Copilot](chapter_03_copilot.md), but read and
    correct every field before you use the output.

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

!!! tip "Not just for Claude"
    `SKILL.md` is ordinary Markdown: a set of instructions any capable agent can
    read and follow. The helper scripts return their results in **JSON format**,
    which any agent can work with. Claude is simply the quickest to set up.

---

## Install

=== "Claude"

    [:material-open-in-new: Open Claude](https://claude.ai/){ .md-button .md-button--primary }
    [:material-download: Download the skill (ZIP)](https://github.com/gavinf97/dome-agent-skill/archive/refs/heads/main.zip){ .md-button }

    **In Claude Code** — two commands in a session:

    ```
    /plugin marketplace add gavinf97/dome-agent-skill
    /plugin install dome-agent-skill@dome-marketplace
    ```

    These are Claude Code commands; slash commands do not run in the browser chat.

    **In Claude in the browser** — upload the skill once, then use it in any chat:

    1. **Download the ZIP** with the button above.
    2. **Repackage it.** Unzip, rename the folder `dome-agent-skill-main` to
       `dome-agent-skill`, then zip that folder back up as `dome-agent-skill.zip`.
       The zip and the folder inside it must both be named `dome-agent-skill`, or
       Claude will not accept it.
    3. In the message box, click **+** → **Skills** → **Manage skills**, and
       upload the zip. (**Browse skills**, in the same menu, is the directory of
       ready-made skills.)
    4. Uploading your own skill needs a paid plan — Pro, Max, Team or Enterprise.
    5. The skill now appears under **+ → Skills**. Just ask for what you want,
       for example *"Assess this paper for DOME compliance: `<DOI>`"* — it
       triggers on intent, with no special syntax.

=== "Any IDE agent session"

    An **IDE** (integrated development environment) is the editor you write code
    in, such as VS Code. The agent built into it — GitHub Copilot, Gemini Code
    Assist, ChatGPT/Codex — can run this too.

    ```bash
    git clone https://github.com/gavinf97/dome-agent-skill.git
    cd dome-agent-skill
    pip install -r scripts/requirements.txt
    ```

    Then point the agent at the instructions:

    > Follow `SKILL.md` in this repository to assess the paper at
    > `<DOI or URL>` against the DOME recommendations. Use the scripts in
    > `scripts/` for the lookups and file handling. Show me the entry and the
    > notes summary.

    The agent needs two abilities: **read files** and **run commands**. That is all.

---

## Setup

```bash
# Python 3.10 or newer
python3 --version

# Three dependencies only: requests, PyMuPDF, PyYAML
pip install -r scripts/requirements.txt
```

Optionally, set `GITHUB_TOKEN` to raise the GitHub API rate limit for the
external-link check in Phase 6. It is not required.

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

Submitting straight to the DOME Registry is **not enabled**. Review the output
and take it forward yourself. A connection may follow once the approach is
validated, but that is not confirmed.

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
