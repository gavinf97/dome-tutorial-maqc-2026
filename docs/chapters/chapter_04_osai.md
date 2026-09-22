---
tags:
    - OSAI
    - open science
    - sustainability
    - Green AI
    - FAIR4ML
---

# 4. Open and Sustainable AI (OSAI)

**DOME asks how you *reported* a method. OSAI asks how you *share, reproduce and run* it.**

---

!!! overview "Overview"

    **Questions:**

    - What does OSAI cover that DOME does not?
    - What are the nine OSAI recommendations?
    - How do I go from a recommendation to something I can actually do on Monday?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Position DOME and OSAI as complementary rather than competing
    2. Recall the nine OSAI recommendations
    3. Use the OSAI ecosystem components list to find a concrete tool for a specific gap

    **Time:** 10 minutes

---

## Where OSAI fits

DOME governs the **reporting of a supervised ML method** in a publication. It
does an excellent job of that and deliberately stops there.

But a well-reported method can still be unusable: no packaged environment, no
standardised metadata, not deposited anywhere findable, no benchmark others can
run against, and no idea what it cost to train. **Open and Sustainable AI
(OSAI)** addresses that surrounding layer — how AI models and datasets are
shared, reproduced, evaluated and run responsibly [@farrell2026osai].

The two are complementary, and both are in scope for this tutorial:

| | **DOME** | **OSAI** |
|---|---|---|
| Unit | A supervised ML method in a paper | An AI model or dataset as a research object |
| Question | Was it reported transparently? | Can it be found, reused, reproduced and run sustainably? |
| Output | A structured 21-field transparency report | Practices mapped to ecosystem components |
| Scope | Publication | Whole model lifecycle, including compute cost |

!!! tip "A useful mental model"
    DOME makes the paper assessable. OSAI makes the model *usable*.

## The nine OSAI recommendations

The OSAI work maps nine practical recommendations to **over 300 components** of
the AI ecosystem, so that each recommendation comes with real tools rather than
good intentions [@farrell2026osai].

=== "Share and reuse (R1–R3)"

    **R1 — Generate and share standardised AI metadata for models and datasets**

    Use community schemas — [FAIR4ML](https://github.com/RDA-FAIR4ML/FAIR4ML-schema)
    for models, [Croissant](https://mlcommons.org/croissant/) for datasets — so
    your work can be found and interpreted by machines as well as people.

    **R2 — Leverage AI registries as central hubs for sharing and discovering reusable AI models and datasets**

    Deposit in a registry rather than only a personal repository. The
    [DOME Registry](chapter_02_registry.md) is one such hub; there are many others
    in the ecosystem list.

    **R3 — Host, promote and share training and guidance on correct deposition of AI research objects for reuse**

    Deposition practice has to be taught. *This tutorial is itself an instance of R3.*

=== "Reproduce and verify (R4–R6)"

    **R4 — Ensure transparent disclosure, clear documentation and sharing of all model relevant information**

    The closest overlap with DOME — disclose data, training configuration, model
    files and evaluation so others can independently verify your results.

    **R5 — Provide portable code and reproducible environments to facilitate smooth reuse**

    Containers, lockfiles, declared dependencies. "It works on my machine" is not
    a reproducibility claim.

    **R6 — Use standardised AI-ready datasets and benchmarking evaluation protocols to facilitate reproducible model comparisons**

    Shared benchmarks and protocols are what make two papers' numbers comparable
    at all.

=== "Green AI (R7–R9)"

    **R7 — Implement Green AI model development techniques**

    Efficient architectures, transfer learning over training from scratch, early
    stopping, right-sized models — much of this improves science *and* reduces cost.

    **R8 — Choose and optimise hardware to reduce environmental impact**

    Hardware selection and utilisation are a first-order lever on the footprint of
    a training run.

    **R9 — Measure and report AI model environmental impact**

    You cannot manage what you do not measure. Report the compute and energy cost
    of training alongside your performance numbers.

## Finding a tool for your gap

The [**OSAI ecosystem components list**](https://osai.dome-ml.org/ai-ecosystem)
is a community-curated inventory of AI-relevant tools, registries, metadata
standards and best-practice frameworks, each mapped to the OSAI recommendations
it supports [@osai2025ecosystem].

It is also **explicitly designed for reuse** — the maintainers acknowledge there
is no single perfect set of AI best-practice recommendations, so the list is
built to be remapped onto other frameworks and other communities' guidance.

---

## Sources and further reading

- **The OSAI site**: <https://osai.dome-ml.org/>
- **The community**: the [ELIXIR AI Ecosystem Focus Group](https://elixir-europe.org/focus-groups/ai-ecosystem), successor to the [Machine Learning Focus Group](https://elixir-europe.org/focus-groups/machine-learning) that produced DOME and OSAI
- **The paper**: Farrell G, Adamidi E, Andrade Buono R, et al. *Open and sustainable AI: challenges, opportunities and the road ahead in the life sciences.* Nature Methods (2026). [doi:10.1038/s41592-026-03037-6](https://doi.org/10.1038/s41592-026-03037-6) [@farrell2026osai]
- **Preprint**: [arXiv:2505.16619](https://arxiv.org/abs/2505.16619) [@farrell2025osaipreprint]
- **Ecosystem components list**: [osai.dome-ml.org/ai-ecosystem](https://osai.dome-ml.org/ai-ecosystem) · [doi:10.5281/zenodo.15391274](https://doi.org/10.5281/zenodo.15391274) [@osai2025ecosystem]

---

**Next:** [Chapter 5 — Agentic AI Skills for DOME](chapter_05_agentic.md)
