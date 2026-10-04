# <Project Name>

One sentence: what this must do, for whom, and what counts as success.

| | |
|---|---|
| **Status** | designing / building / testing / done |
| **Domain** | automotive / software / … |
| **Started** | |

---

## 1. Problem

What is wrong or missing that this exists to address. Written before any solution is
in mind. If this section mentions a component, it was written too late.

---

## 2. Requirements

### Functional

### Non-functional

| Requirement | Target | Measured how |
|---|---|---|
| | | |

Numbers, not adjectives. If it has no number it is not a non-functional requirement,
it is a hope.

---

## 3. Constraints and assumptions

### Constraints
Budget, parts available, rules, deadline, team skills, weight, space.

### Assumptions

| Assumption | What breaks if wrong | Verified? |
|---|---|---|
| | | |

Verify the load-bearing ones **before** building, not after.

---

## 4. Boundary

**Inside** — what you are designing.

**Outside but connected** — what you use but do not design.

**Deliberately not doing** — at least two things.

---

## 5. High-level design

| Block | Responsibility |
|---|---|
| | |

**Why this cut**, and what the alternative was.

![HLD](diagrams/<slug>-hld.drawio.svg)

### Interfaces

| From | To | Carries | Form | Rate | Units |
|---|---|---|---|---|---|
| | | | | | |

### Flows

**Data / signal**

**Power**

**Control**

**Mechanical / physical** *(state explicitly if not applicable)*

---

## 6. Low-level design

Only for blocks that are complex, contested, or next to be built.

### <Block name>
Expands HLD block: **<name>**

![LLD](diagrams/<slug>-lld-<subject>.drawio.svg)

---

## 7. Implementation

What was actually built, and **where it diverged from the design**. The divergences
are the valuable part — each one is either a design error you found or a shortcut you
took, and both are worth knowing.

---

## 8. Testing

How you know it works. Tie each test back to a requirement from section 2 — a test
that maps to no requirement is testing something nobody asked for.

| Requirement | Test | Result |
|---|---|---|
| | | |

---

## 9. Trade-offs

| Decision | Chosen | Rejected | Why | What it cost |
|---|---|---|---|---|
| | | | | |

---

## 10. Change log

Run [Check My Change](../../07-workshop/ai-prompts/check-my-change.md) on every
change and record it.

| Date | Change | Blast radius | Resolved how |
|---|---|---|---|
| | | | |

---

## 11. Retrospective

- What worked
- What did not
- What you would cut differently next time
- What you assumed that turned out false
- The single thing you would tell someone starting this project

Write this while it is fresh. A retrospective written a month later is a list of the
things you happen to still remember, which is not the same list.
