---
tags:
    - DOME
    - OSAI
    - MAQC2026
    - reporting standards
    - reproducibility
---

# Publishing Reusable AI/ML Models in the Life Sciences

**MAQC2026 Technical Tutorial P06 · Wednesday 23 September 2026, 14:00–15:30 · Brescia, Italy**

Led by [Gavin Farrell](https://orcid.org/0000-0002-0558-8337), University of Padua ([BioComputingUP](https://protein.bio.unipd.it/)) · Focus: **ELIXIR ecosystem, DOME, OSAI**

---

!!! overview "Overview"

    **Questions this tutorial answers:**

    - What does it actually take to report an AI/ML method transparently enough that someone else can trust and reuse it?
    - What are the DOME recommendations, and what do their 21 fields ask for?
    - How do the DOME Registry, DOME Copilot and agentic AI skills each help me produce a DOME transparency report?
    - How does OSAI extend this from *reporting* a method to *sharing and sustaining* a model?
    - Which route should I use for my own paper — and what does each one cost me in time, money and control?

    **Learning Objectives**

    By the end of this session, you will be able to:

    1. Explain the four DOME pillars — Data, Optimisation, Model, Evaluation — and identify which of the 21 fields a given paper fails to report
    2. Describe why a public registry of DOME reports matters for authors, reviewers, editors and meta-researchers
    3. Produce a DOME transparency report for a paper by **at least one** of three routes: manual, DOME Copilot, or an agentic AI skill
    4. Position the nine OSAI recommendations alongside DOME and identify concrete ecosystem components that close a reporting gap
    5. Judge the trade-offs between the three routes — accuracy, cost, accessibility and required human review

    **Who this is for:** Researchers publishing AI/ML methods, data curators, journal editors and peer reviewers, and anyone assessing the reproducibility of computational methods in the life sciences

    **Prerequisites:** Familiarity with supervised machine learning terminology. No coding is required for Routes A and B; Route C needs Python 3.10+ and a terminal

    **Time:** 90 minutes

---

## Why this session exists

AI/ML methods in the life sciences are published far faster than anyone can
assess them. A reader — or a reviewer — often cannot tell from a paper how the
data were split, whether the test set was independent, what the baseline was,
or whether the model can be run at all. That is not a peer-review failure so
much as a **reporting** failure: the information was never asked for in a
structured way.

The [DOME recommendations](chapters/chapter_01_dome.md) are the community's
answer to that, and this tutorial is about putting them into practice — not
just reading them. We will look at the standard itself, at the
[registry](chapters/chapter_02_registry.md) that makes DOME reports findable
and reusable, at the [tooling](chapters/chapter_03_copilot.md) that makes
producing one tractable at scale, at the broader
[Open and Sustainable AI](chapters/chapter_04_osai.md) picture, and then you
will produce a report yourself by whichever
[route](chapters/chapter_06_route_manual.md) suits you.

## Run sheet — the 90 minutes

| Time | Segment | Page |
|---|---|---|
| 14:00–14:05 | Welcome, scope, and getting the shared assets open | [Session Assets](assets.md) |
| 14:05–14:20 | The DOME standard: four pillars, 21 fields | [Chapter 1](chapters/chapter_01_dome.md) |
| 14:20–14:30 | The DOME Registry: findable, reusable transparency reports | [Chapter 2](chapters/chapter_02_registry.md) |
| 14:30–14:40 | DOME Copilot: LLM-assisted, human-in-the-loop curation | [Chapter 3](chapters/chapter_03_copilot.md) |
| 14:40–14:50 | Open and Sustainable AI: the nine recommendations | [Chapter 4](chapters/chapter_04_osai.md) |
| 14:50–15:00 | Agentic AI skills: frontier models in the loop | [Chapter 5](chapters/chapter_05_agentic.md) |
| 15:00–15:25 | **Hands-on** — pick a route and annotate a paper | [Ch. 6](chapters/chapter_06_route_manual.md) · [7](chapters/chapter_07_route_copilot.md) · [8](chapters/chapter_08_route_agent.md) |
| 15:25–15:30 | Discussion, next steps, how to keep contributing | [Further Resources](follow_up_training.md) |

!!! tip "Do this first"
    Open the **[Session Assets](assets.md)** page now. The slides and the shared
    collaborative document are both linked there, and we will use the shared
    document throughout for notes, questions and the hands-on activity.

## The three routes at a glance

There is no single right way to produce a DOME transparency report. The
hands-on segment lets you pick, and the honest trade-offs are laid out in each
chapter.

| | **Route A — Manual** | **Route B — DOME Copilot** | **Route C — Agent Skill** |
|---|---|---|---|
| What drives it | You, reading the paper | A mid-sized LLM (Mistral Small 3.1 24B) | A frontier agent (Claude or similar) |
| Setup needed | ORCID account | Web login, nothing installed | Python 3.10+, an agent platform |
| Time per paper | 30–90 min | ~2 min to draft, then human review | ~5–15 min, then human review |
| Cost | Free | Cheap, self-hostable, scales to a corpus | Higher per paper; needs model credits |
| Covers OSAI too | No | No | Yes — DOME plus OSAI suggestions |
| Human review | *Is* the work | **Required** | **Required** |
| Chapter | [Chapter 6](chapters/chapter_06_route_manual.md) | [Chapter 7](chapters/chapter_07_route_copilot.md) | [Chapter 8](chapters/chapter_08_route_agent.md) |

## About MAQC2026

This tutorial is part of the **MAQC Society 2026 Annual Meeting**, themed
*"Precision in a Complex World"*, held **22–26 September 2026** at **LIGHT,
University of Brescia**, Italy. The meeting is co-organised with the
International Human Phenome Institute (IHPI), Shanghai, under the Patronage of
the University of Brescia. Session P06 sits on the **MAQC Technical Tutorial
Day** (Wednesday 23 September), the second pre-conference day.

The MAQC Society's tagline — *"Reproducibility is science. Science demands
reproducibility."* — is the reason this tutorial fits the programme.

::cards:: cols=2

- title: "MAQC Society"
  content: "The society behind MAQC2026, its working groups and its reproducibility mission."
  url: https://themaqc.org/

- title: "MAQC2026 Conference Page"
  content: "Dates, venue, registration, logistics and the full programme PDF."
  url: https://themaqc.org/conferences/

- title: "MAQC2026 Full Programme (PDF)"
  content: "The official programme. Session P06 is on page 5, Wednesday 23 September, 14:00–15:30."
  url: http://themaqc.org/wp-content/uploads/2026/08/MAQC2026_Program_Full-2026-08-29_v1.07.pdf

- title: "MAQC ML Working Group"
  content: "The society's machine learning working group — the natural home for follow-up on this session."
  url: https://themaqc.org/ml-working-group/

::/cards::

## Credits, citation and licence

This tutorial draws on work by the ELIXIR
[Machine Learning Focus Group](https://elixir-europe.org/focus-groups/machine-learning)
and its successor the [AI Ecosystem Focus Group](https://elixir-europe.org/focus-groups/ai-ecosystem),
[BioComputingUP](https://protein.bio.unipd.it/) at the University of Padua, and
the many contributors to the DOME and OSAI initiatives.

!!! note "How to cite this tutorial"

    > Farrell, G. (2026). *Publishing Reusable AI/ML Models in the Life Sciences*
    > (MAQC2026 Technical Tutorial P06). <https://gavinf97.github.io/dome-tutorial-maqc-2026/>

    Machine-readable metadata is in
    [`CITATION.cff`](https://github.com/gavinf97/dome-tutorial-maqc-2026/blob/main/CITATION.cff).
    Please also cite the underlying works listed in [References](chapters/references.md).

??? info "Template attribution"
    This site is built with the [ELIXIR Training Lesson Template](https://zenodo.org/records/7913092)
    by van Geest G, Kronander E, Romero Herrera JA, Žlender N, ELIXIR Training
    Coordination Team & Cardona A (2023), DOI
    [10.5281/zenodo.7913092](https://doi.org/10.5281/zenodo.7913092), CC BY-SA 4.0.
    Content has been replaced with the MAQC2026 tutorial material. Because the
    template is ShareAlike, **this tutorial is also licensed
    [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)**.

[add-bioschemas]
