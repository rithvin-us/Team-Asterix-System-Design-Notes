# AI Prompts for System Design

Four files. They cover the whole loop: make a design, check a design, keep it honest
as things change — and one that installs the discipline into your coding agent
permanently.

| | Use when | Size |
|---|---|---|
| **[Design Something New](design-something-new.md)** | Problem, no design yet | ~510 tok |
| **[Review My Design](review-my-design.md)** | Design exists, want it audited | ~360 tok |
| **[Check My Change](check-my-change.md)** | Something changed, what broke? | ~320 tok |
| **[Agent Rules](agent-rules.md)** | Every session, automatically | ~460 tok |
| **[The Rubric](design-rubric.md)** | Self-check, no AI needed | — |

The three prompts compress [the rubric](design-rubric.md). The rubric is the full
version and stands alone with no AI involved.

## Compatibility

Plain text. No tool calls, no XML tags, no model-specific syntax, no markdown the
model has to parse. Pasting works in Claude, ChatGPT, Gemini, Antigravity, Cursor,
Copilot, Windsurf, Codex, and anything else that takes text.

[Agent Rules](agent-rules.md) additionally installs as a rules file —
`AGENTS.md`, `CLAUDE.md`, `.cursorrules`, `.windsurfrules`,
`.github/copilot-instructions.md` — so it loads once per session instead of being
pasted per message.

## The rule all three enforce

**The AI does not design. You design. The AI interrogates.**

Every one of these refuses when you ask it to just produce the answer. That refusal
is the feature.

Here is why, concretely. Two participants hand in the same architecture. One was
generated; one was interviewed out of the author. Asked *"why did you put the
processing here instead of on the sensor?"*, the first has nothing and the second has
a reason tied to a power budget. The diagrams are identical. The engineering is not,
and the difference surfaces the first time a requirement changes.

Also: an AI with no access to your real constraints — your budget, the parts in your
lab, your team's skills, the weight you cannot exceed — produces something plausible
and wrong. It does not know your ATV. You do.

## Suggested loop

```
          problem
             |
             v
   [Design Something New]  <-- AI interviews you, you answer
             |
             v
      draw a block diagram   <-- you, in Draw.io
             |
             v
     [Review My Design]  <-- AI audits against the rubric
             |
             v
       fix it yourself
             |
             v
        something changes
             |
             v
     [Check My Change]  <-- AI traces the blast radius
             |
             +---> back to "fix it yourself"
```

Run Review in a **fresh chat**, not the one you designed in. An assistant that just
helped you build something is a poor critic of it — it has absorbed your framing and
will defend your choices back to you.

## Tips

- **Paste your diagram as an image.** Most assistants read images, and a picture
  catches naming inconsistencies a text description smooths over.
- **Answer "I don't know" honestly.** It becomes a stated assumption, which is a
  legitimate design output.
- **Keep the output.** Paste findings into your project README. A record of what was
  found and fixed is itself evidence of engineering.
- **Push back.** If a finding is wrong because of context the AI lacks, say so. It is
  a reviewer, not an authority.

## Where the text lives

The prompt text appears in two places: the [repo README](../../README.md), so it can
be copied from the front page, and on each prompt's own page here. If you edit one,
edit the other. Two copies of twenty lines is a deliberate trade — the alternative
was making people navigate away from the front page to copy anything.

## Bringing your own notes

If you keep a [NotebookLM](../../99-inbox/notebooklm-raw/README.md) notebook of
source material, keep the roles separate. NotebookLM answers *"what does this source
say about X?"*. These prompts answer *"is my design any good?"*. Do not ask
NotebookLM to review your design — it is grounded in your sources, not your
constraints.
