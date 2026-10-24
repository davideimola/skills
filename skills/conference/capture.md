# During: Takeaways

I am on my phone between Sessions, often mid-talk. Every reply fits a phone screen: short, no tables.

## Fold `## Da smistare` first

On every run, before anything else: any line under `## Da smistare` is something I typed by hand in Trilium. Turn
each into a Takeaway (below) and empty `## Da smistare`. Do it in the same write as the rest of the run.

## A Takeaway

Whatever I give you ("takeaway: …", or just a thought) becomes one line under `## Takeaways`:

```markdown
- **[provare]** <my words, tightened, never embellished> · <Session title or "corridoio"> · <HH:MM>
```

- **Kind**: `approfondire` (study it), `provare` (try it), `condividere` (worth telling people),
  `contattare` (a person to reach: name, why, where to find them). Pick the one my words imply; when unsure,
  ask with the four kinds as choices.
- **Session**: the one running now in my Agenda, unless I say otherwise.
- Links, tools and names I mention go in the line as they are.

Done when the line is in the note. Reply in one line: `Salvato [kind]: <first words>`.

## A post for the Live lane

When a Takeaway is `condividere`, or I ask for a post, propose **one** short post in chat:

- English, my voice: read the **Voice** section of
  `gh api repos/davideimola/brand/contents/docs/brand.md -H "Accept: application/vnd.github.raw"`.
- One post, at most 280 characters on X, 300 on Bluesky; first person, specific, no em dashes, one hashtag
  only if it truly helps. A link goes in a second post of the thread (`posts[1]`), so the first carries the
  value on its own. Mentions: Bluesky needs the person's Bluesky handle or their name, so show both
  versions.

Iterate until I say yes **to that text**, and ask when: now, or a day and time. Then `create_draft` on
Typefully social set `97290`, `platforms.x` and `platforms.bluesky` enabled, `linkedin` never,
`draft_title` the topic, `scratchpad_text` the Conference and Session:

- now: `publish_at: "now"` with `confirm_publish: true`;
- later: `publish_at` the ISO datetime I gave, with timezone.

My yes to the text and the timing is the only thing that publishes: without it, nothing goes out. Done when
the draft exists on Typefully, or I passed on the post. Reply with where and when it goes.

## "Cosa vedo dopo?"

Look at the next time block in the Agenda and its alternatives, in the light of today's Takeaways. Answer with the
pick and one line of why; mention the alternative only if today changed the call. Update `## Agenda` only
when I switch.
