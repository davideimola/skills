# skills

The Agent Skills I use every day to run my writing, outside any single repo. They are wired to my own
setup (my Trilium notes, my Typefully queue, my voice), so they will not work for you as they are.
They are here as examples of how I work with Claude: read them, take what fits, and change the IDs and
the voice to yours.

For skills meant to be installed as they are, see
[go-security-skills](https://github.com/davideimola/go-security-skills).

## Skills

| Skill | What it does |
|---|---|
| [`idea`](skills/idea/) | Captures a content spark into my Trilium Inbox as an idea note, verbatim, from any repo. Capture first, judge later. |
| [`tweets`](skills/tweets/) | Proposes a few short posts from what I already make (Trilium ideas, blog posts, my open source work, upcoming talks) and saves the ones I approve as planned drafts in Typefully, for X and Bluesky. It never publishes. |
| [`social-post`](skills/social-post/) | Writes a LinkedIn post for something I made, in my voice: a real taste of a blog post that points home, or a self-contained post for a talk or an event. Builds a branded image when one helps and saves the post as a planned draft in Typefully. It never publishes. |
| [`conference`](skills/conference/) | My companion at a conference, all in one Trilium note: an Agenda of the sessions worth my time, takeaways caught from my phone (with a post when one is worth sharing, published only on my yes), and a recap with follow-ups. |
| [`cfp`](skills/cfp/) | Scouts open conference Calls for papers every two weeks (eventitech, developers.events and my own watchlist), matches each to one of my talks or a new idea, shapes a new talk into an abstract and a proposal, pressure-checks my answers to the form, and tracks each submission's outcome in Trilium. I send the form myself. |

They expect MCP servers: [Trilium](https://github.com/TriliumNext/Trilium) for all of them,
[Typefully](https://typefully.com) for `tweets`, `social-post` and `conference`. `social-post` also
builds its images with [mkcr](https://github.com/ludusrusso/mkcr).

## Install

With the [`skills`](https://github.com/vercel-labs/skills) CLI:

```sh
npx skills add davideimola/skills
```

Or copy a single folder from [`skills/`](skills/) into your agent's skills folder.

## No secrets

Nothing in this repo is a credential: both MCP servers authenticate on their own, and the IDs in the
skills mean nothing without my accounts. CI runs gitleaks on every push to keep it that way.

## License

[MIT](LICENSE)
