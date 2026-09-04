# Contributing

Thanks for helping improve this tutorial. Corrections, clarifications and
additional examples are all welcome.

## Scope

This repository holds **the tutorial site only**. Issues with the underlying
projects belong in their own repositories:

| Topic | Where |
|---|---|
| The DOME standard or schema | [BioComputingUP/dome-schema](https://github.com/BioComputingUP/dome-schema) |
| The DOME Registry | [BioComputingUP/dome-registry](https://github.com/BioComputingUP/dome-registry) |
| DOME Copilot | [IFCA-Advanced-Computing/dome-copilot](https://github.com/IFCA-Advanced-Computing/dome-copilot) |
| The DOME Agent Skill | [gavinf97/dome-agent-skill](https://github.com/gavinf97/dome-agent-skill) |
| OSAI ecosystem components | [BioComputingUP/OSAI_ecosystem](https://github.com/BioComputingUP/OSAI_ecosystem) |
| Anything on this site | Here |

## Quick fixes

Every page has an edit (pencil) icon in the top right that takes you straight to
the source file on GitHub. For a typo or a broken link, that is the fastest path.

## Larger changes

1. **Fork** this repository and create a branch off `main`
2. **Edit** the relevant file under `docs/`
3. **Preview locally** before opening a PR:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   mkdocs serve            # http://127.0.0.1:8000
   mkdocs build --strict   # must pass — this is what CI effectively runs
   ```

4. **Open a pull request** against `main`, describing what changed and why

`mkdocs build --strict` fails on broken internal links and nav mismatches. Please
make sure it passes before opening a PR.

## Commit message convention

Prefix commits with the kind of change:

- `docs:` — content changes to pages
- `fix:` — corrections to errors, broken links, wrong facts
- `feat:` — new pages or new site capability
- `chore:` — dependencies, config, tidying

## Content conventions

Pages follow the ELIXIR Training Lesson Template conventions:

- Front matter contains **`tags:` only** — the page title comes from the first `# H1`
- Every chapter opens with an `!!! overview "Overview"` block containing
  **Questions**, **Learning Objectives**, **Time** and **Prerequisites**
- Use `=== "Tab label"` for branching content and `??? info` for collapsible detail
- Use `:::cards cols=2 ... :::` for link card grids
- Citations go in `references.bib` and are referenced with `[@key]`

## Accuracy standards

This tutorial makes factual claims about published research and about tooling
maturity. Please hold to the same bar:

- **Cite the source** for any factual claim, with a DOI where one exists
- **Do not overstate tool maturity.** The DOME Agent Skill is explicitly labelled
  as an unbenchmarked v0.1.0 prototype requiring human review. If that changes,
  change it because a benchmark exists — not because it feels better
- **Keep the human-in-the-loop framing.** Every automated route on this site
  requires human review before deposition, and the pages say so

## Licence

By contributing you agree that your contributions are licensed under
[CC BY-SA 4.0](./LICENSE.md), the same licence as the rest of this work
(required by the ELIXIR template's ShareAlike clause).

## Code of Conduct

Participation is governed by the [Code of Conduct](./CODE_OF_CONDUCT.md).
