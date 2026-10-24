# Before: the Agenda

## 1. The note

Find the Conference note. Without one, create it as [SKILL.md](SKILL.md) describes, with `#status=paused`,
and ask me:

- the program URL, the city and the dates;
- my **Obiettivi** for this Conference: 2-3 lines on what I want to come home with. Write them verbatim in
  `## Obiettivi`.

When I speak there, find my Talk in Contenuti `l78292msrPRH` (`#channels=talk`, the Conference named in its
`## Talk` section) and write under `## Talk` a link to it, with the day and time I speak.

Done when the note exists with its header line and `## Obiettivi` filled.

## 2. The program

Best effort, no scraper per site:

1. The program URL. Sessionize-backed programs expose JSON
   (`https://sessionize.com/api/v2/<id>/view/All`); look for it in the page before parsing HTML.
2. The page itself, its schedule and each Session's abstract.
3. Neither works: ask me to paste the program (text, PDF, a screenshot).

Done when you hold every Session with title, speaker, day, time, room and abstract. Keep the program out of
the note: the note links it in the header line.

## 3. What I care about

Two sources, the Obiettivi weighing more:

- **Obiettivi** of this Conference, from the note.
- **Standing interests**, read fresh each time: my positioning in Aree/Pipeline contenuti `I78vgbZLZnde`,
  active Projects in Progetti `Gbou0FRbp5Ln`, Contenuti with `#status=in-progress`.

Done when you can name, in a line each, what I am after at this Conference.

## 4. Propose the Agenda

Per time block, one pick and, when it is a close call, one alternative. Every pick carries a **reason** in
one line that ties the abstract to an Obiettivo or an interest. Leave a time block empty when nothing earns
it: the hallway is a fine choice. Flag picks whose times overlap only in part, and say which part I lose.

When I speak, my time block is blocked, and so is the one right before it (I am preparing).

Show it in chat, iterate until I approve, then write it under `## Agenda`, one `###` per day:

```markdown
### 2026-11-02
- 10:00–10:45 · **<Session title>** · <speaker> · <sala>
  Perché: <reason> · Alternativa: **<title>** (<one-line reason>)
- 11:00–11:45 · *bloccato: prep del mio Talk*
```

Then set `#status=active`. Done when the Agenda is in the note and the status is `active`. Reply with one
line per day: how many Sessions, and the one you would least want me to miss.
