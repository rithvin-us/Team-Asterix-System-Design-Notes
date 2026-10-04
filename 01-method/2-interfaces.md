# Move 2. Interfaces

> **Status:** stub

**The question:** what crosses between the parts?

## What this move is

For every block: what goes in, what comes out, and exactly what those things are.

Not "data", *which* data, in what form, how often, in what units, how much.

This is the highest-value move of the five and where beginner designs are weakest.
The sharpest test in system design: pick any arrow and say what travels along it. No
answer means that arrow is decoration standing where a decision should be.

## To write up here

- What a fully specified interface contains: content, form, rate, units, range, direction
- Why "data" is not a type
- Physical interfaces: voltage, current, connector, pinout, mounting, torque
- Logical interfaces: message shape, call contract, error cases
- Why an interface is only definable once a boundary exists
- Orphan detection: outputs nobody consumes, inputs nobody produces
- Interfaces as the thing that lets two people work in parallel

## Guiding questions

- What exactly enters this block? What exactly leaves?
- For each: what is it, in what form, how often, in what units, how much?
- Are units stated everywhere a quantity appears?
- Any output nothing consumes? Any input nothing produces?
- Could someone build the block on the other side of this interface from your
  description alone, without asking you anything?

## See also

- [Move 3. Flows](3-flows.md)
- [Block diagramming conventions](../02-concepts/block-diagramming-conventions.md)
