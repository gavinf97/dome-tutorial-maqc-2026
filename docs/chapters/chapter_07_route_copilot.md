---
tags:
    - hands-on
    - DOME Copilot
    - LLM-assisted
---

# Route B — DOME Copilot

**Upload a PDF, get a structured draft in about two minutes, then review every field.**

---

!!! overview "Overview"

    **Questions:**

    - How do I actually run DOME Copilot on a paper?
    - What do I get back, and in what format?
    - Which fields should I check hardest before trusting the output?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Log in to the workshop DOME Copilot instance and generate an annotation
    2. Download the resulting JSON and read it against the paper
    3. Identify and correct the fields most likely to need human amendment
    4. Move a reviewed annotation into the DOME Registry

    **Time:** 35 minutes (hands-on exercise)

    **Prerequisite:** [Chapter 3](chapter_03_copilot.md) · a publication PDF · a browser

---

## Access

| Field | Value |
|---|---|
| URL | **<https://dome-copilot.ifca.es/>** |
| User | `admin` |
| Password | `6yKG7b5p` |

!!! warning "Shared workshop account"
    This instance does not yet have federated authentication (AAI) in place, so a
    single shared account is provided for the tutorial. Everyone in the room is
    logged into the same service — **do not upload confidential or unpublished
    material you would not be comfortable others seeing.**

---

## Step by step

1. **Go to the DOME Copilot web URL** — <https://dome-copilot.ifca.es/>
2. **Log in** with the details above
3. **Upload the publication's primary PDF**, plus any supplementary materials
   (also PDF). Supplementary files are worth including: several DOME fields —
   data splits, hyperparameters, evaluation details — are usually only stated
   there
4. **Provide the DOI** *(optional)* to pull in bibliographic metadata via
   external APIs. Do this if you have it; it means the publication fields come
   from a lookup rather than from the model reading a title page
5. **Click the orange "Generate annotations" button**
6. **Wait for the annotation to complete** — typically around two minutes,
   varying with document size
7. **Download the JSON** of the annotation, for refinement and sharing — for
   example by depositing it in the [DOME Registry](chapter_02_registry.md)

!!! info "If your browser warns about the certificate"
    The DOME Copilot server currently sends only its leaf TLS certificate without
    the intermediate chain. Most browsers fetch the missing intermediate
    automatically and connect without complaint, but some strict clients and
    corporate networks will show a certificate warning. The certificate itself is
    valid — issued to `dome-copilot.ifca.es` by the GEANT/HARICA academic CA. If
    you are blocked, try a different browser or network, or use
    [Route A](chapter_06_route_manual.md) or [Route C](chapter_08_route_agent.md)
    for the hands-on exercise.

!!! info "Something not working?"
    Technical issues can be flagged to **<contact@dome-ml.org>**.

---

## Now review it — this is the actual work

The download is a **draft**, not a finished report. Read it against the paper,
paying most attention to these:

=== "Fields the paper never states"

    The highest-value check. Copilot works from the manuscript text, and a
    plausible-sounding sentence in a field the paper is silent about is exactly
    what human review is for.

    Watch particularly for **1.3 Redundancy between data splits** and
    **4.3 Comparison** — both are commonly under-reported in papers, and both are
    fields where a confident-sounding draft can paper over a real gap.

=== "Numbers"

    Dataset sizes (N~pos~/N~neg~), parameter counts, feature counts, metric values.
    Check each against the source. Numbers are cheap to verify and expensive to get
    wrong.

=== "Availability fields"

    **1.4** (data), **2.8** (configuration), **3.4** (software), **4.5** (evaluation
    files). Verify that each URL resolves and that the licence stated is the licence
    actually there. A dead link is a DOME finding.

=== "Anything decision-changing"

    If a field would alter how a reader judges the method, read the paper's own
    words for it before accepting the draft.

!!! warning "Do not deposit an unreviewed annotation"
    An unchecked machine-drafted entry looks authoritative and borrows the
    Registry's credibility. The `isAiGenerated` flag records provenance — it does
    not substitute for review.

---

## When to choose this route

**Good fit:** many papers; building registry coverage for a subfield; a fast
first pass you will then correct; nothing installable on your machine; cost
matters.

**Poor fit:** you want OSAI recommendations as well as DOME (use
[Route C](chapter_08_route_agent.md)); or the material is confidential — this is
a shared instance.

---

## Sources

- **DOME Copilot**: <https://dome-copilot.ifca.es/>
- **The preprint**: [doi:10.64898/2026.04.16.718888](https://doi.org/10.64898/2026.04.16.718888) [@farrell2026copilot]
- **Source code**: [IFCA-Advanced-Computing/dome-copilot](https://github.com/IFCA-Advanced-Computing/dome-copilot)
- **Support**: <contact@dome-ml.org>

---

**Next:** [Route C — Agent Skills](chapter_08_route_agent.md)
