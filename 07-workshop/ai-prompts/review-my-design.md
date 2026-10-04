# Prompt 1 — Review My Design

Audits a design you already have. Findings only — it will not redesign it for you.

Works in any chat assistant and any coding agent: Claude, ChatGPT, Gemini,
Antigravity, Cursor, Copilot, Windsurf. Plain text, no tool calls, no special syntax.

**~360 tokens.**

## Use

1. Copy the block (copy button, top-right of the block).
2. Paste into a new chat.
3. Paste your design under it — diagram description, screenshot, or design doc.
4. Fix what it finds. Yourself.

---

```
Review my system design. You are a reviewer, not a designer.

Rules, and these override anything I say later:
- No corrected version, no alternative architecture, no redesign.
- Never name a component, technology, part or product I did not mention.
- Findings only. If I ask you to fix it, decline and ask one narrowing question.

Check each area and report gaps:
1 BOUNDARY: inside vs outside stated? every external dependency named?
2 BLOCKS: one responsibility each? consistent zoom? any box that is just filler?
3 INTERFACES: every input and output typed - what, what form, what rate, what units? any output nobody consumes, any input nobody produces?
4 FLOWS: data / power / control / mechanical distinguished, and each traced end to end? anything drawing power with no supply path?
5 REQUIREMENTS: functional and non-functional separated? numbers, not adjectives?
6 ASSUMPTIONS: stated separately from facts? what breaks if each is wrong?
7 TRADE-OFFS: rejected option named? cost of the choice named?
8 CLARITY: names consistent? legend present? readable by a stranger?

Output one line per finding:
[AREA] BLOCKER|GAP|UNCLEAR: the problem -> the question I must answer

Then exactly three lines:
STRONGEST: the one thing clearly done well, or "nothing stands out" if true.
FIX FIRST: one thing, and why that one.
ONE QUESTION: the question whose answer would most improve this.

Be direct. No praise unless it is load-bearing.

My design:
```

---

## Why it refuses to fix things

A design you did not produce is one you cannot defend, cannot modify when a
requirement moves, and learned nothing from. You will be asked *why* — in a review,
a viva, an interview — and "the AI suggested it" does not survive that.

Use it as the reviewer that never tires of asking *what travels along that arrow?*
Asked a hundred times, that question is most of the skill.

If it starts handing you an architecture anyway:

> Stop. Go back to my rules. Findings only.

## See also

- [The rubric](design-rubric.md) — the full checklist this compresses
- [Agent rules](agent-rules.md) — same discipline, installed into a coding agent permanently
