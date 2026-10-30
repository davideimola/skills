---
name: social-post
description: Write a LinkedIn post for something I made (a blog post, a talk, a project, an event), build a branded image when one helps, and plan it as a draft in Typefully. Use when I want to promote something on LinkedIn ("prepara il post LinkedIn", "social per l'ultimo post", "/social-post"), from any repo.
---

# social-post — the LinkedIn lane

You write LinkedIn posts in my voice: direct, first person, opinionated, with self-deprecating humour
when it fits. I never sound like a corporate account.

When the post amplifies something with a home of its own (a blog post, a page on my site), you write a
**sneak-peek amplifier**: a real taste of the piece that points home for the rest, deliberately **not**
a copy of it. A LinkedIn post that reproduces the whole blog post depresses the post's own reach. For a
talk, a project or an event with no page to point to, the post stays self-contained instead.

You never publish. The post ends as a **planned** draft in Typefully, and it goes out only when I
confirm it there. Short posts for X and Bluesky are the `tweets` skill's job, never a trimmed copy of
this one.

## Trilium

Every piece of my writing has a **content note** in Trilium (`trilium` MCP), one note per topic, not
per channel. Read "Convenzioni per Claude" `kg6Nk6GFhfZK` before your first write of a run: it is the
authoritative schema. What this skill touches:

- `#channels`: one label per channel (`blog`, `linkedin`, `talk`). The LinkedIn post of a blog post
  normally lives on the **same** note as the post. A second LinkedIn post on the same topic gets its
  own note.
- `#linkedinDate` (ISO) and `#linkedin` (the published URL). A channel is published when its URL is set.
- `#artifact`: links to drafts, one label each, multi-valued.
- `#status`: `idea → in-progress → published`.

Touch only those. Two MCP gotchas:

- `set_attribute` **overwrites** a label with the same name, so it cannot add a second value to
  `#channels` or `#artifact`. Check `get_note` first: if the label is absent, set it; if it already
  has a value, never call `set_attribute` on it.
- `edit_note_content` does not work on text notes: to change a body, `get_note_content`, edit the
  Markdown and write it back whole with `set_note_content`, links included.

## 1. Gather the content

Depending on what I gave you:

- **A content note** (its title): `search_notes`, then `get_note` (`#flagSide`, `#channels`,
  `#linkedinDate`, `#blog`, `#artifact`) and `get_note_content` (the body opens with the original
  spark, verbatim).
- **A blog post** (slug or URL): read `https://davideimola.dev/blog/<slug>.md`, the post as plain
  Markdown. Look up its content note too: `search_notes` for the slug or the post title.
- **Free text**: use it as the source.
- **Nothing**: list the content notes with `linkedin` in `#channels` and no `#linkedin` URL yet,
  soonest `#linkedinDate` first, and ask: "Cosa vuoi promuovere? Uno di questi, uno slug di post, o
  descrivimelo."

When both a note and a post exist, read both: the note carries the framing, the post the content.

## 2. Write the post

Read the **Voice** section of my brand guidelines first:
`gh api repos/davideimola/brand/contents/docs/brand.md -H "Accept: application/vnd.github.raw"`. The
rules below apply it to LinkedIn; where they disagree, the brand wins and this file needs fixing.

One fact from my own analytics (2026-07) governs the feed: a bare promo ("new post, go read it") gets
5-20x fewer impressions than a post that carries real value. So pay out a genuine taste (the hook, one
real specific, the shape of the idea), then stop at the threshold and point home for the payoff.

1. **Hook**: the first line stops the scroll. A counterintuitive statement, a specific problem, a
   blunt opinion. Never "I'm excited to share...".
2. **Body**: 3-6 paragraphs, first person, flowing prose: full sentences that connect and let the
   story breathe, never staccato one-liners. One concrete detail or turn worth reading. Leave the full
   argument at home.
3. **CTA**: one line naming what the reader gets by clicking through (the rest of the story, the how,
   the numbers), then the link, at the bottom of the body. "Link in the first comment" does not help
   on my posts. A closing question only if it is interesting on its own: "How do you structure your
   X?" reads as bait.

Line breaks between paragraphs, conversational sentences inside them. The tone benchmark is the
[ReactJS Day 2026 post](https://github.com/davideimola/davideimola.dev/blob/main/.carousel/reactjsday-2026-speaker/social-post.md):
warm, discursive, never telegraphic.

**Never write**: "Excited to share", "Thrilled to announce", "In this article, we explore", "Let's
dive into", "It's worth noting", "game-changer", "leverage", "seamlessly", "delve"; em dashes; passive
sentences with no subject ("Security improves when..."); bullet lists that repeat what was just said;
any sentence that could be about any topic. If a sentence reads like a press release, rewrite it.

**Always**: direct opinions without hedging, specifics (names, tools, numbers, events) over generic
statements, humour only where it fits naturally.

### The visual

Default to a single branded image in portrait 4:5 (1080x1350, more feed space on mobile than a
square), or no image at all for pure storytelling. A post with a link already shows my site's card as
its preview, so it often needs nothing else. Carousel reach is declining (2026-07): propose one only
for genuinely step-by-step content (a process, numbered lessons, a before and after), never for a
story or a reflection.

State your call first ("a carousel works here because X", "I'd skip the image: the story carries it"),
then propose the slides (6-10, title and one line each, the one with the strongest pull quote) or say
why not.

## 3. Show and iterate

Show me the post and the visual plan with your honest opinion: what works, what sounds generic or off
brand. Ask "Cosa cambieresti? Il tono, il hook, l'immagine?" and iterate until I approve. Push back
when a change weakens the post.

## 4. Build the image

Only with an approved visual. The slides are throwaway: build them in a scratch directory (your
scratchpad, or a fresh `mktemp -d`), never in a repo. Nothing from this step is committed.

`mkcr` lives at `/Users/davideimola/.local/share/mise/installs/go/1.26.1/bin/mkcr` (not on `PATH`, and
the mise shim fails outside a Go project): `mkcr` below means that path. Run it from the scratch
directory:

```sh
mkcr init <slug> --format vertical   # single 4:5 image; --format square for a carousel
mkcr preview <slug>
mkcr render <slug> --format png --output <slug>/out   # single image
mkcr render <slug>                                     # carousel, a PDF
```

Each slide is a numbered HTML file (`1.html`, `2.html`, ...) holding only inner content (no
html/head/body), styled with Tailwind and inline styles, next to the `carousel.json` that `mkcr init`
writes. Load the fonts at the top of each slide:

```html
<style>
  @import url('https://fonts.googleapis.com/css2?family=Schibsted+Grotesk:wght@400;600;700&family=IBM+Plex+Mono:wght@400;500&family=Barlow+Condensed:wght@700&display=swap');
</style>
```

After `mkcr preview`, ask me about layout and balance, iterate, then render.

### Brand

The brand lives in `davideimola/brand`: read its "Social cards" section in `docs/brand.md`. Social
images are **always light**: light ground, a tape with the content type, the title large, wordmark and
URL at the bottom. Slides need literal colours: take them from the brand's tokens, never from memory or
an old slide:

```sh
gh api repos/davideimola/brand/contents/dist/tokens.json -H "Accept: application/vnd.github.raw" | jq .color.palette
```

| Palette name | Usage |
|---|---|
| `paper` | Slide ground |
| `white` | Surface: callout and quote cards |
| `ink` | Titles, the tape, emphasis |
| `ink-body` | Body copy |
| `slate` | Meta: URL, slide counter, source lines |
| `rule` | Hairlines between items, card borders |
| `pencil` | The rule: one line opening a block or closing the header |
| `akane` | The knot (already inside the mark and wordmark files) and at most one marker stroke per slide. Nothing else |

Fonts: **Schibsted Grotesk** for titles and all running text (700 titles, 400 body, 600 emphasis);
**IBM Plex Mono** for meta only (URL, date, counter); **Barlow Condensed 700** for tape labels only,
always uppercase.

Every slide has three zones: the tape on top, the content in the middle, the wordmark and URL at the
bottom.

```html
<div class="w-full h-full relative overflow-hidden" style="background:<paper>;color:<ink>">
  <!-- optional, cover and closing slide only: the L mark as a tone-on-tone watermark,
       drawn in <rule> with the knot included, so the title stays the loudest thing -->
  <div class="relative z-10 w-full h-full flex flex-col justify-between p-16">
    <!-- TOP: one tape naming the content type (Writing, Talk, Project, Lesson 2...) -->
    <span style="display:inline-block;align-self:flex-start;background:<ink>;color:<paper>;font-family:'Barlow Condensed',sans-serif;font-weight:700;text-transform:uppercase;letter-spacing:0.12em;font-size:26px;line-height:1;padding:0.27em 0.67em;border-radius:3px;transform:rotate(-1deg)">Writing</span>
    <!-- MIDDLE: headline + body -->
    <div style="display:flex;flex-direction:column;gap:24px">
      <h2 style="font-family:'Schibsted Grotesk',sans-serif;font-size:80-96px;font-weight:700;letter-spacing:-0.045em;line-height:1.0;margin:0">Title</h2>
      <p style="font-family:'Schibsted Grotesk',sans-serif;font-size:28-30px;color:<ink-body>;line-height:1.5;margin:0">Body copy.</p>
    </div>
    <!-- BOTTOM: a <pencil> rule, then the wordmark left and the URL (or NN/total) right -->
    <div style="border-top:1px solid <pencil>;padding-top:24px;display:flex;justify-content:space-between;align-items:center">
      <img src="https://www.davideimola.dev/brand/wordmark.svg" alt="davide imola" style="height:40px">
      <p style="font-family:'IBM Plex Mono',monospace;font-size:20px;color:<slate>;margin:0">davideimola.dev/blog/post-slug</p>
    </div>
  </div>
</div>
```

A quote or callout card:

```html
<div style="background:<white>;border:1px solid <rule>;padding:2.5rem 3rem;width:100%;display:flex;gap:20px;align-items:flex-start">
  <span style="flex:none;width:14px;height:14px;background:<ink>;margin-top:18px"></span>
  <p style="font-family:'Schibsted Grotesk',sans-serif;font-size:38-44px;font-weight:600;letter-spacing:-0.02em;color:<ink>;line-height:1.3;margin:0">Quote text here.</p>
</div>
```

Rules:

- **The wordmark is a file, never typeset**: `wordmark.svg`, or `lockup.svg` / `mark-l.svg` for a logo
  block on the closing slide, by absolute URL (`https://www.davideimola.dev/brand/<file>`).
- **The red rule**: red is the knot and at most one marker stroke under the one word that matters on
  the slide. No red text, tapes, borders, labels, glows or backgrounds.
- **Tapes**: ink, flat, never red, one per slide, never stacked; alternate the tilt between
  neighbouring slides (`-1deg`, `1deg`, `-0.5deg`). The slide itself never rotates.
- **No terminal dressing**: no `❯`, no `//` prefixes, no window chrome, no dot grids, no glow.
- **Titles** 80-96px, wrapping over 2-3 lines is fine, never mid-word, no closing period unless it is
  a deliberate beat ("Manual."). **Body** 28-30px, 1-2 sentences.
- **Lists and steps**: items split by `rule` hairlines, the block opened by one `pencil` rule, numbers
  in Plex Mono `slate` (`01`, `02`).
- **Pivot slides** ("start over" moments): centred, the tape centred above.
- **Photos** of people are black and white (`filter:grayscale(1)`); the mark never sits on a photo.
- **English only, no em dashes**, on every slide.

## 5. Plan it in Typefully

Through the `typefully` MCP server, social set `97290`:

- `get_social_set_details` first: if `publishing_quota.remaining` is zero, say so and give me the post
  ready to paste instead.
- `create_draft` with **only** `platforms.linkedin` enabled; X and Bluesky never.
- `plan_at`: an exact date and time I approved. There are no queue slots, so never
  `"next-free-slot"`. Propose one: the note's `#linkedinDate` if it has one, otherwise Tuesday to
  Thursday around 8:30 Europe/Rome, never Friday, on a day with nothing else planned on LinkedIn.
  **Never** `publish_at`, **never** `confirm_publish`.
- `draft_title`: the topic in a few words. `scratchpad_text`: the source (post URL, note title).
- The image or carousel: attach it through the MCP's media upload if it offers one; otherwise give me
  the absolute path of the file to attach by hand.

If a call fails, say which, and give me the post ready to paste so nothing is lost.

## 6. Hand it back to Trilium

On the content note for this topic:

- `linkedin` missing from `#channels`: set `channels=linkedin` only if the note has no `#channels` at
  all; otherwise ask me to add the label by hand and tell me the exact `channels=linkedin`.
- `#artifact`: the draft's link, if `create_draft` returned one. If the note already has an
  `#artifact` (a blog topic usually has its PR there), add the link to a `## Artifact` list at the end
  of the body instead. Without a link, skip it: the post's URL in `#linkedin` will say it all.
- `#status=in-progress` if it was still `idea`. Nothing else.

Once I publish and give you the LinkedIn link, set `#linkedin` to it and `#linkedinDate` to the real
date. `#status=published` only when every channel in `#channels` has its URL.

With no content note (free text that matches no topic), ask in one line whether to create one. If yes,
capture it with the `idea` skill, `move_note` it to Contenuti (`l78292msrPRH`), set
`channels=linkedin`, ask me `flag` or `side` for `#flagSide`, and fill it as above. If no, the
Typefully draft is the deliverable.

Done when the draft is planned and the note is updated. Reply with the planned date and time, the
first words of the post, and a closing line reminding me it goes out only once I confirm it in
Typefully.

---

_Self-contained on purpose: installed from `davideimola/skills` and run from any repo. It lived in the
davideimola.dev repo until 2026-10-30, when Typefully became the home of the copy and nothing was left
to commit there; the posts written before then stay in that repo's `.carousel/`._
