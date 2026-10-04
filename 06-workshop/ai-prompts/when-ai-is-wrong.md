# When AI Is Wrong About System Design

Everyone tells you to use AI. Almost nobody tells you **where it fails**, which is the
part that gets you a vehicle that does not start.

This page is about that. Read it before you trust anything an assistant tells you
about your design.

---

## The one thing to understand

An AI does not know when it is wrong.

It produces the most *plausible-sounding* continuation of your conversation. When it
knows the answer, plausible and correct are the same thing. When it does not, it still
produces something plausible, at the same confidence, in the same tone, with the same
fluent sentences.

There is no wobble in its voice. There is no "I think". A wrong answer and a right
answer look **identical**.

That is the whole problem. Everything below is a consequence of it.

---

## The seven failures, in the order they will bite you

### 1. Invented part numbers and specs

You will be told about a sensor with a part number that does not exist, or a real
sensor with specifications it does not have. The number will be the right *shape*,
plausible voltage, plausible range, plausible update rate, and simply not true.

**Why it happens:** it has seen thousands of datasheets. It has learned what a
datasheet line *looks like*. It has not memorised yours.

**What to do:** every part number, voltage, current, pin count and operating range
gets checked against the actual datasheet. Every one. The AI is allowed to tell you a
part *category* exists. It is not allowed to be your source for a number.

### 2. Confident, wrong arithmetic

Power budgets, current draw, weight sums, bandwidth, battery life. It will add up
seven current draws and give you a total that is simply incorrect, formatted neatly,
with units.

**Why it happens:** it predicts text. Arithmetic is not prediction, and long chains of
it drift.

**What to do:** do the sum yourself. Calculator, phone, paper. If a number decides
something, which battery, which wire gauge, whether the Jetson browns out, you
compute it.

### 3. Architecture that ignores your real constraints

Ask for a telemetry design and you get a good one. For somebody else. It assumes
budget you do not have, parts you cannot get, weight you cannot carry, and skills your
team does not have.

**Why it happens:** it does not know your budget, your lab, your ATV, your deadline or
your team, and it will not ask unless the prompt makes it.

**What to do:** this is exactly why
[the prompts here](prompts-index.md) refuse to produce designs. You hold the constraints. An
architecture built without them is decoration.

### 4. Agreeing with you

Push back on an AI and it very often folds. Say "are you sure?" and watch it
apologise and change its answer, **even when it was right the first time**.

**Why it happens:** it is trained to be agreeable. Your disagreement is a strong
signal about what you want to hear.

**What to do:** never treat agreement as confirmation. If it caves the moment you
object, it never knew. Ask *"what evidence would change your mind?"* rather than
*"are you sure?"*.

### 5. Defending your design because it helped you build it

An assistant that spent an hour helping you design something is a terrible critic of
that design. It has absorbed your framing, your assumptions, your vocabulary, and it
will reflect them back as agreement.

**What to do:** **always review in a fresh chat.** This is not a nicety; it is the
single highest-value habit on this page. Same prompt, new conversation, no history.

### 6. Protocols and interfaces that do not exist on your hardware

It will confidently connect two blocks with a protocol that one of them does not
speak, or suggest a bus with more devices on it than the bus supports, or wire two
things together that are electrically incompatible.

**Why it happens:** at the level of text, "sensor sends data to controller over X" is
a sentence that reads fine. Whether that chip has that peripheral is a physical fact
it has no access to.

**What to do:** every interface between two real parts gets confirmed against both
datasheets. Both, not one.

### 7. Old information presented as current

Models have a training cutoff. Libraries change, parts go out of production, APIs
move, prices move. It will not tell you its information is two years old, because it
does not know which parts of what it learned have since changed.

**What to do:** anything time-sensitive, prices, availability, library versions,
"the current recommended way", gets checked against a live source.

---

## Where AI is genuinely good at this

This page is not an argument against using it. The failures above are narrow and
specific, and outside them it is extremely useful:

| Good at | Because |
|---|---|
| **Asking you questions you did not think of** | It never gets bored of asking "what travels along that arrow?" |
| **Finding gaps in what you wrote** | Pattern-matching absence is easier than inventing truth |
| **Explaining a concept five different ways** | Genuinely better than a textbook at meeting you where you are |
| **Tracing consequences of a change** | Tireless at following a chain two or three hops out |
| **Being a rubber duck at 2am** | It is there, and it responds |
| **Turning your rambling into structure** | Shaping text is what it actually does |

Notice the pattern: **it is good at operating on information you supply, and bad at
supplying information.**

That one sentence is the whole skill. Give it your design and it will do excellent
work. Ask it for a design and you get fiction that reads like engineering.

---

## The habits that follow

1. **Fresh chat for review.** Never review in the chat that designed.
2. **Every number verified.** If it decides something, you compute or source it.
3. **Every part checked against its datasheet.** Not the AI's summary of one.
4. **Treat agreement as noise.** It agreeing with you is not evidence.
5. **State your constraints up front**, budget, weight, parts, deadline, or you
   will get a design for somebody else's vehicle.
6. **Ask "what would change your mind?"** rather than "are you sure?"
7. **Keep what it got wrong.** Write it into your project's change log. Real examples
   from your own project teach far better than this page does.

---

## The one-line test

Before you use anything an AI told you about your design, ask:

> **Did it tell me this, or did it reorganise something I told it?**

Reorganising your input is what it is for. Supplying facts is where it fails.

---

## For instructors

Collect real failures from these sessions, a hallucinated part number, a power budget
that does not add up, an architecture that ignored the weight limit, and add them to
the list above. A failure a participant watched happen is worth more than this entire
page.

## See also

- [The AI prompts](prompts-index.md), built around these failure modes
- [Agent rules](agent-rules.md), installs the discipline permanently
- [The rubric](design-rubric.md), what to check, with or without AI
