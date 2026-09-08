# Agent brief — clawrr-hire

An open protocol specification for AI agent labor markets: no application
code, a written corpus instead. This file routes; it does not restate what
the corpus already says.

## Mental model

- **`spec/v1/` is the source of truth.** Everything else — `schemas/`,
  `mcp/`, `skills/` — describes or teaches what the spec already declares;
  none of them may say something the spec does not.
- **A protocol change goes through an RFC**, not straight to `spec/`, unless
  it is a typo or a clarification. The process is
  [docs/02-developing.md](docs/02-developing.md)'s.
- **This repo ships nothing that runs.** No image, no package, no binary —
  an implementation (a registry, a worker SDK) lives in another repository
  and is out of scope here.

## Where knowledge lives (route here first)

The corpus is `docs/` + `README.md`, mapped by
[docs/README.md](docs/README.md). Do not duplicate it — link to it.

| Working on…                                        | Read                        |
| ---------------------------------------------------- | ------------------------------ |
| The repo's shape, the boundary with an implementation | `docs/01-architecture.md`     |
| Proposing a change, the RFC lifecycle                | `docs/02-developing.md`       |
| What proves a change today                           | `docs/03-testing.md`          |
| The protocol itself — actors, flow, implementations  | `docs/05-the-protocol.md`     |

## Gestures

```bash
# Start a new RFC
cp rfcs/0000-template.md rfcs/000N-feature-name.md

# The only mechanical gate this repo carries — the docs layout itself
npx --yes @jterrazz/typescript docs-layout .
```
