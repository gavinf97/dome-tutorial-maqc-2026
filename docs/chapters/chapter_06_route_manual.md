---
tags:
    - hands-on
    - DOME Registry
    - DOME Wizard
    - manual annotation
---

# Route A — Manual via the DOME Registry

**You, the paper, and 21 fields. The slowest route, and the one that teaches you the most.**

---

!!! overview "Overview"

    **Questions:**

    - How do I create a DOME entry by hand?
    - What is the difference between the DOME Registry form and the DOME Wizard?
    - What do I do about fields the paper simply does not answer?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Sign in to the DOME Registry with LS Login and start an entry
    2. Work through the four pillars and record what the paper does and does not report
    3. Use the DOME Wizard as a guided alternative
    4. Save a draft and submit it for review

    **Time:** 35 minutes (hands-on exercise)

    **Prerequisite:** [Chapter 1](chapter_01_dome.md) for the field definitions · an [LS Login](https://lifescience-ri.eu/ls-login/) account

---

!!! tip "Which paper should I annotate?"
    **Your own**, if you have one with a supervised ML method — you will get the
    most out of it, and you end up with a real registry entry. Otherwise pick any
    supervised ML paper in biology you know reasonably well. A paper you have
    reviewed works especially well.

---

## Two ways to annotate manually

=== "DOME Registry (direct)"

    The registry's own schema-driven form. Best if you want the entry to land
    directly in the registry with the least indirection.

    **Steps**

    1. Go to **<https://registry.dome-ml.org/>**
    2. **Sign in with LS Login** (Life Science Login, the European life-science
       AAI). If you do not have an account yet, register via
       [LS Login](https://lifescience-ri.eu/ls-login/) — ideally before the session
    3. Start a **new entry** and supply the publication's **DOI**. Bibliographic
       metadata is pulled in for you — do not retype it
    4. Work through the four pillars in order: **Data → Optimisation → Model →
       Evaluation**. Keep [Chapter 1](chapter_01_dome.md) open in another tab for
       the field definitions
    5. **Save as a draft** as you go. You do not have to finish in one sitting
    6. When you are satisfied, **submit for review** — the entry goes to
       moderation before appearing publicly

=== "DOME Wizard (ELIXIR DSW)"

    The DOME questionnaire hosted on ELIXIR's
    [Data Stewardship Wizard](https://ds-wizard.org/). Best if you prefer a guided,
    question-by-question interview with contextual help, or if your institution
    already uses DSW for data management planning.

    **Steps**

    1. Go to **<https://dome.dsw.elixir-europe.org/wizard/>**
    2. Create or open a project using the **DOME** knowledge model
    3. Answer the questions in sequence — DSW carries per-question guidance and
       lets you leave comments and TODOs on individual answers, which is genuinely
       useful when several people are filling it in together
    4. Export your answers, then transfer them into a
       [DOME Registry](https://registry.dome-ml.org/) entry for deposition

    !!! info "Why two tools?"
        DSW is a general-purpose questionnaire platform used across ELIXIR for data
        management planning; the DOME knowledge model runs inside it. The Registry
        is the *home* for finished DOME reports. Use whichever interface you prefer
        to think in — the destination is the same.

---

## Working through the fields

The four pillars in order, with what to look for and where it usually hides:

| Pillar | Fields | Where the answers usually live |
|---|---|---|
| **Data** | 1.1–1.4 | Methods, "Data availability" statement, supplementary tables |
| **Optimisation** | 2.1–2.8 | Methods, supplementary methods, the code repository's README or config files |
| **Model** | 3.1–3.4 | Methods, "Code availability" statement, the repository itself |
| **Evaluation** | 4.1–4.5 | Results, figures and their captions, supplementary benchmarks |

!!! warning "Record gaps as gaps"
    When the paper does not state something, **leave the field empty** and note it.
    Do not fill it from the GitHub repository, from a previous paper by the same
    group, or from what you assume they must have done. DOME measures what the
    *publication* discloses — inferring the answer defeats the entire exercise.

    (The [agent skill](chapter_08_route_agent.md) handles this by tagging any
    repo-sourced field as `external:<url>` and flagging it as *not disclosed in the
    paper itself*. Do the same thing by hand: note it separately.)

!!! tip "If you get stuck on a field"
    Go back to [Chapter 1](chapter_01_dome.md) and read the *"why it matters"*
    line for that field. It usually makes clear what evidence would satisfy it —
    and, just as often, makes clear that the paper genuinely does not provide it.

---

## When to choose this route

**Good fit:** your own paper; you want to learn the recommendations properly; small
numbers; no LLM in the loop for policy or preference reasons; maximum control
and confidence in every field.

**Poor fit:** more than a handful of papers. At 30–90 minutes each, manual
annotation does not scale — which is the entire reason
[Route B](chapter_07_route_copilot.md) and
[Route C](chapter_08_route_agent.md) exist.

---

**Next:** [Route B — DOME Copilot](chapter_07_route_copilot.md)
