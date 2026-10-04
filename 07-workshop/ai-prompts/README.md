# AI Prompts for System Design

Three prompts. They cover the whole loop: make a design, check a design, keep a
design honest as things change.

| Prompt | Use when | Time |
|---|---|---|
| **[Design Something New](design-something-new.md)** | You have a problem, no design yet | 30–60 min |
| **[Review My Design](review-my-design.md)** | You have a design, want it audited | 5–10 min |
| **[Check My Change](check-my-change.md)** | Something changed, you want to know what broke | 5 min, run often |

All three read from the same **[design rubric](design-rubric.md)**. You can use that
rubric on its own, with no AI at all, as a self-check before you submit anything.

## The rule all three enforce

**The AI does not design. You design. The AI interrogates.**

Every one of these prompts is built to refuse when you ask it to just produce the
answer. That refusal is the feature.

Here is why, concretely. Two participants hand in the same architecture. One was
generated; one was interviewed out of the author. Asked "why did you put the
processing here instead of on the sensor?", the first has nothing and the second has
a reason tied to a power budget. The diagrams are identical. The engineering is not,
and the difference becomes visible the first time a requirement changes.

Also: an AI with no access to your actual constraints — your real budget, the parts
in your lab, your team's skills, the weight you cannot exceed — will produce
something plausible and wrong. It does not know your ATV. You do.

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

- **Paste your diagram as an image.** Most assistants read images now, and a picture
  catches naming inconsistencies that a text description smooths over.
- **Answer "I don't know" honestly.** It turns into a stated assumption, which is a
  legitimate and valuable design output.
- **Keep the output.** Paste findings into your project README. A record of what was
  found and fixed is itself evidence of engineering.
- **Push back on the AI.** If a finding is wrong because of something it does not
  know about your context, say so. It is a reviewer, not an authority.
- **Any assistant works.** These are plain text with no tool dependencies.

## Bringing your own notes

If you keep a [NotebookLM](../../99-inbox/notebooklm-raw/README.md) notebook of
source material, you can ask it questions about concepts — but keep the roles
separate. NotebookLM answers *"what does this source say about X?"*. These prompts
answer *"is my design any good?"*. Different jobs. Do not ask NotebookLM to review
your design; it is grounded in your sources, not in your constraints.
