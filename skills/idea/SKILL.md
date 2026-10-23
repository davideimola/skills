---
name: idea
description: Capture a raw content spark as an idea note in Davide's Trilium Inbox, from any repo. Use when Davide wants to jot down a content idea or spark and file it fast — capture first, judge later.
---

# idea — the capture door

File the spark Davide just gave you as a raw content idea in his Trilium Inbox, then confirm. **Capture
first, judge later**: your whole job is to file the spark faithfully; it is judged later, when he works
the Contenuti board. File it as-is and add nothing of your own — no channel, no format, no quality
verdict, no draft or rewrite.

The **spark** is whatever Davide gave you with the invocation — the words after `/idea`, or the idea he
just expressed. With no spark, ask for it in one line and stop.

## Filing it

Through the `trilium` MCP server:

1. `create_note` with `parentNoteId: "oI6dJqP0hGHG"` (the Inbox), `type: "text"`, the title below, and
   the spark **verbatim** as `content` (copy it exactly, typos and all).
2. On the new note, `set_attribute` three times:
   - label `type` = `content`
   - label `status` = `idea`
   - relation `template` = `HtMZvVGrddyG` (Content Item, which carries the content fields)

The **title** is a short, readable summary of the idea's core (its thesis or subject), in the spark's
language, one scannable line (aim under ~70 chars). This is the one place you rephrase — and even here
you name the topic, never rate it.

Done when the note exists in the Inbox with all three attributes.

Reply with **only** a one-line confirmation carrying the title (e.g. `Captured idea "<title>" in Trilium`).
If the `trilium` tools are missing or a call fails, say exactly that on one line, with the spark quoted
so it is not lost.

---

_Self-contained on purpose: installed from `davideimola/skills` and run from any repo. If the Inbox or
the template is ever recreated, find the new IDs with `search_notes` for `#inbox` and for
`#template note.title = "Content Item"`. Schema of content notes: "Convenzioni per Claude" in Trilium's
Sistema._
