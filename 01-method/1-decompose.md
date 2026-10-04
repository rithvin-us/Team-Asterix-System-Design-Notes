# Move 1. Decompose

> **Status:** stub

**The question:** what are the parts?

## What this move is

Cutting the system into blocks, each with one responsibility you can state in a
sentence without using "and" twice.

The cut is a decision, not a discovery. Several valid cuts exist for any system and
they are not equally good. A bad cut puts boundaries in places where many things have
to cross them, which makes every later move harder.

## To write up here

- Why a cut can be good or bad, with a worked contrast of two cuts of the same system
- The "one responsibility, no double-and" test and where it breaks down
- Consistent zoom: why mixing levels destroys readability
- How to tell a real block from a box that exists because you had nowhere else to put something
- Functional vs physical vs domain-based decomposition, and when each is right

## Guiding questions

- What are the major parts inside the boundary?
- State each one's responsibility in one sentence. Does any need "and" twice?
- Are all these at the same level of detail?
- Why this split and not another? What would the alternative cut be?
- Is any box here only because you had nowhere else to put something?

## See also

- [Move 2. Interfaces](2-interfaces.md)
- [System boundaries](../02-concepts/system-boundaries.md)
