# <System Name>

One sentence: what this system does, for whom, and what counts as success.

| | |
|---|---|
| **Domain** | automotive / software / … |
| **Difficulty** | starter / intermediate / hard |
| **Pattern** | the architectural shape, if it has a recognisable one |
| **Illustrates** | which [concepts](../../../02-concepts/) this is a good study for |

---

## 1. Boundary

**Inside** — what is being designed.

**Outside but connected** — what it talks to and depends on.

**Deliberately not doing** — at least two things excluded on purpose.

---

## 2. Requirements

### Functional
What it must do.

### Non-functional
How well. Numbers, with how each is measured. No adjectives.

| Requirement | Target | Measured how |
|---|---|---|
| | | |

---

## 3. Constraints and assumptions

### Constraints
Budget, parts, rules, time, weight, space, skills.

### Assumptions

| Assumption | What breaks if it is wrong | Verified? |
|---|---|---|
| | | |

---

## 4. Decomposition

The blocks, each with one responsibility stated in a sentence.

| Block | Responsibility |
|---|---|
| | |

**Why this cut** — and what the alternative cut would have been.

![HLD](diagrams/<slug>-hld.drawio.svg)

---

## 5. Interfaces

| From | To | Carries | Form | Rate | Units |
|---|---|---|---|---|---|
| | | | | | |

---

## 6. Flows

**Data / signal** — one measurement traced from sensing to action, every hop.

**Power** — energy from source to every consumer.

**Control** — one command traced from decision to actuator. What if it is late or wrong?

**Mechanical / physical** — load paths, attachment, motion. *(State explicitly if not applicable.)*

---

## 7. Low-level design

Only for blocks that are genuinely complex, contested, or about to be built.

### <Block name>
Expands HLD block: **<name>**

![LLD](diagrams/<slug>-lld-<subject>.drawio.svg)

---

## 8. Trade-offs

| Decision | Chosen | Rejected | Why | What it costs |
|---|---|---|---|---|
| | | | | |

Least confident decision, and why.

---

## 9. Change log

Every time something changed, what it broke. Run
[Check My Change](../../../07-workshop/ai-prompts/check-my-change.md) and record the
result here.

| Date | Change | Blast radius | Resolved how |
|---|---|---|---|
| | | | |

---

## 10. What this study teaches

The two or three transferable lessons. The reason this is in the repo at all.
