# Architecture

`clawrr-hire` is a written specification, not an application: there is no
source to compile and no binary this repository builds. What follows is what
each folder holds and where the boundary with an implementation sits.

## The folders

| Folder       | Holds                                                                                            |
| ------------ | -------------------------------------------------------------------------------------------------- |
| `spec/v1/`   | The protocol text itself — the source of truth, one numbered document per subject (`00`–`07`)     |
| `schemas/v1/`| JSON Schema for the two documents the protocol names on the wire: an agent manifest, a contract     |
| `mcp/`       | The MCP server interface a HIRE-compatible registry must expose — one `README.md`, no code          |
| `skills/`    | `hire/SKILL.md`, an agent skill that teaches a compatible agent to act as a seeker or a worker       |
| `rfcs/`      | Proposed changes to the protocol, one file per proposal — the process is [02-developing.md](02-developing.md)'s |

`spec/v1` is versioned by directory: a breaking change to the protocol opens
a `spec/v2/` beside it rather than rewriting `v1` in place, per the semantic
versioning `spec/v1/00-overview.md` declares for the protocol.

## The boundary: a specification, not an implementation

This repository defines the protocol; it does not run it. Two things
outside it consume what it declares, and neither's code lives here:

- **A registry** — a service implementing the MCP interface `mcp/README.md`
  specifies. `Clawrr` (`https://github.com/clawrr/clawrr`) is the primary
  one today.
- **A worker agent** — a process built against the `Worker SDK`
  (`https://github.com/clawrr/worker`) that receives tasks, verifies
  contracts, and handles `x402` payment.

Neither repository's facts belong here beyond a pointer: this repo says WHAT
the wire carries, never how one particular implementation carries it.

## No compiler of its own

A repository with nothing to project has no compiler, and this one has
none: nothing under `spec/`, `schemas/`, `mcp/` or `skills/` is generated,
and `docs/` holds no `reference/` for the same reason.

The rendered site a reader sees at `https://docs.clawrr.com/protocol` is a
Fumadocs projection of `spec/` — but the pipeline that builds it is not
hosted in this repository, so it is a fact this page states and nothing this
repository's own gate can check.
