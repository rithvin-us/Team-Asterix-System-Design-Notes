# Move 3 — Flows

> **Status:** stub

**The question:** does it work end to end?

## What this move is

Following one thing all the way through the system. Not one hop — the whole path.

Four kinds, genuinely different, routinely drawn with the same arrow by people who
have not been told to separate them.

| Flow | The question |
|---|---|
| **Data / signal** | Where does a measurement go, from sensing to being acted on? |
| **Power** | Where does energy come from, and does every consumer have a supply path? |
| **Control** | Who decides, and how does a command reach the thing that carries it out? |
| **Mechanical / physical** | What is attached to what? Where do loads and motion go? |

## To write up here

- Why a flow is a path and not a hop, and why one-hop thinking hides most defects
- Data vs control: measurement and command are not the same arrow
- Power: why it is the most-forgotten flow, and power budgeting
- Mechanical flow: load paths, what is fixed to what
- Latency and rate accumulating along a data path
- Software-only systems: stating that power and mechanical do not apply, rather than silently omitting
- Walking a flow out loud as a review technique

## Guiding questions

- Pick one measurement. Trace it from sensing to action. Every hop. Any gaps?
- Does anything draw power with no supply path drawn?
- Who decides? Trace one command from decision to actuator.
- What happens if that decision is late, or wrong?
- Are the four flow types visually distinguishable in your diagram?

## See also

- [Move 4 — Constraints](4-constraints.md)
- [Block diagramming conventions](../02-concepts/block-diagramming-conventions.md)
