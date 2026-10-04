# Block Diagramming Conventions

How to draw a system so that someone else can read it without you standing next to
them explaining it.

There is no universal standard for block diagrams. What follows is the convention
used in this repository. Consistency matters more than which convention you pick —
but pick one and hold it.

---

## The minimum viable diagram

A block diagram that works has four things. Miss any one and readers start guessing.

1. **A boundary** — a line showing what is inside the system and what is outside.
2. **Blocks** — named after responsibilities, at one consistent level of zoom.
3. **Arrows with labels** — every arrow says what travels along it.
4. **A legend** — what your line styles mean.

If you have those four, the diagram is readable. Everything below is refinement.

---

## Blocks

**Name a block after what it is responsible for, not what it is made of.**

| Instead of | Write |
|---|---|
| `Arduino Nano` | `Wheel Speed Sensing` |
| `PostgreSQL` | `Trip History Store` |
| `Jetson Nano` | `Perception Processing` |

Why this matters more than it sounds: `Arduino Nano` locks in a component before you
have decided you need it. `Wheel Speed Sensing` describes a job that still has to be
done whatever you put there, which leaves the choice available — and makes it a
*choice*, which means it can appear in your trade-offs.

Rules:

- **One responsibility per block.** If describing it needs "and" twice, it is two
  blocks.
- **One level of zoom per diagram.** A diagram containing both `Powertrain` and
  `M3 bolt` is mixing levels, and the reader cannot tell what scale they are looking
  at.
- **Consistent names.** The same block called two different things in two places is a
  real and frequent defect. It also silently breaks any search.

---

## Arrows: the four flow types

The core convention here. Four kinds of flow, visually distinct, because they are
genuinely different things and a reader needs to tell them apart at a glance.

| Flow | Line style | Carries |
|---|---|---|
| **Data / signal** | Solid, thin | Measurements, messages, readings |
| **Power** | Thick, or double line | Electrical energy |
| **Control** | Dashed | Commands, decisions, enable/disable |
| **Mechanical** | Solid, heavy, or distinct colour | Force, torque, motion, physical attachment |

Pick styles that survive being printed in black and white. Colour alone is not a
distinction — it fails on a projector, a photocopy, and for colour-blind readers.

**Every arrow gets a label.** The label states what travels, and where a quantity is
involved, its rate and units:

```
Wheel Speed Sensing  --[ wheel RPM, 50 Hz, integer ]-->  Speed Estimation
Battery              ==[ 12 V DC, 4 A max ]==>           Sensor Bus
Control Unit         --[ engine cut command ]-->         Ignition Relay
```

An unlabelled arrow means one of two things: you know what travels and did not write
it, or you do not know. The second is a hole in the design, and leaving the arrow
unlabelled is how it stays hidden.

---

## The boundary

Draw it. A dashed rectangle around everything you are designing.

Things outside go beyond the line: the driver, the pit laptop, the weather, the
ground, a part you are buying rather than building.

Why it is first and not cosmetic: without a boundary, "the system" quietly expands
until it means everything, and then nothing can be specified. It is also the thing
that makes an interface definable at all — an interface is a thing that crosses the
boundary, so no boundary means no interfaces.

---

## Levels of zoom

| Level | Shows | Typical block count |
|---|---|---|
| **Context** | Your system as one box, plus everything it talks to | 1 + 3–6 external |
| **HLD** | The major blocks inside, and what passes between them | 5–9 |
| **LLD** | One HLD block, opened up | 5–9 |

**Five to nine blocks per diagram.** Fewer than five and you probably have not
decomposed anything. More than nine and the reader cannot hold it — split it, and
make the overflow an LLD of one block.

An LLD **states which HLD block it expands**, in its first line. Without that, a
reader cannot locate it in the system. See [HLD vs LLD](hld-vs-lld.md).

---

## The legend

Bottom-left corner, every diagram, no exceptions. **Copy this into your Draw.io
canvas as a text box:**

```
LEGEND
──────  data / signal
══════  power
┄┄┄┄┄┄  control
▰▰▰▰▰▰  mechanical
┌ ─ ┐   system boundary
└ ─ ┘
```

It takes thirty seconds and it is the difference between a diagram that stands alone
and a diagram that needs you present to interpret it. You will not be present when it
matters.

---

## File format

**Save as `.drawio.svg`** — "Editable SVG" in Draw.io.

One file that renders inline on GitHub and still opens as an editable diagram. No
separate source and export, so no chance of them drifting apart and nobody knowing
which is current.

Naming:

```
<system-slug>-<level>[-<subject>].drawio.svg

atv-telemetry-context.drawio.svg
atv-telemetry-hld.drawio.svg
atv-telemetry-lld-sensor-node.drawio.svg
```

Diagrams live in a `diagrams/` folder next to the document that explains them. Not in
a global image folder. See [CONVENTIONS.md](../CONVENTIONS.md#diagrams).

---

## Checklist before you call it done

- [ ] Boundary drawn, inside and outside visible
- [ ] Every block named after a responsibility, not a technology
- [ ] Every block at the same level of zoom
- [ ] 5–9 blocks
- [ ] Every arrow labelled with what travels, plus rate and units
- [ ] Four flow types visually distinct, and distinguishable in black and white
- [ ] Legend present
- [ ] No block with outputs nothing consumes, or inputs nothing produces
- [ ] Power traced to every consumer
- [ ] Names consistent throughout
- [ ] Readable at the size it will actually be viewed
- [ ] Saved as `.drawio.svg`

Then run **[the review prompt](../07-workshop/ai-prompts/review-my-design.md)** on it.

---

## What a block diagram is not

Three things get drawn as block diagrams by mistake, and each produces something that
looks like a system design but answers a different question:

- **An org chart.** Boxes are responsibilities of the system, not of people.
- **A build sequence.** Arrows mean "this travels to that", not "do this next".
- **A flowchart.** Blocks are parts that exist simultaneously, not steps that happen
  in order. If your arrows mean "then", you have drawn a process, not a system.

A quick test: in a block diagram, every box exists at the same time and keeps
existing. If a box is finished and gone by the time the next one starts, it is not a
block.
