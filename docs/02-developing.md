# Developing

How a change to the HIRE protocol is made: when it needs an RFC, the RFC's
own lifecycle, and where a change lands once it is agreed. What the
repository IS is [01-architecture.md](01-architecture.md); what proves a
change is [03-testing.md](03-testing.md).

## When an RFC is needed

A minor typo fix or a clarification is a regular pull request. Everything
else against the protocol goes through an RFC first:

- Adding a new protocol feature
- Changing existing behaviour
- Deprecating functionality
- A significant clarification

## The RFC lifecycle

1. **Draft** — copy `rfcs/0000-template.md` into a new file, numbered
   sequentially (`0001-feature-name.md`), and fill in its Summary,
   Motivation, Detailed Design, Drawbacks, Alternatives and Unresolved
   Questions.
2. **Discussion** — open a pull request carrying the file; gather feedback
   on it.
3. **Revision** — update the RFC from that feedback.
4. **Accepted** — merged into `main`; the spec it changes is updated in the
   same unit of change.
5. **Implemented** — the change is reflected in a consuming implementation
   (a registry, a worker SDK), outside this repository.

## Where a change lands

| A change to…                                     | Lands in                                              |
| -------------------------------------------------- | -------------------------------------------------------- |
| The protocol's rules for one subject               | `spec/v1/NN-subject.md` — the numbered document that owns it |
| A wire shape the protocol names (manifest, contract)| `schemas/v1/*.json`, in lockstep with the spec document that describes it |
| What a registry's MCP server must expose           | `mcp/README.md`                                        |
| What an agent skill teaches about participating    | `skills/hire/SKILL.md`                                  |

A change that reaches more than one of these lands them together, in the
same commit: a spec change without its schema, or a schema without the spec
sentence that names it, is a wire shape nobody can read back.

## Review norm

Discussion on an RFC or a pull request stays on technical merit, argued in
good faith.
