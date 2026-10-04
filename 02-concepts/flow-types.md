# Flow Types

> **Status:** stub

Four kinds of flow. Genuinely different things, routinely drawn with the same arrow.

| Flow | Carries | What usually goes wrong |
|---|---|---|
| **Data / signal** | Measurements, messages, readings | Drawn, but untyped |
| **Power** | Electrical energy | Forgotten entirely |
| **Control** | Commands, decisions, enables | Conflated with data |
| **Mechanical / physical** | Force, torque, motion, attachment | Omitted in software-minded designs |

## To write up here

- Data vs control: a measurement is not a command, and conflating them hides who decides
- Power flow and power budgeting; the diagram where nothing supplies the compute
- Mechanical load paths, what is bolted to what, and where force goes
- Visual conventions that survive black and white and colour-blindness
- Software-only systems: declaring power and mechanical out of scope rather than silently omitting them
- Tracing a flow end to end out loud, as a review technique
- Rate and latency accumulating along a path

## Guiding questions

- Which of the four does each arrow in your diagram carry?
- Does anything draw power with no supply path?
- Can a reader tell, from your diagram alone, who decides?

## See also

- [Move 3. Flows](../01-method/3-flows.md)
- [Block diagramming conventions](block-diagramming-conventions.md)
