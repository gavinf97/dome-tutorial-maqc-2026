# Publishing Reusable AI/ML Models in the Life Sciences

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-live-brightgreen)](https://gavinf97.github.io/dome-tutorial-maqc-2026/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22900624.svg)](https://doi.org/10.5281/zenodo.22900624)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

Tutorial companion site for **MAQC 2026 Technical Tutorial P06**.

**Live site: <https://gavinf97.github.io/dome-tutorial-maqc-2026/>**

| | |
|---|---|
| Conference | MAQC Society 2026 Annual Meeting — *Precision in a Complex World* |
| Dates | 22–26 September 2026 |
| Venue | LIGHT, University of Brescia, Brescia, Italy |
| Session | **P06 — Publishing Reusable AI/ML Models in the Life Sciences** |
| Slot | Wednesday 23 September, 14:00–15:30 (MAQC Technical Tutorial Day) |
| Lead | Gavin Farrell, University of Padua / BioComputingUP |

## What the site covers

**Course content**

1. **The DOME Recommendations** — four pillars, 21 fields, requirements vs recommendations
2. **The DOME Registry** — making transparency reports findable, citable and usable in peer review
3. **DOME Copilot** — LLM-assisted, human-in-the-loop annotation at scale
4. **Open and Sustainable AI (OSAI)** — the nine recommendations
5. **Agentic AI Skills** — frontier-model agents that produce DOME *and* OSAI output

**Hands-on: submission routes**

- **Route A** — manual annotation with the DOME Wizard
- **Route B** — DOME Copilot, step by step
- **Route C** — the DOME Agent Skill, in Claude Code or any agentic assistant

**Slides:** [Google Slides deck](https://docs.google.com/presentation/d/1YyIH6UaMAw16p5z5xwGjAdpWyqXuT1-GMjMfYWFtFnU/edit?slide=id.g3fbb5ca46c4_0_934#slide=id.g3fbb5ca46c4_0_934)

## Local preview

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve          # http://127.0.0.1:8000
mkdocs build --strict # verify before pushing
```

## Deployment

Pushing to `main` triggers `.github/workflows/render_page.yml`, which runs
`mkdocs gh-deploy --force` and publishes the built site to the `gh-pages`
branch. GitHub Pages serves that branch at the URL above. The workflow also runs
weekly on a Sunday cron and can be triggered manually.

## Attribution

Built with the [ELIXIR Training Lesson Template](https://zenodo.org/records/7913092)
by van Geest G, Kronander E, Romero Herrera JA, Žlender N, ELIXIR Training
Coordination Team & Cardona A (2023), DOI
[10.5281/zenodo.7913092](https://doi.org/10.5281/zenodo.7913092), CC BY-SA 4.0.
Site structure follows [AIBIO-UK/airbds-metric-tutorial](https://github.com/AIBIO-UK/airbds-metric-tutorial),
which uses the same template.

## Licence

[CC BY-SA 4.0](./LICENSE.md) — required by the template's ShareAlike clause.

Cite as: Farrell, G. (2026). *Publishing Reusable AI/ML Models in the Life
Sciences* (MAQC 2026 Technical Tutorial P06). Zenodo.
[10.5281/zenodo.22900624](https://doi.org/10.5281/zenodo.22900624). See
[`CITATION.cff`](./CITATION.cff) for machine-readable metadata.
