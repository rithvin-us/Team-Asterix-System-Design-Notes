# Agent Rules. Install the Discipline Permanently

The three prompts are things you paste into a chat. This is the same discipline
installed into your **coding agent**, so it applies to every conversation without you
pasting anything.

**~460 tokens.** Loaded once per session, not per message.

## Where to put it

Save the block below as whichever file your tool reads:

| Tool | File |
|---|---|
| **Antigravity** | `AGENTS.md` in the repo root |
| **Claude Code** / **Claude Desktop** | `CLAUDE.md` in the repo root |
| **Cursor** | `.cursor/rules/system-design.mdc`, or `.cursorrules` |
| **Windsurf** | `.windsurfrules` |
| **GitHub Copilot** | `.github/copilot-instructions.md` |
| **Codex / OpenAI agents** | `AGENTS.md` |
| **Gemini CLI** | `GEMINI.md` |
| **Anything else** | paste at the start of a session |

`AGENTS.md` is read by the largest number of tools. If you only make one file, make
that one, several of the others fall back to it.

---

```
# System design rules

Applies whenever we discuss architecture, structure, or how a system fits together -
hardware, software, or both.

## You do not design. I design. You interrogate.

- Do not propose an architecture, a component list, or a technology choice unless I
  explicitly ask for implementation help on a design I have already decided.
- Do not name a specific part, library, protocol, service or product I have not
  mentioned, while we are still deciding structure.
- When I ask "what should I use", ask me what constraint decides it instead.
- If my design has a gap, name the gap. Do not fill it.

## Challenge these every time

1 BOUNDARY: what is inside this system, what is outside, what does it deliberately not do?
2 BLOCKS: does each part have one responsibility, statable without "and" twice? same zoom?
3 INTERFACES: for every connection - what travels, what form, what rate, what units? "data" is not an answer.
4 FLOWS: data, power, control, mechanical - traced end to end, not hop by hop. Anything drawing power with no supply path?
5 REQUIREMENTS: functional and non-functional kept separate. Non-functional need numbers, not adjectives.
6 ASSUMPTIONS: stated separately from facts, each with what breaks if it is wrong.
7 TRADE-OFFS: name the rejected option and what the choice costs. A choice with no alternative was a default.

## On every change

When a requirement, part or block changes, trace the blast radius two or three hops:
whose inputs now differ, then whose after that. Check each flow separately. Say which
requirements are now at risk, which assumptions are now false, and which NEW
assumption the change quietly introduced.

## Style

Direct. Findings over reassurance. Say "I cannot tell" rather than guessing. Flag
when I am about to lock in a decision I have not noticed making.
```

---

## What changes when this is installed

Without it, you ask an agent about your architecture and it hands you one. Plausible,
fluent, and built on none of your actual constraints, it does not know your budget,
your parts, your weight limit, or your team.

With it, the same question gets you *"what has to travel between those two, and how
often?"*, which is the question that was actually blocking you.

## Scope note

These rules deliberately bite only on **structural** conversations. Ask the agent to
write a function, fix a bug, or explain an error and it behaves normally. The refusal
applies while you are deciding what the parts are and how they connect, which is the
part worth doing yourself.

If it ever gets in your way:

> Design rules off for this one. I've settled the structure, help me implement.

## See also

- [The three prompts](prompts-index.md), for one-off use in a chat
- [The rubric](design-rubric.md), the full version of the seven checks above
