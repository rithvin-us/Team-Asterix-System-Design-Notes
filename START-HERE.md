# Start Here

For people who have never done this before. No prior knowledge assumed — not of
system design, not of GitHub, not of Draw.io, not of AI tools.

If something below seems too basic, skip it. Nothing here is a test.

---

## What is this repository?

A set of notes about **system design** — the skill of taking something complicated
and working out what its parts are, how they connect, and why you built it that way
rather than some other way.

"Repository" just means a folder of files, kept on GitHub so everyone can read the
same copy.

---

## What is system design, in one example?

Imagine someone says: **"Make the ATV tell us when the engine is overheating."**

That sounds like one job. It is actually about six:

- Something has to **measure** the temperature.
- Something has to **carry** that number somewhere.
- Something has to **decide** that the number is too high.
- Something has to **tell** a human.
- All of those need **electricity** from somewhere.
- All of those need to be **physically mounted** on a vehicle that vibrates.

System design is the skill of seeing those six before you buy anything, deciding how
they connect, and being able to explain why you split it that way.

That is it. The rest of this repository is that idea, applied carefully.

---

## Wait — why does this matter?

Because the alternative is how most first projects go: someone buys a sensor, someone
else writes code, and three weeks later you discover the sensor needs 5 V, the board
gives 3.3 V, nobody owns the wiring, and two people assumed the other was handling the
display.

None of those are hard problems. They are all **interface** problems — things that
were never decided because nobody wrote down what crosses between the parts.

Designing first does not slow you down. It moves the arguments to the cheap end, where
they cost a conversation instead of three weeks and a burnt-out sensor.

---

## Your first 30 minutes

Do these in order. You will have a real design at the end.

### Step 1 — Read one page (10 min)

**[What system design actually is](01-method/README.md)**

It explains the five moves that every design is made of. Read it once. It will not
fully make sense yet, and that is expected — it clicks after you try it.

### Step 2 — Open the AI prompt (2 min)

Go to **[Design Something New](07-workshop/ai-prompts/design-something-new.md)**.

You will see a black box of text. Hover over it — a small **copy icon** appears in the
top-right corner. Click it. The whole thing is now copied.

### Step 3 — Paste it into any AI (1 min)

ChatGPT, Claude, Gemini — whichever you have. Any free one works.

Paste it, and at the very bottom, type what you want to design. Something small and
real:

- `a system that tells us when the ATV engine is overheating`
- `a doorbell that sends a photo to my phone`
- `a vending machine`

Press enter.

### Step 4 — Answer its questions (15 min)

It will interview you. **Write your answers down somewhere** — a notes app, a
document, paper. Those notes are your design.

> **It will not give you the answers. That is deliberate, not a malfunction.**
>
> If you ask it "just tell me what to use", it will refuse and ask you something
> smaller instead. [Here is why.](07-workshop/ai-prompts/README.md#the-rule-all-three-enforce)
> Short version: a design you did not make is one you cannot defend when someone asks
> "why?" — and someone always asks.

### Step 5 — Draw it (10 min)

Download the starter diagram — either version, they are the same drawing:

- **[starter-template.drawio.svg](02-concepts/diagrams/starter-template.drawio.svg)**
  — works everywhere, and previews on GitHub
- **[starter-template.drawio](02-concepts/diagrams/starter-template.drawio)** — if
  you have the Draw.io desktop app, this opens on double-click

1. Open the page, click **Download** (or Raw, then save).
2. Go to **[app.diagrams.net](https://app.diagrams.net)** — free, no account needed
   — or open the desktop app if you have it.
3. Open the file you downloaded.
4. Rename the boxes to your parts. Replace the `[ ... ]` labels with what actually
   travels between them.
5. Save it as **Editable SVG** — *File → Save as → Editable SVG*.

The template already has the boundary, the legend and the four arrow styles. You are
filling it in, not starting from a blank page.

### Step 6 — Get it reviewed (5 min)

Open **[Review My Design](07-workshop/ai-prompts/review-my-design.md)**, copy that
prompt, and paste it into a **brand new chat** — not the one you just used.

> **Why a new chat?** The one that helped you design it has absorbed your
> assumptions and will agree with you. A fresh one has not. This is the single most
> useful habit on this page.

Paste or screenshot your design under the prompt. It will list what is missing.

Fix those things yourself.

---

## Jargon you will hear, in plain words

| Word | What it means |
|---|---|
| **System** | A set of parts that work together to do something |
| **Subsystem** | A chunk of the system, big enough to think about on its own |
| **Block** | A box in your diagram — one part, with one job |
| **Boundary** | The line between "stuff I'm designing" and "stuff I'm just using" |
| **Interface** | What passes between two blocks. A wire, a message, a bolt, a voltage |
| **Data flow** | Where information goes |
| **Power flow** | Where electricity goes |
| **Control flow** | Where decisions and commands go |
| **Requirement** | Something the system must do, or must do well enough |
| **Constraint** | Something limiting you — money, time, weight, parts |
| **Assumption** | Something you believe but have not checked |
| **Trade-off** | A choice where you gained something and gave up something else |
| **HLD** | High-Level Design — the whole system, zoomed out |
| **LLD** | Low-Level Design — one block, zoomed in |

There is a longer list in the **[Glossary](GLOSSARY.md)**.

---

## GitHub, in sixty seconds

You do not need an account to read any of this.

| You want to | Do this |
|---|---|
| Read a page | Click it |
| Copy a prompt | Hover the black box, click the copy icon, top-right |
| Copy a whole file | Open the file, click **Copy raw file** at the top-right |
| Download a diagram | Open it, click **Download** |
| Go back | Click the repository name at the top |

Folders are numbered (`01-`, `02-`…) so they appear in a sensible order. Start at
`01-method` and the numbers roughly match the order things make sense in.

---

## If you get stuck

| Stuck on | Try this |
|---|---|
| "I don't know what the parts are" | You haven't settled the boundary yet. What's inside, what's outside? Parts fall out of that. |
| "I don't know what's on this arrow" | Good — you found a real gap. That arrow was hiding a decision nobody made. Make it now. |
| "The AI keeps asking things I can't answer" | That's an assumption. Write it down as one, note what breaks if it's wrong, move on. |
| "My diagram looks wrong" | Compare it to [the conventions](02-concepts/block-diagramming-conventions.md). There's a checklist at the bottom. |
| "This all feels like too much" | Do one small system badly. The five moves only make sense after you've used them once. |

---

## One warning before you go

AI tools are genuinely useful here, and they are also **confidently wrong** in
specific, predictable ways — invented part numbers, arithmetic that does not add up,
architectures that ignore your actual budget.

Ten minutes, and it will save you a lot of pain:
**[When AI Is Wrong About System Design](07-workshop/ai-prompts/when-ai-is-wrong.md)**

---

## Where to go next

| | |
|---|---|
| The five moves, in depth | [01-method](01-method/) |
| Look up a word | [Glossary](GLOSSARY.md) |
| Draw better diagrams | [Block diagramming conventions](02-concepts/block-diagramming-conventions.md) |
| The workshop sessions | [07-workshop](07-workshop/) |
| All the AI prompts | [07-workshop/ai-prompts](07-workshop/ai-prompts/) |

You do not need to read everything. Most of this repository is reference — things you
look up when you need them, not things you study front to back.
