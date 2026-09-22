---
tags:
    - DOME Registry
    - peer review
    - FAIR
    - dome-schema
---

# 2. The DOME Registry

**A public home for DOME transparency reports — so they are findable, shareable, citable and comparable.**

---

!!! overview "Overview"

    **Questions:**

    - A DOME report is useful — but where does it live, and who can find it?
    - How does a registry entry help an author, a reviewer, an editor and a meta-researcher differently?
    - What is a DOME score, and what can it legitimately be used for?
    - How is the underlying schema versioned, and why does that matter?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Explain why DOME reports need a registry rather than living in supplementary PDFs
    2. Describe how a registry entry slots into a journal's peer-review workflow
    3. Interpret a DOME score, and state its limits
    4. Find the schema an entry conforms to, and tell v1.0.0 from v2.0.0

    **Time:** 10 minutes

    **Prerequisite:** [Chapter 1 — The DOME Standard](chapter_01_dome.md)

---

## The problem a registry solves

A DOME report buried in Supplementary Table 7 of a PDF is, for practical
purposes, invisible. It cannot be searched, compared, updated, linked to from a
review, counted across a field, or reused by anyone building tooling on top of
it. The reporting effort is spent and then lost.

The [**DOME Registry**](https://registry.dome-ml.org/) is the answer: a public,
structured, versioned database of DOME transparency reports, described in
*GigaScience* [@attafi2024registry]. Entries are stored as structured JSON
against a controlled schema, given persistent identifiers, and linked to their
publication and to the curator who created them.

!!! tip "The shift"
    From *"the DOME checklist is a thing you fill in once"* to *"the DOME report is
    a research object with an identifier, a version history and an author."*

## Who it serves, and how

=== "Authors"

    Complete a DOME report during manuscript preparation, get a stable link, and
    supply that link at submission. It is a concrete, low-effort way to demonstrate
    methodological transparency — and filling it in usually improves the methods
    section itself.

=== "Reviewers"

    Open one link and see, field by field, what the paper does and does not report.
    As the *GigaScience* paper puts it, reviewers gain a standardised and efficient
    evaluation tool — instead of reconstructing the methods from prose, you are
    checking a structured record against the manuscript.

=== "Journals and editors"

    Integrate the report into the submission workflow so that ML methodology is
    assessed consistently across submissions. The benefit that matters editorially
    is improved submission quality: authors who know they will be asked tend to
    report better.

=== "Meta-researchers and infrastructure"

    Structured entries can be counted, queried through the REST API, and analysed
    across a field — which is what makes questions like *"has data-split reporting
    improved since 2021?"* answerable at all.

## What the Registry provides

| Feature | What it does |
|---|---|
| **LS Login authentication** | Sign in with [LS Login](https://lifescience-ri.eu/ls-login/), the European life-science AAI; curation is attributed to a real, persistent identity |
| **Annotation wizard** | Guided, field-by-field entry following the four DOME pillars |
| **DOME score** | Automated compliance score, **0–21**, one point per completed field |
| **Versioned entries** | Entries can be revised; earlier versions remain interpretable against their schema version |
| **Moderation workflow** | Drafts can be submitted for review before appearing publicly |
| **REST API** | Programmatic read and write access — what tooling like DOME Copilot and the DOME Agent Skill build on |
| **APICURON integration** | Biocuration contributions are credited, so curation effort is visible and countable |
| **Data Stewardship Wizard** | The DOME questionnaire is also available through ELIXIR's DSW instance |
| **Zenodo archival** | The full dataset is versioned and backed up to Zenodo automatically |

!!! info "Two ways in"
    You can annotate directly in the Registry, or work through the **DOME Wizard**
    hosted on ELIXIR's Data Stewardship Wizard at
    <https://dome.dsw.elixir-europe.org/wizard/>. Both are covered step by step in
    [Route A — Manual via the DOME Registry](chapter_06_route_manual.md).

## Reading a DOME score honestly

The score is **0–21**: one point per DOME field that has been completed.

!!! warning "What the score is not"
    The DOME score measures **how much was reported**, not **how good the science
    is**. A well-reported weak method scores higher than a brilliantly executed
    method whose authors said nothing about their data splits. Use it as a
    transparency indicator and a prompt for specific questions — never as a proxy
    for methodological quality, and never as a ranking of researchers.

Used well, the score is most valuable **comparatively**: across a journal's
submissions, across a subfield, or across versions of your own work as you
improve its reporting.

## The schema, and why versioning matters

Registry entries conform to
[**dome-schema**](https://github.com/BioComputingUP/dome-schema) [@domeschema],
maintained as a versioned, citable artefact in its own right — separately from
the Registry application. This matters because entries created years apart must
stay valid and interpretable as the model evolves, especially now that entries
are increasingly generated at scale by automated pipelines.

| Version | Shape | Notes |
|---|---|---|
| **v1.0.0** | Free-text string per field | The original convention; section is named `dataset` |
| **v2.0.0** | Typed sub-fields per field | Current default. Section renamed to `data`; `fitting`/`regularization`/`confidence` became `fit`/`regularisation`/`confidance` |

Both releases are shipped inside the
[DOME Agent Skill](chapter_05_agentic.md) so that entries can be generated
against either one.

!!! note "Entries can be machine-generated"
    The schema carries an `isAiGenerated` flag — true if an entry was produced
    automatically, for example by [DOME Copilot](chapter_03_copilot.md). This is
    deliberate: provenance of the *annotation itself* is part of the record, so a
    reader can weigh a machine-drafted entry differently from a hand-curated one.

---

## Sources and further reading

- **The Registry**: <https://registry.dome-ml.org/>
- **The paper**: Attafi OA, et al. *DOME Registry: implementing community-wide recommendations for reporting supervised machine learning in biology.* GigaScience 13, giae094 (2024). [doi:10.1093/gigascience/giae094](https://doi.org/10.1093/gigascience/giae094) [@attafi2024registry]
- **The schema**: [BioComputingUP/dome-schema](https://github.com/BioComputingUP/dome-schema)
- **DOME Wizard (ELIXIR DSW)**: <https://dome.dsw.elixir-europe.org/wizard/>
- **Zenodo archive**: <https://zenodo.org/records/18301904>
- **Software practices behind the Registry**: [RSQKit research software story](https://everse.software/RSQKit/dome_registry_research_software_story)

---

**Next:** [Chapter 3 — DOME Copilot](chapter_03_copilot.md)
