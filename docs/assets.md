---
tags:
    - slides
    - collaborative notes
    - session assets
---

# Session Assets

**Everything you need during the live session, in one place.**

---

!!! overview "Overview"

    **What is on this page:**

    - The tutorial slide deck, open to everyone
    - The shared collaborative document for notes, questions and activities
    - Login details for the DOME Copilot instance we will use in the hands-on segment
    - The tools you will need open in a browser tab

    **Time:** 5 minutes at the start of the session

---

## The two live assets

::cards:: cols=2 class="assets"

- title: "📊 Tutorial Slides"
  content: "The full P06 slide deck, in Google Slides. Open access — follow along live, or read it afterwards. No account needed."
  url: https://docs.google.com/presentation/d/1YyIH6UaMAw16p5z5xwGjAdpWyqXuT1-GMjMfYWFtFnU/edit?usp=sharing

- title: "📝 Collaborative Notes & Activities"
  content: "The shared Google Doc we write in together — questions, the hands-on activity, and the notes that come out of the room. Open access."
  url: https://docs.google.com/document/d/1PB32nN9AhfMlwwNqnykVrBBlfbpfKRf8BaiUMBIz9g8/edit?usp=sharing

::/cards::

| Asset | Link | How we use it |
|---|---|---|
| :material-presentation-play: **Tutorial slides** | [Open in Google Slides](https://docs.google.com/presentation/d/1YyIH6UaMAw16p5z5xwGjAdpWyqXuT1-GMjMfYWFtFnU/edit?usp=sharing) | Presented from the front; open it yourself if you want to move at your own pace or revisit a slide |
| :material-file-document-edit: **Collaborative notes** | [Open in Google Docs](https://docs.google.com/document/d/1PB32nN9AhfMlwwNqnykVrBBlfbpfKRf8BaiUMBIz9g8/edit?usp=sharing) | Post questions as they occur to you, record your hands-on findings, and leave anything you want followed up after the conference |

!!! tip "Put both in a tab now"
    We will move between the slides, this site and the shared document
    throughout. Having all three open saves time later — particularly in the
    hands-on segment, where you will be pasting results into the shared
    document.

---

## Tools we will use in the hands-on segment

::cards:: cols=2

- title: "DOME Registry"
  content: "The public registry of DOME transparency reports. Used in Route A. ORCID sign-in."
  url: https://registry.dome-ml.org/

- title: "DOME Wizard (Data Stewardship Wizard)"
  content: "The ELIXIR DSW-hosted DOME questionnaire — a guided, question-by-question alternative for Route A."
  url: https://dome.dsw.elixir-europe.org/wizard/

- title: "DOME Copilot"
  content: "LLM-assisted annotation. Upload a PDF, get a structured draft DOME report. Used in Route B — shared login below."
  url: https://dome-copilot.ifca.es/

- title: "DOME Agent Skill"
  content: "The agentic route. Install into Claude Code or point any agent at it. Used in Route C."
  url: https://github.com/gavinf97/dome-agent-skill

::/cards::

### DOME Copilot — shared workshop login

The DOME Copilot instance we will use during this session is hosted at
**<https://dome-copilot.ifca.es/>**. It does not yet have federated
authentication (AAI) in place, so a shared account is provided for the
tutorial:

| Field | Value |
|---|---|
| URL | <https://dome-copilot.ifca.es/> |
| User | `admin` |
| Password | `6yKG7b5p` |

!!! warning "Shared demo account"
    This is a **shared instance with a shared account** — everyone in the room
    is logged into the same service. Do not upload anything confidential or
    unpublished that you would not be comfortable others seeing, and treat
    anything you find there as visible to other workshop participants.

    Full step-by-step usage is in
    **[Chapter 7 — Route B: DOME Copilot](chapters/chapter_07_route_copilot.md)**.

!!! info "Something not working?"
    Some browsers or networks may show a **TLS certificate warning** for the
    Copilot host — the server does not send its full certificate chain. The
    certificate is valid; see
    [Chapter 7](chapters/chapter_07_route_copilot.md) for details and
    workarounds.

    Technical issues with DOME Copilot can be flagged to
    **<contact@dome-ml.org>**.

---

## What to have ready

=== "If you plan to use Route A (manual)"

    - An [ORCID iD](https://orcid.org/) — you will sign in to the DOME Registry with it
    - A paper to annotate: ideally **your own**, otherwise pick any supervised ML paper in biology
    - Optionally, the [DOME Wizard](https://dome.dsw.elixir-europe.org/wizard/) open as a guided alternative

=== "If you plan to use Route B (DOME Copilot)"

    - A browser, and the login details above
    - The **PDF** of the paper you want to annotate, plus any supplementary PDFs
    - The paper's **DOI**, if you have it — Copilot can pull metadata in automatically

=== "If you plan to use Route C (agent skill)"

    - Python 3.10 or newer (`python3 --version`)
    - A terminal, and an agent platform — Claude Code is fastest, but any agentic
      coding assistant works
    - The paper's **DOI or URL**
    - See [Chapter 8](chapters/chapter_08_route_agent.md) for the full install steps —
      doing this **before** the session starts will save you time

---

**Next:** [Chapter 1 — The DOME Standard](chapters/chapter_01_dome.md)
