# How to Draw a System You Have Read About

Reading an architecture teaches you very little. **Drawing it** teaches you a lot,
because the moment you try to draw something you did not understand, you find you
cannot.

This is a six-pass method. Use it on any system in the
[reference list](reference-architectures.md). It takes about an hour.

> **The rule that makes it work:** do not look at their diagram while you draw. Read
> their *words*, draw from understanding, and only then compare. If you copy their
> picture you will learn the picture, not the system.

---

## Before you start

Open the [starter template](../02-concepts/diagrams/starter-template.drawio.svg) and
have the source open in another tab. Keep a scrap page for things you cannot answer —
that list is the valuable output.

---

## Pass 1 — Find the boundary (10 min)

Read the overview once, looking for one thing only: **what is this software or system,
and what is it not?**

Write two lists. Do not draw yet.

- **Inside:** what the authors built.
- **Outside:** what they use, assume, or hand off to.

Then hunt for the hardest thing to find: **what they deliberately excluded**. Search
the page for "future work", "out of scope", "not currently", "planned", "limitations".

In Autoware this is explicit — fail-safe, HMI, real-time, redundancy and state
monitoring were all deferred, and they say so. Most sources are less honest, and the
exclusions have to be inferred from what is simply never mentioned.

**Output:** two lists and a third headed *not doing*.

---

## Pass 2 — Name the blocks (10 min)

List the major components **by name, exactly as the source names them**. Using their
vocabulary matters: it makes your diagram checkable against the source, and it stops
you quietly renaming something into a thing you understand better than they meant.

Next to each, write its responsibility **in one sentence with no second "and"**.

If you cannot write that sentence, you have found a gap. Write the block name on your
scrap page and move on — do not invent a responsibility.

**Output:** a two-column list — name, responsibility.

---

## Pass 3 — Draw boxes only (10 min)

Now open the template. Place the blocks. **No arrows yet.**

- Keep everything at the same level of zoom. If one box is a whole subsystem and
  another is a function, split the diagram.
- Aim for 5–9 boxes. More than nine means you are drawing two diagrams at once.
- Put the boundary around what is inside, and leave external things outside it.

Arrange so that the thing that starts the work is on one side and the thing that acts
on the world is on the other. Most systems read left to right; some read outward from
a centre. Try both and keep the one with fewer crossing lines.

**Output:** a diagram with no arrows. It should already look like something.

---

## Pass 4 — Add arrows, and label every one (20 min)

This is the pass that teaches. For each connection ask: **what exactly travels here?**

Label with content, and with rate and units wherever a quantity is involved:

```
Sensing  --[ point cloud, 10 Hz ]-->  Perception
Steering service  --[ list of OCA URLs ]-->  client
Battery  ==[ 12 V, 4 A max ]==>  sensor bus
```

Rules:

- **Separate the flow types.** Data, power, control, mechanical. If the system is
  software only, write that on the diagram rather than silently omitting the other
  three.
- **If you cannot label an arrow, do not draw it.** Put it on the scrap page instead.
  An unlabelled arrow is a guess that will look like knowledge in a week.
- Watch for a block everything points at. That is either the most important thing in
  the system or a box hiding three blocks inside it.

By the end you will have found things the source never said. **That is the point.**

---

## Pass 5 — Trace one flow end to end (10 min)

Pick one thing and follow it the whole way, out loud, without skipping:

> "LiDAR produces a point cloud. Sensing pre-processes it. Localization fuses it with
> GNSS and IMU to estimate pose. Planning takes that pose and the map and produces a
> trajectory. Control turns the trajectory into a steering angle. Vehicle Interface
> turns that into a CAN message."

Where you say "and then it somehow…" — stop. That is a gap. Scrap page.

Then trace a **second** flow of a different type. If it is a physical system, trace
power: start at the source, reach every consumer. In a software system, trace control:
who decides, and how does the decision arrive?

**Output:** two traced paths and a longer scrap page.

---

## Pass 6 — Compare, then score (10 min)

**Now** open their diagram.

Do not look for what you got wrong. Look for **differences**, and for each one ask
which of these it is:

| Difference | What it means |
|---|---|
| They have a box you do not | You missed it, or they expose something you folded in |
| You have a box they do not | You split something they treat as atomic — why? |
| They group differently | Their grouping encodes something. What? |
| They show a flow you did not | Usually the one you could not label |

The differences are the lesson. A diagram identical to theirs means you copied; a
diagram with *explicable* differences means you understood.

Finally, score your diagram with the **[HLD Scorecard](https://claude.ai/artifact/2tr1jH6Zyyt6LCDXTPfsGR)** —
upload the `.drawio` file and it counts your blocks and labelled arrows for you.
Score it honestly — it is your own diagram of someone else's system, and nobody is
marking it. The number that matters is the weakest dimension, not the total.

---

## Write it up

Fill in [the case study template](case-study-template.md). Four sections carry the
value:

1. **Boundary**, including what they excluded.
2. **Why this cut** — their stated reasons if they gave any, your inference if not,
   clearly marked as inference.
3. **Trade-offs** — the decision, the rejected option, the cost.
4. **What they do not tell you** — your scrap page, cleaned up.

Section 4 is the one most people skip and the one most worth having. A list of honest
unknowns is a more useful artifact than a confident summary, and it is the part a
reviewer will trust you for.

---

## Worked examples

Two case studies in this repository were produced with exactly this method:

- **[Autoware](autoware/autoware.md)** — a vehicle stack, including its architecture
  rewrite and why it happened
- **[Netflix](netflix-streaming/netflix-streaming.md)** — control plane and data plane
  as genuinely separate systems

Read one *after* you have attempted your own. Reading it first turns the exercise into
copying.

---

## Common sticking points

| Stuck | What it means |
|---|---|
| "Everything connects to everything" | You are at the wrong zoom. Go up a level. |
| "I can't tell what's inside or outside" | Read for who maintains what. Boundaries follow ownership. |
| "There are 20 components" | They documented an LLD. Group into 5–9 and note the detail for later. |
| "I can't label most arrows" | Normal on a first pass. The source genuinely does not say. That *is* your finding. |
| "My diagram looks nothing like theirs" | Good, if you can explain each difference. Bad, if you cannot. |
