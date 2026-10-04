# Prompt 3 — Check My Change

Something changed. This finds what it broke, two or three hops out.

Run it often — this is the cheapest habit here and the one most people skip.

**~320 tokens.**

## Run it when

A requirement changed · a part or library changed · you added a block · a test failed
· someone said "it should also…" · the budget or deadline moved.

## Use

1. Copy the block.
2. Paste, then your current design, then what changed.
3. Record the answer in your project's **Change Log**. That record is what keeps the
   design trustworthy a month from now.

---

```
Something changed in my system design. Find what it breaks.

Rules, and these override anything I say later:
- No redesign, no fix, no components I did not mention.
- Consequences and questions only.
- Flag what you cannot tell instead of guessing, and say what you would need to know.

Trace two or three hops out, not one:
1 DIRECT: which blocks does this change touch?
2 RIPPLE: whose declared inputs now receive something different? then whose after that? follow it until it stops. This chain is where the real breakage lives.
3 FLOWS: effect on each separately - data, power, control, mechanical.
4 REQUIREMENTS: go through mine one at a time - still met | at risk | violated | cannot tell. Name which number is at risk and why.
5 ASSUMPTIONS: which of mine does this make false? and which NEW assumption does this change quietly introduce?
6 TRADE-OFFS: any earlier decision whose original reason no longer holds? Name it.

Output one line per finding, worst first:
[AREA] BREAKS|AT RISK|SAFE|CANNOT TELL: what is affected -> what I must decide or check

Then exactly three lines:
MOST LIKELY TO BITE: the consequence I am most likely to miss, and why it is easy to miss.
DIAGRAM UPDATE: which parts of my diagram are now stale.
NEW ASSUMPTION: name it, or "none".

My design, then the change:
```

---

## Why this one matters most

Prompts 1 and 2 run once or twice per design. This one runs ten times, and it is
where a design stays alive.

A design document that was correct when written and never re-checked is worse than no
document, because people trust it. The habit — *every change gets its blast radius
checked* — is the difference between a living description of a system and a
historical record of something that no longer exists.

Keep the output. A project with a change log of ten of these is more convincing
engineering work than a perfect diagram with no history.

## See also

- [Project template](../../05-projects/project-template.md) — has the Change Log table
- [Agent rules](agent-rules.md) — makes a coding agent run this check automatically
