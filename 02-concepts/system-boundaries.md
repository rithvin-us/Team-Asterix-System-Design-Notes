# System Boundaries

> **Status:** stub

What is inside the system, what is outside, and why nothing else can be specified
until this is settled.

Almost every confused design is a boundary problem wearing a different costume.

## To write up here

- Why boundary precedes interfaces: an interface is a thing that crosses a boundary
- Three categories: inside, outside-but-connected, irrelevant
- Stating what the system deliberately does *not* do
- External dependencies: power source, operator, network, ground, weather, other vehicles
- Boundary creep, how "the system" quietly grows to mean everything
- Choosing where to draw it, and the consequence of each choice

## Guiding questions

- What are you designing, versus what are you merely using?
- Name two things this system deliberately does not do.
- What does it depend on already existing?
- Pick any element: can a reader tell which side of the line it is on?

## See also

- [Move 1. Decompose](../01-method/1-decompose.md)
- [Block diagramming conventions](block-diagramming-conventions.md)
