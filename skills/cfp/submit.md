# Submit: answering the CFP form

I send the form myself. You help me answer it, keep the answers in Trilium for the next submission, and
move the CFP line to `CFP inviato` once I've sent it.

## 1. What we answer

Ask in one message for what you don't already have:

- **Talk**: find its note ([SKILL.md](SKILL.md)); without one, a new Talk goes through
  [pitch.md](pitch.md) first.
- **Conference**: name, year, public homepage, deadline.
- **The form's questions**: pasted by me, or read from the public CFP page when it lists them. Only public
  pages: logged-in portals (Sessionize speaker area, Pretalx admin) are mine to open.

Note the notification date when the CFP page states it.

Done when you hold the Talk note, the Conference and every question.

## 2. What the Talk already says

Read the Talk note: spark, `## Abstract`, `## Proposta`, `## Talk`. Read its child notes `CFP <…>`: earlier
submissions of the same Talk are the starting point. When the Talk has a Brief ([SKILL.md](SKILL.md)),
read it too: a developed Talk is pitched with its real content.

## 3. The CFP line

Create-if-missing on the Talk note, with `CFP da inviare (scadenza <YYYY-MM-DD>)` ([SKILL.md](SKILL.md)).
An existing line for this edition is reused as it is.

## 4. Already answered?

When the child note `CFP <Conference Year>` exists, show me which questions it already answers and ask:
add new questions, reword some, or neither. A finished answer is rewritten only on my explicit ask, and
new questions go through steps 5-7 like the first ones.

## 5. Framing from the homepage

Fetch the Conference's public homepage and read: the audience's seniority and mix (dev-only or with
managers), the language, past editions and their talks (the editorial angle), the tracks. When the page
renders nothing useful, say "Non riesco a ricavare il framing dalla homepage" and ask me to describe the
audience and angle.

## 6. Adapt the Talk

Before the answers, ask with your own draft from the framing:

- Is this audience more senior or junior than usual? Do we change the depth?
- Does the thesis hold for them, or does it need reframing?
- Which title works for this CFP?

Typical pressure check: "GoLab is 90% senior Go. Your Talk is DDD applied to Go. 'DDD is useful in Go' is
trivial for that audience. Reframe it."

## 7. Answers, one at a time

For each question, in the CFP's language:

1. Draft it from the Abstract, the Proposta, earlier submissions, the Brief if any, and the framing.
2. **Pressure check**: say explicitly whether it is generic, buzzword-stuffed, valid for any talk, or not
   specific to this Conference.
3. I reply or correct; you reword. Iterate until I say ok.

Pressure checks look like:

- "The bio says 'passionate developer'. Delete it. What have you concretely done in the last 12 months?"
- "This 'why this talk?' fits any talk. What makes it specific to *this* Conference?"
- "The abstract is 350 characters and the form allows 500. Leave the margin empty, or add the hook?"
- "'You'll learn X, Y, Z' is didactic. For Codeway it works. For GoLab it's a keynote in disguise."

Done when every question has an answer I said ok to.

## 8. Save the answers

A child note of the Talk note, `type: "text"`, titled `CFP <Conference Year>`, no labels of its own: it is
part of the Talk. Body:

```markdown
**Call**: <link> · **Scadenza**: <YYYY-MM-DD> · **Notifica**: <YYYY-MM-DD, when known> · **Lingua**: <it|en>

## <Question 1, as the form asks it>
<final answer>

## <Question 2>
<final answer>
```

On a re-run, write into the existing note: new questions appended, reworded answers replaced, everything
else as read. I may stop halfway and come back: save what is ok so far.

Done when every ok'd answer is in the note.

## 9. Sent

When I confirm I've sent the form, and only then, change that line's Outcome to `CFP inviato`. Reply with
the Talk, the CFP line and its Outcome, and the answers note.
