# Glossary

Terms as used in **this** repository. System design has no universal vocabulary —
several of these mean different things elsewhere, so where that is likely, it is
noted.

> **Status:** growing. Add a term the moment you notice it being used ambiguously.

---

**Assumption** — Something believed to be true but not verified. Must be stated
separately from facts. An unstated assumption is indistinguishable from a mistake.

**Block** — A part of a system with one stated responsibility. Named after what it is
responsible for, not what it is made of.

**Block diagram** — A drawing of a system as blocks and the labelled things that pass
between them. Not a flowchart: blocks exist simultaneously, they are not steps.

**Boundary** — The line between what you are designing and what you are merely using.
Must be drawn before interfaces can be defined, because an interface is by definition
something that crosses it.

**Canonical** — Written or rewritten deliberately, and stood behind. Everything
outside [`99-inbox/`](99-inbox/).

**Case study** — A whole system traced end to end through all five moves. Contrast
with *example*.

**Constraint** — Something that limits you: budget, available parts, rules, deadline,
skills, weight, space. A design input, not an excuse.

**Context diagram** — The system as a single box plus everything it talks to. The
widest zoom level.

**Control flow** — Commands and decisions. Who decides, and how the decision reaches
the thing that carries it out. Distinct from data flow: a measurement is not a
command. *(Note: in programming, "control flow" means branching within a program.
Here it means command paths through a system.)*

**Data flow** — Measurements, messages and readings moving through the system.

**Decompose** — Cut a system into blocks. [Move 1](01-method/1-decompose.md).

**Example** — A short illustration of a single point. Contrast with *case study*.

**Exercise** — A practice task completable in one sitting. Contrast with *project*.

**Flow** — A path through the system, traced end to end — not a single hop. Four
kinds: data, power, control, mechanical.

**Functional requirement** — What the system must do.

**HLD** — High-Level Design. The major blocks inside the boundary and what passes
between them. 5–9 blocks.

**Interface** — What crosses between two blocks, fully specified: what it is, its
form, its rate, its units, its direction. "Data" is not an interface specification.

**LLD** — Low-Level Design. One HLD block opened up. Must state which HLD block it
expands.

**Mechanical flow** — Force, torque, motion, and physical attachment. What is bolted
to what, and where loads go.

**Move** — One of the five steps of the method:
[decompose](01-method/1-decompose.md),
[interfaces](01-method/2-interfaces.md),
[flows](01-method/3-flows.md),
[constraints](01-method/4-constraints.md),
[trade-offs](01-method/5-tradeoffs.md).

**Non-functional requirement** — How well the system must do something. Must have a
number. "Fast" is not one; "under 100 ms" is.

**Power flow** — Electrical energy from source to every consumer. The most frequently
forgotten of the four flows.

**Project** — Substantial open-ended work with a full design record. Contrast with
*exercise*.

**Raw** — Unverified machine-generated material. Lives only in
[`99-inbox/notebooklm-raw/`](99-inbox/notebooklm-raw/) and never gets promoted
without being rewritten.

**Responsibility** — What a block is for, statable in one sentence without using
"and" twice.

**Stub** — A page whose structure exists but whose prose does not. Marked
`> **Status:** stub`.

**Trade-off** — A decision with a named rejected alternative and a named cost. A
choice with neither was a default, not a decision.

**Zoom level** — How detailed a diagram is. Context, HLD, LLD. Mixing levels in one
diagram makes it unreadable, because the reader cannot tell what scale they are
looking at.
