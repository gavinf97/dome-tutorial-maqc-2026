---
tags:
    - further resources
    - contributing
    - community
---

# Further Resources

**Where to go after the session — and how to keep contributing.**

---

## Core resources

::cards:: cols=2

- title: "DOME"
  content: "The recommendations, the full guidelines, news and the community behind them."
  url: https://dome-ml.org/

- title: "DOME Registry"
  content: "Deposit, search and cite DOME transparency reports. ORCID sign-in."
  url: https://registry.dome-ml.org/

- title: "OSAI"
  content: "Open and Sustainable AI — the nine recommendations and the implementation pathways."
  url: https://osai.dome-ml.org/

- title: "AI Ecosystem"
  content: "300+ curated AI-relevant components, mapped to the OSAI recommendations."
  url: https://dome-ml.org/ai-ecosystem

- title: "DOME Copilot"
  content: "LLM-assisted DOME annotation. Login details are on the Session Assets page."
  url: https://dome-copilot.ifca.es/

- title: "DOME Wizard"
  content: "The DOME questionnaire on ELIXIR's Data Stewardship Wizard."
  url: https://dome.dsw.elixir-europe.org/wizard/

- title: "DOME Agent Skill"
  content: "The agentic route — install into Claude Code, or point any agent at SKILL.md."
  url: https://github.com/gavinf97/dome-agent-skill

- title: "dome-schema"
  content: "The versioned, citable data model behind Registry entries."
  url: https://github.com/BioComputingUP/dome-schema

::/cards::

## The communities

| Community | What it does | Link |
|---|---|---|
| **ELIXIR AI Ecosystem Focus Group** | The current home for this work — successor to the ML Focus Group since October 2025 | [elixir-europe.org](https://elixir-europe.org/focus-groups/ai-ecosystem) |
| **ELIXIR Machine Learning Focus Group** | Developed DOME and OSAI; ran 2019–2025 | [elixir-europe.org](https://elixir-europe.org/focus-groups/machine-learning) |
| **MAQC ML Working Group** | The MAQC Society's machine learning working group | [themaqc.org/ml-working-group](https://themaqc.org/ml-working-group/) |
| **BioComputingUP** | University of Padua group maintaining the Registry and schema | [protein.bio.unipd.it](https://protein.bio.unipd.it/) |
| **MAQC Society** | *"Reproducibility is science. Science demands reproducibility."* | [themaqc.org](https://themaqc.org/) |

## How to contribute

=== "Annotate a paper"

    The single most useful thing: deposit a DOME entry for a paper — ideally your
    own — in the [DOME Registry](https://registry.dome-ml.org/). Registry coverage
    is what makes field-level questions about reporting quality answerable.
    Curation is credited via [APICURON](https://apicuron.org/).

=== "Add an ecosystem component"

    Know a tool that supports one of the OSAI recommendations and is not in the
    list? Two routes, both in the
    [OSAI_ecosystem repository](https://github.com/BioComputingUP/OSAI_ecosystem):

    1. **Open an issue** with the *Submit a New AI Ecosystem Component* template — recommended
    2. **Open a pull request** editing `data/ecosystem_components_list.yml`

=== "Improve the tooling"

    - **DOME Copilot** — [IFCA-Advanced-Computing/dome-copilot](https://github.com/IFCA-Advanced-Computing/dome-copilot)
    - **DOME Agent Skill** — [gavinf97/dome-agent-skill](https://github.com/gavinf97/dome-agent-skill).
      This is v0.1.0 and explicitly unbenchmarked; a rigorous evaluation against
      expert human curation would be a genuinely valuable contribution
    - **dome-schema** — [BioComputingUP/dome-schema](https://github.com/BioComputingUP/dome-schema)

=== "Improve this tutorial"

    Corrections and additions are welcome:
    [gavinf97/dome-tutorial-maqc-2026](https://github.com/gavinf97/dome-tutorial-maqc-2026).
    See `CONTRIBUTING.md` in the repository. Every page has an edit icon that takes
    you straight to the source.

## Related reading

- **Interpretation of DOME for proteomics and metabolomics** — [PMC8981311](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8981311/)
- **Integrating ML standards in research dissemination** — Edmunds SC, *CODATA Data Science Journal* (2026), [10.5334/dsj-2026-001](https://datascience.codata.org/articles/10.5334/dsj-2026-001)
- **DOME Registry research software story** — [RSQKit / EVERSE](https://everse.software/RSQKit/dome_registry_research_software_story)
- **Adjacent standards** — TRIPOD+AI, REFORMS, Bridge2AI, [FAIR4ML](https://github.com/RDA-FAIR4ML/FAIR4ML-schema), [Croissant](https://mlcommons.org/croissant/)

## Citing and reusing this tutorial

This site is licensed
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — reuse and adapt
it freely for your own training, keeping the same licence.

> Farrell, G. (2026). *Publishing Reusable AI/ML Models in the Life Sciences*
> (MAQC2026 Technical Tutorial P06).
> <https://gavinf97.github.io/dome-tutorial-maqc-2026/>

Machine-readable metadata:
[`CITATION.cff`](https://github.com/gavinf97/dome-tutorial-maqc-2026/blob/main/CITATION.cff).
Please also cite the underlying works in [References](chapters/references.md).

## Contact

- **DOME / OSAI / Copilot** — <contact@dome-ml.org>
- **This tutorial** — [open an issue](https://github.com/gavinf97/dome-tutorial-maqc-2026/issues)
- **Tutorial lead** — Gavin Farrell, [ORCID 0000-0002-0558-8337](https://orcid.org/0000-0002-0558-8337)
