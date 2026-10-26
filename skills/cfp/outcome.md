# Outcome: what happened to a CFP

Runs at the end of every scout round, and whenever I tell you how a CFP went.

## 1. Which CFPs to ask about

Load every Talk note ([SKILL.md](SKILL.md)) and read its `## Talk` lines: the CFPs with Outcome
`CFP inviato` are the candidates. Never find them with a text search, which matches the words anywhere.
A CFP is due when the **Notifica** date in its `CFP <Conference Year>` note has passed, or its Conference
starts within eight weeks, or neither date is known. When I named a CFP myself, that one only.

Done when you have every due CFP, or none: then say so in one line and stop.

## 2. Ask

One message, one line per CFP: `<Talk> · <Conference Year>: accettato, rifiutato o ancora niente?`

## 3. Record

- **accettato**: on the Talk note, the Outcome to `CFP accettato`; `status` to `in-progress` when it is
  `idea` (a `published` Talk changes only on my yes); `talkDate` to the day I speak, which you ask me,
  with the Conference start as the proposal. When `talkDate` already holds a date still to come, keep the
  earlier one. Then remind me to develop the Talk with `talk-forge` in `davideimola/presentations`, and
  offer the Conference Project below.
- **rifiutato**: only the Outcome, to `CFP rifiutato`. The Talk stays a candidate for the next Call.
- **ancora niente**: leave it; it comes back next round.

Done when every answer I gave is on its Talk note.

## The Conference Project

On an accepted CFP, offer it once. When I accept, first look for one (`#type=project ~area.title =
"Conferenze"` with the Conference's name); with none, create it as the `conference` skill reads it:

- Child of Progetti `Gbou0FRbp5Ln`, `type: "text"`, titled `<Name> <year>`.
- label `type` = `project`, relation `template` = `t079A0nGpIku` (Project), relation `area` =
  `X8WYWSLmfXHr` (Conferenze), label `status` = `paused`.
- Body:

  ```markdown
  **Dove**: <città> · **Quando**: <YYYY-MM-DD → YYYY-MM-DD> · **Programma**: <url, when known>

  ## Obiettivi
  ## Talk
  [<Talk title>](#root/<Talk noteId>) · <day and time, when known>
  ## Agenda
  ## Da smistare
  ## Takeaways
  ## Recap
  ```

From there `conference` takes over. Done when the Project exists, or I passed.
