---
name: conference
description: 'Run my Conference companion on Trilium, from any repo. Use when I want to plan which Sessions to follow at a conference, capture a takeaway during one ("takeaway: …", "cosa vedo dopo?"), or write the recap afterwards.'
---

# conference — the companion

I go to Conferences as an attendee, sometimes as a speaker too. You help me before (pick the Sessions worth
my time), during (catch my Takeaways fast) and after (turn them into a Recap I can reread and act on).
Everything lives in **one Trilium note per Conference**, through the `trilium` MCP server.

## Words

- **Conference**: an event I go to. **Session**: one item on its program, given by someone else. **Talk**:
  only ever *my* talk, a content topic in Contenuti.
- **Agenda**: the Sessions I pick to follow. **Takeaway**: something I carry away, with a kind:
  `approfondire | provare | condividere | contattare`. **Recap**: my written summary, with follow-ups.
- **Live lane**: short posts born from the moment, here from a Takeaway; the planned **Queue** belongs to
  the `tweets` skill.

## Pick the phase

Read only the file for the phase in front of you:

- No note for this Conference yet, or I want an Agenda: [prepare.md](prepare.md).
- During the Conference ("takeaway: …", a raw thought, "cosa vedo dopo?", a post to share):
  [capture.md](capture.md).
- After it ("fai il recap", follow-ups, a deck for the team): [recap.md](recap.md).

When I name no Conference, use the one with `#status=active`; with none or several, ask in one line.

## The Conference note

A Project in Trilium (read "Convenzioni per Claude" `kg6Nk6GFhfZK` before your first write):

- Child of **Progetti** `Gbou0FRbp5Ln`, `type: "text"`, titled `<Name> <year>` (e.g. `GoLab 2026`).
- label `type` = `project`, relation `template` = `t079A0nGpIku` (Project), relation `area` = the
  **Conferenze** hub under Aree (`search_notes` for `note.title = "Conferenze" note.parents.title = "Aree"`).
  When the hub is missing, stop and ask me to create it: the structure of Trilium is mine to change.
- label `status`: `paused` (I'm going, no Agenda yet) → `active` (Agenda ready) → `done` (Recap written).
  Archiving is mine: you never move the note.

Find my Conferences with `#type=project ~area.title = "Conferenze"`.

The body, in Italian, Session titles in their original language, sections in this order:

```markdown
**Dove**: <città> · **Quando**: <YYYY-MM-DD → YYYY-MM-DD> · **Programma**: <url>

## Obiettivi
## Talk          ← only when I speak there
## Agenda
## Da smistare
## Takeaways
## Recap
```

Each phase file says what goes in its sections. To change one section: `get_note_content`, edit only that
section, write the whole body back with `set_note_content` (`edit_note_content` does not work on text
notes). Link notes with Trilium internal links, `[title](#root/<noteId>)`, only to notes that exist.

If the `trilium` tools are missing or a call fails, say which, and give me in chat whatever you were about to
write, so nothing is lost.

---

_Self-contained on purpose: installed from `davideimola/skills` and run from any repo. During a Conference I
drive it from my phone through Claude Code's Remote Control, since the Claude app cannot load my MCP
servers. Why a Conference is a Project: `docs/adr/0001-conference-is-a-project.md` in this repo._
