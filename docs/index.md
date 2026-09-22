---
tags:
    - DOME
    - OSAI
    - MAQC 2026
    - reporting standards
    - reproducibility
---

# Publishing Reusable AI/ML Models in the Life Sciences

**MAQC 2026 Technical Tutorial P06**

**Wednesday 23 September 2026, 14:00–15:30 · Brescia, Italy**

Led by [Gavin Farrell](https://orcid.org/0000-0001-5166-8551), University of Padua ([BioComputingUP](https://protein.bio.unipd.it/))

[:material-presentation-play: Open the tutorial slides](https://docs.google.com/presentation/d/1YyIH6UaMAw16p5z5xwGjAdpWyqXuT1-GMjMfYWFtFnU/edit?slide=id.g3fbb5ca46c4_0_934#slide=id.g3fbb5ca46c4_0_934){ .md-button .md-button--primary }
[:material-toolbox: Session assets](assets.md){ .md-button }

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
just reading them. We will look at the recommendations themselves, at the
[registry](chapters/chapter_02_registry.md) that makes DOME reports findable
and reusable, at the [tooling](chapters/chapter_03_copilot.md) that makes
producing one tractable at scale, at the broader
[Open and Sustainable AI](chapters/chapter_04_osai.md) picture, and then you
will produce a report yourself by whichever
[submission route](routes.md) suits you.

## Run sheet — the 90 minutes

| Time | Activity | Description |
|---|---|---|
| 14:00–14:10 | **Introduction** | Attendee background<br>Learning outcomes<br>Overview |
| 14:10–14:40 | **[Slides](https://docs.google.com/presentation/d/1YyIH6UaMAw16p5z5xwGjAdpWyqXuT1-GMjMfYWFtFnU/edit?slide=id.g3fbb5ca46c4_0_934#slide=id.g3fbb5ca46c4_0_934)** | AI/ML & publishing issues<br>DOME Recommendations & Registry<br>OSAI |
| 14:40–14:50 | **Break** | Brain rest |
| 14:50–15:25 | **[Hands-on tutorial exercise](routes.md)** | AI/ML method reporting activity with:<br>[DOME Wizard](chapters/chapter_06_route_manual.md)<br>[DOME Copilot](chapters/chapter_07_route_copilot.md)<br>[DOME Agent Skill](chapters/chapter_08_route_agent.md) |
| 15:25–15:30 | **Wrap-up & discussion** | Final Qs |

## About MAQC 2026

This tutorial is part of the **MAQC Society 2026 Annual Meeting**, *"Precision
in a Complex World"*, held 22–26 September 2026 at LIGHT, University of Brescia,
Italy.

::cards:: cols=1

- title: "MAQC 2026 Conference Page"
  content: "Dates, venue, registration and the full programme."
  url: https://themaqc.org/conferences/

::/cards::

## Credits, citation and licence

This tutorial draws on work by the ELIXIR
[Machine Learning Focus Group](https://elixir-europe.org/focus-groups/machine-learning)
and its successor the [AI Ecosystem Focus Group](https://elixir-europe.org/focus-groups/ai-ecosystem),
[BioComputingUP](https://protein.bio.unipd.it/) at the University of Padua, and
the many contributors to the DOME and OSAI initiatives.

!!! note "How to cite this tutorial"

    > Farrell, G. (2026). *Publishing Reusable AI/ML Models in the Life Sciences*
    > (MAQC 2026 Technical Tutorial P06). Zenodo.
    > <https://doi.org/10.5281/zenodo.22900624>

    Please also cite the underlying works listed in [References](chapters/references.md).

??? info "Template attribution"
    This site is built with the [ELIXIR Training Lesson Template](https://zenodo.org/records/7913092)
    by van Geest G, Kronander E, Romero Herrera JA, Žlender N, ELIXIR Training
    Coordination Team & Cardona A (2023), DOI
    [10.5281/zenodo.7913092](https://doi.org/10.5281/zenodo.7913092), CC BY-SA 4.0.
    Content has been replaced with the MAQC 2026 tutorial material. Because the
    template is ShareAlike, **this tutorial is also licensed
    [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)**.

[add-bioschemas]
