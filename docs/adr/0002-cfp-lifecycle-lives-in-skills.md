# The CFP lifecycle lives in this repo, not in presentations

Finding a Call, pitching a Talk to it and answering its form are one `cfp` skill in this repo, with its state in Trilium: the Talk's note holds the Abstract, the Proposta and the CFP lines, and the answers sent go into a child note `CFP <Conference Year>`. A Talk is submitted before anyone develops it (its Brief and slides only follow an accepted CFP), so the submit step needs nothing from `presentations`; keeping it there tied it to a `TALK.md` that does not exist yet at submit time. `presentations` keeps only the development of an accepted Talk: `talk-forge` and `slide-craft`.

## Considered Options

- **Scout here, `cfp-submit` left in `presentations`**: two skills for one path, and `cfp-submit` required a Brief that only exists after acceptance.
- **Answers as local gitignored files** (`presentations/<slug>/cfp/`): private, but unreadable from the phone and invisible when the same Talk is submitted again; in a Trilium child note they are the starting point for the next submission.

## Consequences

- Supersedes the CFP part of ADR-0002 in `davideimola/presentations` ("calibrated answers stay local, never in Trilium"); `cfp-submit` there is retired.
