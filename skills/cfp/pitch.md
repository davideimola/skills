# Pitch: from an idea to a submittable Talk

A new Talk idea is a one-line spark, too thin to submit. This phase turns it into a Talk note with an
Abstract and a Proposta: enough to fill any CFP form, without developing the Talk.

## 1. The idea and the Call

Take the idea from the scout round, or from me. Hold the Call that triggered it (Conference, dates, city,
deadline, themes, link) when there is one. Look for a Talk note or an `/idea` note in the Inbox on the same
subject: when one exists, we grow that note instead of creating another, and moving an Inbox note to
Contenuti waits for my yes.

Done when you know which note this becomes and which Call, if any, it is for.

## 2. Grill it

Be a demanding editor: the CFPs that get thrown out are the generic ones. One question at a time, each with
your own proposed answer, until the idea holds:

- **Thesis**: one sentence I would defend on stage. "AI is useful for security" is a topic, not a thesis.
- **Anyone could say this**: what in it comes from what I have done, and nobody else has?
- **Takeaways**: three things the audience does differently on Monday. "Understand X" is not one.
- **This Call**: does it land on the Call's themes and audience, or is it bent to fit?

Done when the thesis fits one sentence, the three takeaways are concrete, and "why me" names something I
did.

## 3. Draft the Abstract and the Proposta

In the shapes in [SKILL.md](SKILL.md), in Italian unless the note is already in English: an Abstract of
three to five lines, and a Proposta with audience, three takeaways, a rough outline of three to five points
and why me. Title and format stay out: they are tuned per CFP. Show both, iterate until I say ok.

## 4. Write the Talk note

A new note: `create_note` under Contenuti `l78292msrPRH`, `type: "text"`, titled with the working title,
the body below; then `set_attribute` label `type` = `content`, label `status` = `idea`, label `channels` =
`talk`, relation `template` = `HtMZvVGrddyG`. An existing note: add the sections to its body, attributes
untouched, except `channels` = `talk` when it has no `channels` label at all; with another channel already
there, ask me to add `talk` by hand.

```markdown
<the spark, verbatim>

## Abstract
## Proposta
## Talk
*   **<Conference Year>** (<dates>, <city>) — CFP da inviare (scadenza <YYYY-MM-DD>) — <homepage>
```

The `## Talk` line only when a Call triggered this, create-if-missing. Done when the note exists with
`#status=idea`, Abstract, Proposta and, with a Call, its CFP line. Reply with the title and the line, then
offer to answer the form now ([submit.md](submit.md)).
