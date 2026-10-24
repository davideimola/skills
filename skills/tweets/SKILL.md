---
name: tweets
description: Propose a few short posts for Davide's X + Bluesky queue from what he already makes (Trilium ideas, blog posts, Argus activity, upcoming talks), then save the approved ones as planned drafts in Typefully. Use when Davide wants tweets, short posts, or to fill the queue ("proponimi dei tweet", "riempi la coda", "/tweets"), from any repo.
---

# tweets — the queue lane

Davide runs two lanes on X:

- **The queue** (this skill): 2-3 short posts a week, drafted from material he already has, planned in
  Typefully and mirrored to Bluesky. It keeps the profile alive in the weeks he has no time.
- **The live lane** (not this skill): conferences, people he meets, reactions, replies. At a Conference
  the `conference` skill proposes them from his Takeaways; the rest he writes himself. Leave them out of
  the queue.

Your job: find the material, propose posts in his voice, and save the ones he approves as **planned**
drafts. You never publish and never schedule. He confirms each post in Typefully himself.

## 1. Check the queue

Through the `typefully` MCP server, social set `97290` (X `@DavideImola`, Bluesky `davideimola.dev`,
LinkedIn also connected but **never used here**: LinkedIn goes through the `social-post` skill in the
davideimola.dev repo).

- `get_social_set_details`: read `publishing_quota`. If `remaining` is lower than what you are about to
  propose, say so up front.
- `get_queue` for the next 14 days and `list_drafts` with `status: "published"` (last 10): know which
  slots are free and which topics went out recently, so you do not repeat one.

## 2. Gather material

Only from what exists. Never invent an event, a number, or an opinion Davide has not expressed.

- **Trilium** (`trilium` MCP): the Inbox `oI6dJqP0hGHG` (sparks, `#status=idea`) and the Contenuti
  collection `l78292msrPRH` (notes `#status=in-progress` or recently `published`). Read only: never
  change an attribute or a note from this skill.
- **Blog**: `https://davideimola.dev/rss.xml`, the latest 2-3 posts. A post gives one line worth
  lifting, not a promo.
- **Argus** (`gh` on `argusappsec/argus`): commits, merged PRs and releases of the last two weeks. This
  is the richest seam: Davide's audience is the Go community and the Italian tech scene, his
  positioning is AI agents for security, and Argus is an AI security agent written in Go. A design
  choice, a Go library that helped or hurt, an LLM behaviour seen from the integration side.
- **Talks**: `https://davideimola.dev/sharing`, the upcoming ones.

## 3. Propose

Present 4-5 candidates in chat. For each: the post text, the source in one line, and your honest take
on whether it is strong. Lead with your favourite. Mix the shapes: a build note from Argus, an opinion,
a real question to the community (the shape that got the most replies on his Bluesky), a line lifted
from a post, a talk announcement when one is close.

Rules for the text:

- **English.** Read the **Voice** section of the brand guidelines first:
  `node_modules/@davideimola/brand/docs/brand.md` when you are in the davideimola.dev repo, otherwise
  `gh api repos/davideimola/brand/contents/docs/brand.md -H "Accept: application/vnd.github.raw"`.
- **Fits one post**: at most 280 characters on X, 300 on Bluesky. Prefer one post to a thread.
- **No link in the post itself.** The post carries the value on its own; when there is a link, it goes
  in a second post of the thread (`posts[1]`), which reads as the reply under it.
- **No em dashes.** First person, specific, never a press release. No hashtags beyond one if it truly
  helps, no emoji walls, no "🧵".
- **Mentions**: X handles do not exist on Bluesky. When a post mentions someone, write the Bluesky
  version with their Bluesky handle or their name, and show both versions.

Iterate until Davide approves. Push back when a change weakens a post.

## 4. Save as planned drafts

For each approved post, `create_draft` on social set `97290`:

- `platforms.x` and `platforms.bluesky` enabled with their posts; `linkedin` never.
- `plan_at: "next-free-slot"`. **Never** `publish_at`, **never** `confirm_publish`: a planned draft sits
  in the calendar and does nothing until Davide confirms it in Typefully.
- `draft_title`: a few words naming the topic.
- `scratchpad_text`: the source (note title, post URL, PR link), so he can check it while reviewing.

Done when every approved post exists as a planned draft. Reply with one line per draft (date of its
slot and the first words), then a closing line reminding him the drafts publish only once he confirms
them in Typefully. If a call fails, say which, and give him the text so nothing is lost.

---

_Self-contained on purpose: installed from `davideimola/skills` and run from any repo. Decided on
2026-10-24: X is home, Bluesky is the mirror (its Italian audience went back to X; the people who are
only on Bluesky, like Filippo Valsorda, still see the queue). The queue slots are set in Typefully's own
settings, not here._
