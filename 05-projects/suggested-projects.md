# Suggested Projects

Three projects chosen to teach system design, not coding. Each is picked because it
**forces** a specific design problem you cannot avoid by being a good programmer.

Pick one. Do it properly, design first, record the trade-offs, keep the change log.
One done properly beats three done fast, and it is the one you can defend afterwards.

| | Project | Forces you to learn | Scale |
|---|---|---|---|
| **1** | [ATV Health & Telemetry](#project-1--atv-health-and-telemetry-monitor) | Power, physical constraints, real-time limits | Team, 3–5 weeks |
| **2** | [Pit-Lane Race Dashboard](#project-2--pit-lane-race-dashboard) | Data flow, interfaces, failure behaviour | 2–3 people, 2–3 weeks |
| **3** | [Campus Shuttle Tracker](#project-3--campus-shuttle-tracker) | Scale, state, offline edge cases | Solo or pair, 2 weeks |

Project 1 is hardware-heavy. Project 3 is software-only. Project 2 sits between them
and is the best single choice if your team is mixed.

---

## Project 1. ATV Health and Telemetry Monitor

**Build a system that tells the team, while the vehicle is running, whether the ATV is
healthy, and warns before something breaks rather than after.**

### Why this one teaches system design

It is the only project here where **you cannot ignore power**. Every sensor draws
current, the engine bay is electrically filthy, wires come loose on a vehicle that
vibrates, and the whole thing has a weight budget. Software skill will not save a
design that forgot where the 5 V comes from.

It also forces the four flows to be genuinely different things: temperature readings
(data), battery to sensors (power), "warn the driver now" (control), and sensor
mounting that survives a rough course (mechanical).

### The design problems you cannot dodge

- **Power budget.** Add up every consumer. Does the battery carry it for a full run?
- **Where does processing happen?** On the vehicle, or send raw data off it? This is a
  real trade-off with real costs on both sides.
- **What happens when a sensor lies?** A loose thermocouple reads garbage, not
  nothing. How does the system tell a real reading from a broken one?
- **What is the warning threshold, and who decides?** A number nobody can justify is
  an unstated assumption.
- **Mounting.** What survives vibration, heat and mud?

### Minimum viable scope

Two sensors, one decision, one output. Engine temperature and battery voltage; warn
when either leaves a safe band. Everything beyond that is extension.

### What success looks like

The warning fires before the failure, not after, and you can state, with numbers, how
much warning it gives.

### Extensions once it works

Wireless telemetry to the pit · logging for post-run analysis · a second decision that
needs two sensors to agree · graceful behaviour when a sensor dies mid-run.

---

## Project 2. Pit-Lane Race Dashboard

**A live display, away from the vehicle, showing what the ATV is doing right now.**

### Why this one teaches system design

Because the hard part is **the link, not the display**. The vehicle moves, the
connection drops, data arrives late, out of order, or not at all. Every one of those
is an interface decision you have to make explicitly.

It is also the clearest project for the question *what travels along that arrow?*,
the answer changes the design completely depending on whether you send every reading,
a summary, or only changes.

### The design problems you cannot dodge

- **What exactly gets transmitted?** Every reading, or a summary? At what rate? This
  single decision drives bandwidth, power and perceived responsiveness.
- **What does the display show when the link is down?** Last known value, a blank, or
  a warning? All three are defensible, but they are different designs and you must
  pick one and say why.
- **How stale is too stale?** Three-second-old speed may be fine. Three-second-old
  "engine overheating" is not. Does one number cover both?
- **Who buffers?** If the vehicle stores readings while disconnected, how many, and
  what gets dropped first?
- **Boundary.** Is the pit laptop inside your system or outside it?

### Minimum viable scope

One value, transmitted from the vehicle, displayed with its age in seconds. Showing
*how old the data is* is the whole lesson, make it visible from the first version.

### What success looks like

Walk the transmitter out of range and back. The dashboard behaves sensibly throughout
and nobody is misled at any point.

### Extensions once it works

Multiple vehicles on one dashboard · alert history · replaying a saved run ·
prioritising safety messages over telemetry when bandwidth is tight.

---

## Project 3. Campus Shuttle Tracker

**Students see where the campus shuttle is and when it will reach their stop.**

### Why this one teaches system design

No hardware to hide behind. It is the clearest introduction to the software side,
state, scale and the question of what counts as correct, and it maps directly onto
the "design a ride-sharing app" interview question you will meet later.

Its real difficulty is that **the interesting cases are all edge cases**. The happy
path is easy. The design is in what happens when the shuttle stops, the driver forgets
to start tracking, or 400 students open the app at once.

### The design problems you cannot dodge

- **Where does the prediction happen,** and what is it based on? A guess presented as
  a time is worse than no time.
- **How often does position update?** Battery and bandwidth on one side, accuracy on
  the other. Pick a number and justify it.
- **What if the shuttle stops moving?** Traffic, a break, or a dead tracker all look
  identical from the data. How do you tell them apart, or do you admit you cannot?
- **400 people at 9am.** What actually breaks first? Be specific.
- **What is "correct"?** If the shuttle arrives at 9:03 and you said 9:01, was that
  wrong? Define it before you build it.

### Minimum viable scope

One shuttle, one route, a map with a dot and a last-updated time. No predictions in
version one, add them only after position is trustworthy.

### What success looks like

A student who has used it for a week trusts it, and can say what it does when it does
not know.

### Extensions once it works

Multiple shuttles · crowding reports from users · notifications near your stop ·
historical data to improve predictions.

---

## Doing any of these properly

1. **Design before building.** Run
   [the design prompt](../06-workshop/ai-prompts/design-something-new.md). It takes an
   hour and saves a fortnight.
2. **Draw it** from the
   [starter template](../02-concepts/diagrams/starter-template.drawio.svg).
3. **Review it**, [the review prompt](../06-workshop/ai-prompts/review-my-design.md),
   in a fresh chat.
4. **Copy [the project template](project-template.md)** and fill it as you go, not at
   the end.
5. **Every time something changes,** run
   [the change check](../06-workshop/ai-prompts/check-my-change.md) and record it in
   the change log. Something will change in week one.
6. **Write the retrospective while it is fresh.**

The deliverable is **the design record, not the build**. A working prototype with no
record of why it is shaped that way teaches you nothing and shows a reader nothing. A
complete design record with a half-working prototype is a far stronger piece of work,
and it is the thing you can put in front of a recruiter.
