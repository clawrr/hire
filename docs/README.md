# clawrr-hire — the corpus

The manual of this repository: what the HIRE protocol is, how a change to it
is proposed, and what proves one. The protocol text itself is `spec/v1/`; the
vitrine is the root `README.md`.

| Chapter                                    | Holds                                                                                            |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [01-architecture.md](01-architecture.md)   | The shape of the repo: what each folder holds, the boundary with the implementations it specifies for |
| [02-developing.md](02-developing.md)       | How a change is made: the RFC process, where a change lands, the review norm                       |
| [03-testing.md](03-testing.md)             | What proves a change today, honestly — and what does not yet exist to prove one                     |
| [05-the-protocol.md](05-the-protocol.md)   | The protocol itself: the actors, the design principles, the flow, and who implements it             |

`04-operating.md` is absent on purpose: this repository ships nothing that
runs — no image, no package, no binary — so the spine's fourth position has
nothing to hold.

The decisions this repository took alone stand in [decisions/](decisions/),
numbered and chronological, the mold `_template.md` beside them. A decision
that spans several repositories of the `clawrr` brand belongs to
`home/clawrr/wiki/`, not here.

A map routes to its own chapters and nowhere else: the route into this
repository is this page, and the route out of it is the corpus that owns the
subject.
