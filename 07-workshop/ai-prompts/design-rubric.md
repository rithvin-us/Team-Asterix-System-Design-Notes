# The System Design Rubric

This is the single checklist that everything else in this repo is measured against.

- The **review prompt** reads this rubric and audits your design against it.
- The **design prompt** walks you through producing something that satisfies it.
- Your **mini project** is graded against it.
- You can use it on your own, with no AI at all, as a pre-submission self-check.

A design that passes every item below is not necessarily *good*. But a design that
fails items here is reliably *incomplete*, and incomplete is the failure mode that
actually shows up in practice.

---

## How to score

Each item is **Pass**, **Partial**, or **Fail**. There is no numeric total, on purpose
— a single Fail on boundaries matters more than three Partials on naming.

Severity tags used by the review prompt:

| Tag | Meaning |
|---|---|
| 🔴 **Blocker** | The design cannot be built or evaluated as written. |
| 🟡 **Gap** | Buildable, but a reviewer or teammate would have to guess something important. |
| 🔵 **Polish** | Correct and clear; could be tighter. |
| ❓ **Unclear** | The reviewer could not tell from what was submitted. |

---

## 1. Boundaries — what is and is not part of this system

| # | Check |
|---|---|
| 1.1 | Is there an explicit statement of what sits **inside** the system? |
| 1.2 | Is there an explicit statement of what sits **outside** it, that it talks to? |
| 1.3 | Is every external thing it depends on named? (power source, operator, network, another vehicle, a human) |
| 1.4 | Could a reader point at any element and say with confidence whether you are designing it or merely using it? |

**Why this comes first:** almost every confused design is a boundary problem wearing a
different costume. If you have not said where the system stops, you cannot say what an
interface is, because an interface is by definition a thing that crosses the boundary.

---

## 2. Decomposition — the parts

| # | Check |
|---|---|
| 2.1 | Is the system broken into named subsystems or blocks? |
| 2.2 | Does each block have a **single, statable responsibility**? (If describing a block needs the word "and" twice, it is probably two blocks.) |
| 2.3 | Are blocks at a **consistent level of zoom**? (A diagram containing both "Powertrain" and "M3 bolt" is mixing levels.) |
| 2.4 | Is the decomposition justified? Why *these* blocks and not a different cut? |
| 2.5 | Is anything in the diagram a box purely because you did not know where else to put it? |

---

## 3. Interfaces — what crosses between parts

| # | Check |
|---|---|
| 3.1 | Does every block declare its **inputs** and its **outputs**? |
| 3.2 | For each input and output, is the **type** stated? Not just "data" — *what* data, in what form, at what rate? |
| 3.3 | Are physical interfaces specified where they exist? (voltage, current, connector, torque, mounting) |
| 3.4 | Is there any block with outputs that nothing consumes, or inputs that nothing produces? |
| 3.5 | Are units stated everywhere a quantity appears? |

**The sharpest single question in this whole rubric:** *pick any arrow in your diagram
and say exactly what travels along it.* If you cannot, that arrow is decoration.

---

## 4. Flows — tracing things end to end

A flow is a path through the system, not a single hop. This repo tracks four kinds,
and they are genuinely different things that beginners routinely draw with the same arrow.

| # | Check |
|---|---|
| 4.1 | Are the four flow types **visually distinguished** from each other? |
| 4.2 | **Data / signal flow** — can you trace a measurement from the sensor that produced it to the thing that acts on it? |
| 4.3 | **Power flow** — can you trace energy from source to every consumer? Does anything draw power with no supply path drawn? |
| 4.4 | **Control flow** — who decides? Can you trace a command from the decision to the actuator? |
| 4.5 | **Mechanical / physical flow** — where are loads, forces, and motion transmitted? What is bolted to what? |
| 4.6 | Is at least one flow traced **completely**, start to finish, without a gap? |

For a purely software system, 4.3 and 4.5 may legitimately not apply — say so explicitly
rather than silently omitting them.

---

## 5. Requirements

| # | Check |
|---|---|
| 5.1 | Are **functional** requirements listed? (What the system must *do*.) |
| 5.2 | Are **non-functional** requirements listed, and kept separate? (How *well* — speed, weight, cost, reliability, power budget, latency, safety.) |
| 5.3 | Is each non-functional requirement **measurable**? "Fast" fails. "Responds in under 100 ms" passes. |
| 5.4 | Does the design visibly respond to the requirements, or do they sit in a list nobody used? |

---

## 6. Constraints and assumptions

| # | Check |
|---|---|
| 6.1 | Are constraints stated? (budget, rules, available parts, team skills, deadline, physical envelope) |
| 6.2 | Are assumptions stated **explicitly and separately** from facts? |
| 6.3 | For each assumption, is it clear what breaks if it turns out to be wrong? |
| 6.4 | Is there an assumption load-bearing enough that it should really be verified before building? |

**Why this matters more than it looks:** an unstated assumption is indistinguishable
from a mistake. Stating it converts a future argument into a checkable item.

---

## 7. Trade-offs

| # | Check |
|---|---|
| 7.1 | Is at least one real decision point identified? |
| 7.2 | For each decision, is the **option you rejected** named? |
| 7.3 | Is the reason for choosing stated in terms of the requirements or constraints above? |
| 7.4 | Is the **cost** of your choice acknowledged? Every choice gives something up. A trade-off with no downside is not a trade-off, it is a sales pitch. |

---

## 8. Communication

| # | Check |
|---|---|
| 8.1 | Could someone who has never seen this system understand it from the diagram plus one page of text? |
| 8.2 | Is there a legend, or are the conventions otherwise obvious? |
| 8.3 | Is naming consistent? (The same block called two different things is a real and common defect.) |
| 8.4 | Is the diagram readable at the size it will actually be viewed? |

---

## The ten failures that show up most often

Worth reading once before you design anything, and once again before you submit.

1. Arrows with no stated content — decoration posing as design.
2. No boundary, so "the system" quietly expands to mean everything.
3. Mixed zoom levels in one diagram.
4. Power ignored entirely. Everything draws current from nowhere.
5. Data flow and control flow drawn as the same arrow, so you cannot tell measurement from command.
6. Non-functional requirements that are adjectives instead of numbers.
7. Assumptions presented as facts.
8. A block named after a technology rather than a responsibility — the choice gets locked in before it was ever a choice.
9. Trade-offs listed with no rejected alternative, so nothing was actually traded.
10. A diagram that is really an org chart or a build sequence, not a system.
