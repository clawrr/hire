# Testing

What proves a change to this repository, stated honestly: today nothing
mechanical proves one.

There is no `package.json`, no test runner, and no script that validates
`spec/v1/*.md` against `schemas/v1/*.json` — a change that names a field in
the spec and forgets to add it to the matching schema, or the reverse, is
caught by a reviewer reading both, not by a gate. The `docs-layout` check
(`npx --yes @jterrazz/typescript docs-layout .`) is the one mechanical proof
this repository carries, and it holds the shape of `docs/` alone: the map is
bijective with the chapters, the spine is in place, `decisions/` follows its
own mold. It says nothing about the protocol itself.

A reviewer proves a change by hand, against three questions:

- Does every JSON example in the changed `spec/v1/*.md` document validate
  against the schema it claims to follow (`schemas/v1/*.json`)?
- Does `mcp/README.md` still describe every tool the spec now implies, and
  no tool the spec no longer does?
- Does `skills/hire/SKILL.md` still teach an agent to do what the changed
  spec now says?

Nothing here is invented as a suite that runs: it is the checklist a human
reviewer holds until one exists.
