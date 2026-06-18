# transcript-to-article

A Claude Code / Claude Agent **skill** that turns a raw transcript — a panel,
webinar, lecture, keynote, interview, conference session, debate, or roundtable —
into a polished, publication-ready article.

It is built for **political and intellectual discussion** (Global South
organisations, movements, and research institutes), not business meetings. It
auto-detects the transcript's genre, restructures the material accordingly,
preserves the speakers' political voice and terminology, and **never invents
facts** — uncertain names and figures are flagged for you to verify, not guessed.

## What makes it different from a generic "write an article" prompt

- **Genre-aware.** A panel is re-clustered into themes; a lecture keeps its
  argumentative arc; a debate preserves the dialectic. It confirms the genre with
  you before drafting.
- **Closed-book / no hallucination.** The article is built only from your
  transcript plus any supporting materials you provide (slides, speaker notes,
  scripts). It does not browse the web or add outside "facts".
- **Keeps the politics.** It will not soften charged terminology
  (imperialism, occupation, sovereignty, the Global South…) or add false balance.
  An editable `glossary.md` lists protected terms.
- **Human checkpoint.** It produces an outline (plus a ⚠ verify-list and a gaps
  note) and stops for your approval before writing the full draft.
- **Output language follows the transcript** unless you ask otherwise (avoids a
  hidden translation layer).
- **Self-contained outputs.** Markdown (canonical) + a styled HTML preview from a
  bundled template. No other skill required.

## Install

1. Copy the whole `transcript-to-article/` folder into your skills directory:
   - **Personal (all projects):** `~/.claude/skills/`
   - **One project only:** `<project>/.claude/skills/`
2. Restart Claude Code / the VS Code extension to refresh the skill list.
3. Confirm it loaded — you should see `transcript-to-article` available.

> `~/.claude` is a hidden folder. In Finder press **Cmd + Shift + .** to show
> hidden files, or open it from a terminal with `open ~/.claude/skills`.

## Use

Give it a transcript and ask for an article:

```
Turn @transcript.txt into an article
```

You can also attach supporting materials and a style sample:

```
Write an article from @transcript.srt. Use @slides.pdf and @speaker-notes.docx
to check names and figures, and match the voice of @past-article.md.
```

It will:
1. read the transcript (and any materials),
2. tell you the detected **genre** and **output language** and wait for your OK,
3. give you an **outline** + a list of names/numbers to verify + thin claims,
4. on approval, write the **draft**, then self-review against a quality checklist,
5. deliver **Markdown** (+ an **HTML** preview) and accept revision requests.

## What's inside

```
transcript-to-article/
├── SKILL.md                      The workflow + hard rules (entry point)
├── glossary.md                   Protected terminology (edit / extend per project)
├── README.md                     This file
├── assets/
│   └── article-template.html     Standalone HTML template for the preview
└── references/
    ├── genre-playbooks.md        Per-genre restructuring strategies
    ├── voice-and-fidelity.md     Fidelity, political voice, quotes, evidence
    └── writing-style.md          The target prose style + quality checklist
```

## Customise it

- **`glossary.md`** — add your project's people, organisations, acronyms,
  preferred spellings, and (for non-English output) target-language equivalents.
- **`references/writing-style.md`** — adjust the house style, or just feed a past
  article as a style sample at run time and it will match that instead.

## Notes & limits

- It does light formatting and an HTML preview, but heavier publishing formats
  (`.docx` / `.pdf`) and mechanical proofreading are left to downstream tools.
- It flags transcription uncertainties; it does not silently "fix" them — that
  verification is yours.

## Licence

Share and adapt freely.
