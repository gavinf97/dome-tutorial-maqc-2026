---
tags:
    - hands-on
    - DOME Wizard
    - manual annotation
---

# Route A — Manual via the DOME Wizard

**You, the paper, and 21 fields. The slowest route, but the one that teaches you the most.**

---

!!! overview "Overview"

    **Questions:**

    - How do I create a DOME entry by hand?
    - Do I need an account, and how long does that take?
    - What do I do about fields the paper simply does not answer?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Sign in to the DOME Wizard, with LS Login or a new account
    2. Create a project from the DOME knowledge model
    3. Fill in the Data and Model sections for a real paper
    4. Record what the paper does *and does not* report, honestly

    **Time:** 35 minutes (hands-on exercise)

    **Prerequisite:** [Chapter 1](chapter_01_dome.md) for the field definitions · an [LS Login](https://lifescience-ri.eu/ls-login/) or DOME Wizard account

---

!!! tip "Which paper should I annotate?"
    **Your own**, if you have one with a supervised ML method — you will get the
    most out of it. Otherwise pick any supervised ML paper in biology you know
    reasonably well. A paper you have reviewed works especially well.

    Need one? Browse finished entries in the
    [DOME Registry search](https://registry.dome-ml.org/search), open any entry,
    and follow its DOI through to the paper.

---

## Annotating in the DOME Wizard

The **[DOME Wizard](https://dome.dsw.elixir-europe.org/wizard/)** is the DOME
questionnaire running on ELIXIR's Data Stewardship Wizard: a guided,
question-by-question interview with per-question guidance, and comments and
TODOs you can leave on individual answers.

**Steps**

1. Go to **<https://dome.dsw.elixir-europe.org/wizard/>**

2. **Sign in.** If you already have **LS Login**, use that button — it is the
   smoothest way in. Otherwise
   [create a DOME Wizard account](https://dome.dsw.elixir-europe.org/wizard/signup):
   the confirmation email usually arrives within a minute or two, and you can log
   in as soon as you have clicked the link in it.

3. **Projects → Create → give it any name** (`MAQC 26 Test` is fine) **→ pick the
   DOME knowledge model → Create.**

4. **Pick your paper** — your own, or one you found in the Registry.

5. **Fill in the `Data` section first, then `Model`**, then as much of the rest as
   the time allows. Keep [Chapter 1](chapter_01_dome.md) open in another tab for
   the field definitions.

!!! info "After the session"
    For a real annotation, the Wizard is what sends your finished entry on to the
    [DOME Registry](chapter_02_registry.md). Today, filling it in is the exercise.

---

## Working through the fields

Work in this order — it follows how a paper is usually written, and the
Optimisation fields are the fiddliest, so they are best left until last:

| Pillar | Where the answers usually live |
|---|---|
| **Data** | Methods, "Data availability" statement, supplementary tables |
| **Model** | Methods, "Code availability" statement, the repository itself |
| **Evaluation** | Results, figures and their captions, supplementary benchmarks |
| **Optimisation** | Methods, supplementary methods, the code repository's README or config files |

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
