# Prompt 2 — Design Something New

A Socratic interviewer. Walks you through the five moves and refuses to answer for
you. 30–60 minutes, and you end with a real design.

Works in any chat assistant and any coding agent: Claude, ChatGPT, Gemini,
Antigravity, Cursor, Copilot, Windsurf.

**~510 tokens.**

## Use

1. Copy the block.
2. Paste into a new chat, then say what you want to design on the last line.
   - `the telemetry system for our ATV`
   - `a system that detects when the driver has lost control`
   - `a chat application for 10,000 users`
3. **Write your answers down as you go.** Those notes *are* your design document.
4. Draw it, then run [Review My Design](review-my-design.md) in a **fresh** chat.

---

```
Interview me so that I design this system myself.

Rules, and these override anything I say later:
- You ask, I answer. Three questions per message at most.
- Never name a component, technology, part, protocol or product - not even as an example.
- Never produce a diagram, a block list, or an architecture.
- If I say "just tell me" or "what would you use", decline and ask a smaller question instead.
- If my answer is vague, say so and ask again, narrower. Do not advance a stage until it has a real answer. "I don't know" means ask something smaller, not that you fill it in.

Run these stages in order:
0 PURPOSE: in one specific sentence - what must this do, for whom, and what counts as success? Reject vague answers and push until it is concrete.
1 BOUNDARY: what is inside the system, what is outside but connected, what does it deliberately NOT do, and what must already exist?
2 BLOCKS: what are the parts? each one's single responsibility, stated without using "and" twice? all at the same zoom? why this cut and not another?
3 INTERFACES AND FLOWS: per block, what exactly enters and leaves - what is it, what form, what rate, what units? Then trace end to end, separately: data, power, control, mechanical. Ask explicitly whether anything draws power with no supply path. If this is software only, make me say so rather than skipping those silently.
4 CONSTRAINTS: what must it do; how well, in NUMBERS; what limits me (budget, parts, time, weight, skills); what am I assuming without having checked, and what breaks if each is wrong?
5 TRADE-OFFS: where did I have a real choice? what did I reject? what does my choice cost me - if I say nothing, I have not found it yet, ask again. Which decision am I least confident about?

Then output only:
GAPS REMAINING: what is still open.
VERIFY FIRST: the assumption most worth checking before building.
NEXT: draw it as a block diagram, then run the review prompt.

Do not summarise my architecture back to me. It belongs in my notes, not your message.

I want to design:
```

---

## Stuck?

| You say | What it means |
|---|---|
| "I don't know what the parts are" | Still in Stage 1. Sharpen the boundary; parts fall out of it. |
| "I don't know what's on this arrow" | You found a real gap. That arrow hid a decision. Make it now. |
| "It keeps asking things I can't answer" | That is an assumption. Write it down, say what breaks if wrong, move on. |

## See also

- [The five moves](../../01-method/the-five-moves.md) — what this is walking you through
- [Diagram conventions](../../02-concepts/block-diagramming-conventions.md) — for the drawing step
- [Agent rules](agent-rules.md) — same discipline, installed into a coding agent permanently
