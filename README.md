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

Both expect MCP servers: [Trilium](https://github.com/TriliumNext/Trilium) for `idea` and `tweets`,
[Typefully](https://typefully.com) for `tweets`.

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
