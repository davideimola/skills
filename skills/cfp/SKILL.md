---
name: cfp
description: 'Find open Calls for papers and bring my Talks to them, tracked on Trilium, from any repo. Use when I want to scout Calls ("cerca CFP"), shape a Talk idea for a Call, answer a CFP form, or record a CFP outcome.'
---

# cfp — from a Call to a submitted Talk

Every two weeks I look for Calls worth answering, match them to my Talks, and submit. You find the Calls,
pitch the Talk that fits (or a new one), help me answer the form, and keep each CFP's Outcome honest.
State lives in Trilium, through the `trilium` MCP server.

## Words

- **Call**: a Conference's open call for papers, found while scouting: deadline, link, themes. It stays a
  Call until I decide to submit; it is never stored beyond its line in the Radar note.
- **CFP**: one of my Talks submitted to one Conference, a line on the Talk's note with its **Outcome**.
  One Talk has many CFPs.
- **Talk**: only ever *my* talk, a content topic in Contenuti. **Abstract**: its three-to-five-line pitch.
  **Proposta**: what it needs to be submitted before it is developed (audience, three takeaways, rough
  outline, why me). **Brief**: the full `TALK.md` beside its slides in `davideimola/presentations`, which
  exists only once a Talk is developed.
- **Conference**: an event I go to, as attendee, speaker or both.

## Pick the phase

Read only the file for the phase in front of you:

- "cerca CFP", a periodic run, or `/cfp` with nothing specific: [scout.md](scout.md).
- "invio" on a Call with a new Talk, or "strutturiamo questo talk per la CFP": [pitch.md](pitch.md).
- "rispondiamo alla CFP", pasted form questions, "l'ho inviata": [submit.md](submit.md).
- "com'è andata la CFP", "mi hanno accettato/rifiutato", and the end of every scout round:
  [outcome.md](outcome.md).

## The Talk note

In Contenuti `l78292msrPRH`: label `type` = `content`, label `channels` = `talk`, relation `template` =
`HtMZvVGrddyG` (Content Item), label `status` = `idea | in-progress | published | archived`, label
`flagSide` = `flag | side`. Archived Talks are never candidates. Find my Talks with
`#type="content" #channels="talk" #status != "archived"`.

The body keeps its language: a new note is written in the language of the Call that triggered it (its
Abstract and Proposta go into that Call's form), in Italian when no Call did. It keeps whatever it has and
grows these sections:

```markdown
<the original spark, as I said it: transcription and punctuation repaired, meaning untouched>

## Abstract
<three to five lines>

## Proposta
**Pubblico**: <who, at what level>
**Takeaway**:
1. <concrete, something they do on Monday>
2. …
3. …
**Scaletta**:
1. <three to five points>
**Perché io**: <what I have done that makes me the one to give it>

## Talk
*   **GoLab 2026** (2026-11-01 → 2026-11-03, Bologna, Italy) — CFP accettato — [https://golab.io/](https://golab.io/)
```

Title and format are tuned per CFP and stay out of the Proposta. A Talk has a Brief when a `TALK.md` in
`davideimola/presentations` names it (by note ID or title): list them with
`gh api "repos/davideimola/presentations/git/trees/main?recursive=1" --jq '.tree[].path | select(endswith("TALK.md"))'`
and read each header with `gh api repos/davideimola/presentations/contents/<path> -H "Accept: application/vnd.github.raw"`.

## The CFP line

One line per Conference edition in the Talk note's `## Talk` section, the format already in use:

```markdown
*   **<Conference Year>** (<YYYY-MM-DD → YYYY-MM-DD>, <City, Country>) — <Outcome> — <homepage URL>
```

Outcomes: `CFP da inviare (scadenza YYYY-MM-DD)` → `CFP inviato` → `CFP accettato` or `CFP rifiutato`.
Leave out dates or city when unknown. **Create-if-missing**: a line for the same Conference edition is
reused, never duplicated; the year tells editions apart. Without a `## Talk` section, add one after
`## Proposta`, or after the spark when there is none. Logistics only: answers live in the child note
`CFP <Conference Year>` ([submit.md](submit.md)).

## The Radar note

"Radar Call", child of the Conferenze hub `X8WYWSLmfXHr` (under Aree). Body in Italian:

```markdown
**Ultimo giro**: YYYY-MM-DD

## Regola
<my distance rule, in my words>

## Temi
<the themes I submit on, in my words>

## Watchlist
- <Conference> · <its CFP page>

## Già viste
- <Conference Year> · <city> · <Call link> · <YYYY-MM-DD seen>
```

A Call is identified by its **Call link**: one Conference edition can open several Calls (a main track, a
devroom), each with its own link, and seeing one never hides another.

`## Regola`, `## Temi` and `## Watchlist` are mine: you only read them. You write only `## Già viste` and the
`**Ultimo giro**` line. When the note or the hub is missing, stop and ask me to create it with those
sections: the structure of Trilium is mine to change.

## Writing to Trilium

Read "Convenzioni per Claude" `kg6Nk6GFhfZK` before your first write of a run. Then:

- **My yes for that write.** Show what changes, note by note, and write only after I say yes to it.
- **Bodies whole.** To change a section: `get_note_content`, edit only that section, write the whole body
  back with `set_note_content`, every other line and link exactly as read (`edit_note_content` does not
  work on text notes).
- **Single-value labels only.** `set_attribute` overwrites a label of the same name, so on an existing
  note you touch only `status` and `talkDate`, never a multi-value label like `channels` or `artifact`.
- Link notes with Trilium internal links, `[title](#root/<noteId>)`, only to notes that exist.

Searching has two traps. **Quote every label value**: `#status="in-progress"` matches, `#status=in-progress`
silently returns nothing. **Never find an Outcome with a text search**: `"CFP inviato"` matches the words
anywhere in a note, not the phrase. Load the Talk notes (they are few) and read their `## Talk` lines.

If the `trilium` tools are missing or a call fails, say which, and give me in chat everything you were
about to write, so nothing is lost.

## Language

We talk in Italian. The Radar note is in Italian; a Talk note follows [The Talk note](#the-talk-note); CFP
answers are in the CFP's language (ask when the Call does not make it clear). Conference and Session names stay in their original language.

---

_Self-contained on purpose: installed from `davideimola/skills` and run from any repo. A Talk is submitted
before it is developed, so nothing here needs `presentations`; an accepted Talk moves there to
`talk-forge`. Why the CFP lifecycle lives here: `docs/adr/0002-cfp-lifecycle-lives-in-skills.md` in this
repo._
