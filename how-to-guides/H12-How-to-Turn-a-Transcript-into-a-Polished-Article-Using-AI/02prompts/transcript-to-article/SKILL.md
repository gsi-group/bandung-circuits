---
name: transcript-to-article
description: >-
  Turn a raw transcript (panel, webinar, lecture, keynote, interview,
  conference session, debate, or roundtable) into a polished, publication-ready
  article while preserving the speakers' political voice, terminology, and
  argument. Built for political and intellectual discussion — Global South
  organisations, movements, and research institutes — NOT business meetings.
  Auto-detects the transcript genre and applies the matching restructuring
  playbook, keeps a human checkpoint at the outline stage, writes to a rigorous
  analytical house style, never invents facts, and flags uncertain
  names/numbers for human verification. Use when the user says "turn this
  transcript into an article", "transcript to article", "write an article from
  this transcript/recording/panel/webinar/lecture", "polish this transcript",
  or provides a transcript and wants a readable, publishable piece.
---

# Transcript → Article

Convert a raw transcript into a publication-ready article. This skill is **not**
a summariser and **not** a meeting-minutes tool — it restructures spoken material
into a coherent written argument for public readers, while staying faithful to
what was actually said and to the political register in which it was said.

It is publication-agnostic: it works for any project. The only fixed commitments
are (1) the genre-aware restructuring, (2) strict source fidelity, (3) preserving
the speakers' political voice, and (4) a rigorous analytical prose style.

## When to use vs. not

- **Use** for: articles / features / commentary built from panels, webinars,
  lectures, keynotes, interviews, conference sessions, roundtables, debates.
- **Don't use** for: meeting minutes, action-item extraction, business/project
  meetings (a generic `meeting-minutes` skill is fine for those).

## Inputs

- A transcript file (`.txt`, `.srt`, `.vtt`, `.md`, `.docx`) or pasted text.
- If the user only has a video/URL, get the transcript first (with any
  transcript/subtitle extractor), then run this.
- **Supporting materials, if provided** — speaker notes, prepared remarks/scripts,
  slide decks (`.pptx`/`.pdf`), papers, programmes, briefs. These are part of the
  source: read them, draw on them, and use them to resolve transcript errors.
- Optional but recommended: **a style sample** (a past article from the same
  publication/author) so the draft matches an established voice; target length;
  audience; an existing glossary of project terms.

## Workflow

Run these stages in order. **Never skip the genre confirmation or the outline
checkpoint.** Work incrementally — outline before draft, draft before polish.

### 0. (Optional) Learn the target voice
If the user supplies a style sample, read it first and note its register,
sentence rhythm, and how it handles attribution and terminology. The default
prose target is `references/writing-style.md`; a supplied sample overrides it.

### 1. Ingest & assess
Read the full transcript **and all supporting materials** (speaker notes, scripts,
slides, papers). Note: length, number of distinct speakers, whether speaker labels
exist, and the genre signals. While reading, mark in passing the **quotable lines**
(sharp, charged, or precise formulations worth quoting verbatim) and the
**evidence** (statistics, dates, names, sources). If the transcript is very long
(≳15k words), process it in segments (by agenda item / time block) to avoid
omission and drift, then merge.

**Use supporting materials to:** (a) confirm or correct names, places, terms,
titles, dates, and figures that the transcript (ASR) may have mangled — slides and
prepared scripts are usually more reliable for spellings and numbers than ASR;
(b) recover points a speaker made that the transcript garbled or dropped. Where a
genuine conflict remains (slide says one thing, the speaker clearly said another),
keep what was *spoken* as the speaker's position but flag the conflict for the user.

**Source scope:** the article's content, argument, and logic come **mainly from
the speakers — the transcript plus their supporting materials.** Supporting
materials clarify and disambiguate what was said; they do not license importing
outside facts or your own framing (closed-book still applies — see Hard rule 1).

### 2. Detect genre & output language → confirm with the user
Classify the transcript into ONE primary genre using the signals in
`references/genre-playbooks.md`, and state the **output language** you'll use.
Report both in one line with the evidence, e.g.:

> Detected: **panel/webinar** (6 speakers from different countries, sequential
> country presentations, a chair). I'll re-cluster points into themes rather
> than follow speaking order. Output language: **English** (the transcript's
> dominant language). Override either?

Wait for confirmation or override before proceeding. Genre sets the restructuring
strategy and language sets everything downstream — getting either wrong wastes
the whole draft.

**Output-language rule:**
- If the user specifies an output language (or a target publication implies one),
  use that.
- **If the user does NOT choose or confirm, default to the transcript's dominant
  language.** This avoids adding a translation layer, which is a major source of
  hallucination and of softened political terminology.
- If output language ≠ transcript language, treat the job as ALSO a translation —
  see "Language policy" below.
- For a multilingual transcript, pick ONE output language and note which passages
  were interpreted/translated in the source (interpretation can introduce errors,
  so flag those like ASR uncertainties).

### 3. Load the rules for this run
Read and apply, for the confirmed genre:
- `references/genre-playbooks.md` — restructuring strategy + attribution rules.
- `references/voice-and-fidelity.md` — fidelity, political-voice, quotes & evidence.
- `references/writing-style.md` — the prose style the draft should achieve.
- `glossary.md` — terminology to preserve exactly (editable; extend per project).

### 4. Stage 1 — Outline (human checkpoint)
Produce a genre-appropriate **outline** (headings + sub-points), NOT a draft.
This is the editing pass done cheaply, before any prose exists. Include:
- The **restructuring logic** in one line (how you regrouped speaking order).
- 2–3 **lede/opening options** to choose from (see writing-style → Openings).
- A **⚠ Verify** list: every proper noun, organisation, place, statistic, date,
  or quote you're not confident the transcript got right (ASR mangles names from
  many languages — never guess these).
- A **Gaps** note: claims that are asserted but thin/underdeveloped in the
  source, so the user can decide to cut, soften, or supplement them. The skill
  does NOT fill gaps from outside sources — supplementing is the user's call and
  the user's material.

**Present the outline + Verify list + Gaps, and stop for approval/edits.**

### 5. Stage 2 — Draft
Expand the **approved** outline into the article. Follow the structure exactly.
Apply `writing-style.md` and `voice-and-fidelity.md` throughout: rewrite speech
into clean analytical prose, remove filler/repetition/crosstalk, build a lede and
transitions — but invent nothing, never soften the political content, and keep
attributions where naming the speaker/organisation carries meaning. Integrate
verbatim quotes only for the lines marked quotable, each with its context.

### 6. Stage 3 — Self-review & revise
Before handing back, run the **Quality checklist** in `references/writing-style.md`
against the draft and fix what fails (sourcing, attribution integrity, neutralised
terminology, weak transitions, AI tells). Then offer the user a revision loop —
accept natural-language change requests and re-apply without re-running stages 1–2.

### 7. Hand off (optional)
These are downstream, publication-specific steps. This skill does not require any
other skill to be installed; mention these only as options the user may run if
they have the relevant tool:
- A de-AI / "humanising" pass on the prose (if the user has such a skill).
- A mechanical proofreading pass against the publication's style guide.
- A heavier publishing format (`.docx` / `.pdf`) via the publication's own
  converter — kept downstream, not done here.

## Outputs

Default deliverables for a finished article — **self-contained, no other skill
required**:

1. **Markdown (`.md`) — the canonical, editable source.** Everything is authored
   in Markdown; this is the file edits and revisions happen to.
2. **HTML — a rendered preview/shareable copy, generated FROM the Markdown** using
   the bundled template `assets/article-template.html`. Convert the final
   Markdown body to HTML and substitute it into the template's `{{CONTENT}}`
   placeholder (also fill `{{TITLE}}` and `{{LANG}}`). Do NOT hand-author bespoke
   HTML/CSS — use the template so styling stays consistent. (If the user happens
   to have a dedicated md→html tool they prefer, they may use it instead.)

Rules:
- Produce the HTML only **after** the draft is approved at Stage 6, and
  **regenerate** it after any later revision so it never goes stale.
- Filename follows the article title; save both files together (default:
  alongside the transcript, or wherever the user specifies). Ask before writing
  files if the location isn't obvious.
- Heavier formats (`.docx`/`.pdf`) remain a downstream step, not part of this skill.

## Language policy (when output language ≠ transcript language)

Translating is itself a fidelity risk — apply these in addition to the normal rules:

- **Stay closed-book.** Translation does not license adding outside context.
- **Protect the political terminology in the target language.** Extend
  `glossary.md` with the target-language equivalents so charged terms
  (imperialism, sovereignty, the Global South, etc.) aren't softened in
  translation. Don't let a translation neutralise what the original asserted.
- **Render quotes in the output language, faithfully.** A quote may be given in
  the article's language; translate it accurately and do not add labels like
  "(translated from X)". If a single charged word is hard to render, you may keep
  the original term in brackets — but this is the exception, not a routine mark.
- **Prefer a dedicated translation step.** For anything beyond light rendering,
  translate the finished piece with a glossary-aware translation step (if the user
  has a dedicated translation skill, use it) rather than translating loosely
  inside the draft.

## Hard rules (always)

1. **Closed-book on the source.** The article must be built ENTIRELY from the
   supplied transcript and any supporting materials the user provides (speaker
   notes, scripts, slides, papers). Content, argument, and logic come mainly from
   the speakers. Do NOT consult the web, search engines, or your own background
   knowledge to
   add facts, context, dates, or figures — outside sources are the main cause of
   hallucination here. Only go to external sources if the user explicitly asks,
   and then mark clearly what came from outside vs. from the transcript.
2. **Never invent** facts, figures, quotes, or attributions. Absent ≠ inferred.
   If the transcript doesn't establish a bridge, write around it or flag it.
3. **Flag, don't guess** uncertain names/places/numbers from the transcript.
4. **Never neutralise** the speakers' politics (see `voice-and-fidelity.md`).
5. **Attribute correctly** — never move a position to the wrong speaker.
6. **Stop at the outline** for human approval before drafting.
