# Conventions

How this repository is organised, and why. Read once; refer back when you are not
sure where something goes.

---

## The one rule that matters

**Folders encode the method. They do not encode the domain.**

Automotive material and software material sit next to each other inside
`03-examples/` and `04-case-studies/`. There is deliberately no top-level split
between hardware and software, mechanical and digital, ATV and cloud.

Why: the five moves — decompose, interfaces, flows, constraints, trade-offs — are the
same regardless of what you are designing. Splitting by domain at the top would
duplicate the entire method tree twice and force every new note into an arbitrary
side. Splitting by method keeps one tree and makes domain a detail.

The practical test: **if a new note has two plausible homes, the structure is wrong.**
This layout is tuned so that almost never happens.

---

## Top-level directories

| Folder | Holds | Does not hold |
|---|---|---|
| `01-method/` | The five moves. Process, not vocabulary. | Definitions of terms. |
| `02-concepts/` | Ideas and vocabulary. One idea per file. | Worked examples. |
| `03-examples/` | Small illustrations of a single point. | Full systems. |
| `04-case-studies/` | Whole systems traced end to end. | Things you build. |
| `05-exercises/` | Short practice tasks, 15–60 min. | Multi-week work. |
| `06-projects/` | Substantial builds with a full design record. | Quick practice. |
| `07-workshop/` | Asterix session material, prompts, mini project. | Reusable knowledge. |
| `99-inbox/` | Unverified and unfiled. Quarantine. | Anything canonical. |

The numeric prefixes exist only so GitHub lists them in a sensible order. `99-inbox`
is numbered to sort last, because it is the least authoritative thing here and should
look that way.

### Example vs case study

The line that gets blurred most often:

- **Example** — illustrates *one point*. "Here is what a badly drawn power flow looks
  like." Short, lives to make a single idea concrete. Often one diagram plus a
  paragraph.
- **Case study** — traces a *whole system* through all five moves. "Here is the ATV
  telemetry system, from requirements to trade-offs." Long, self-contained, has a
  complete design record.

If it exists to explain a concept, it is an example. If it exists to be studied as a
system, it is a case study.

### Exercise vs project

- **Exercise** — one sitting. Tests one skill. Has a defined answer or a short
  reference solution.
- **Project** — days or weeks. Open-ended. Produces a design record, diagrams, and a
  retrospective.

---

## Knowledge tiers — what you can trust

Four tiers, distinguished by **location only**. No per-file tags, no frontmatter, no
status fields to maintain. Where a file lives tells you what it is.

| Tier | Where | Means |
|---|---|---|
| **Canonical** | Anywhere outside `99-inbox/` | Written or rewritten deliberately. Stands behind it. |
| **Stub** | Marked `> **Status:** stub` at the top | Structure is real, prose is not written yet. |
| **Raw** | `99-inbox/notebooklm-raw/` | Machine-generated. Unverified. Nobody's understanding. |
| **Unfiled** | `99-inbox/unfiled.md` | Captured, not yet thought about. |

Why location and not tags: a tagging system requires effort on every single file, and
a tagging system you abandon in week two is worse than no system — it leaves half the
repo labelled and half not, which is less trustworthy than none of it being labelled.
Folders cost nothing to maintain and cannot silently rot.

---

## File naming

- `kebab-case.md` — lowercase, hyphens, no spaces, no underscores, no capitals.
- Name after the **idea**, not the format: `block-diagramming-conventions.md`, not
  `notes-on-diagrams-v2.md`.
- No dates, no version numbers, no `-final`, no `-v3`. Git already holds history, and
  a filename with a version in it is a filename that will be wrong.
- `README.md` in every directory. It is the index for that directory and the thing
  GitHub shows when you click in.
- `_TEMPLATE.md` and `_TEMPLATE/` — leading underscore marks a template, not content.
- `99-` prefix and `_` prefix are the only prefixes used. Do not invent more.

### Headings inside a file

- One `#` h1 per file, matching what the file is about.
- Stubs carry `> **Status:** stub` immediately after the h1. Nothing else marks state.
- Link between files with relative Markdown links: `[text](../02-concepts/thing.md)`.
  **No `[[wikilinks]]`** — they do not render on GitHub, and this repo is read on
  GitHub.

---

## Diagrams

### Format: `.drawio.svg`, always

One file that renders inline on GitHub **and** opens as an editable diagram in
Draw.io. This is the single most useful convention here, because it removes the
failure mode where a `.drawio` source and its exported `.png` drift apart and nobody
knows which is current.

- In Draw.io: **File → Save as → Editable SVG** (or name the file `*.drawio.svg`).
- Works in [app.diagrams.net](https://app.diagrams.net), the desktop app, and the VS
  Code extension.
- **Never** commit a plain `.png`, `.jpg`, or non-editable `.svg` of a diagram you
  made here. If you did not make it, a plain image is fine — but note where it came from.

### Where they live

**Next to the document they explain.** Not in a global `images/` or `diagrams/` folder
at the root.

```
04-case-studies/automotive/atv-telemetry/
├── README.md
└── diagrams/
    ├── atv-telemetry-hld.drawio.svg
    └── atv-telemetry-lld-sensor-node.drawio.svg
```

Why: a root-level image folder becomes a bucket of hundreds of files with names like
`diagram7.drawio.svg` that nobody can connect back to anything. Co-location means
deleting a case study deletes its diagrams, and moving it moves them.

### Diagram naming

```
<system-slug>-<level>[-<subject>].drawio.svg
```

- `atv-telemetry-hld.drawio.svg`
- `atv-telemetry-lld-sensor-node.drawio.svg`
- `atv-telemetry-lld-power.drawio.svg`

`<level>` is `hld`, `lld`, or `context`.

### How HLD and LLD relate

**They are the same system at two levels of zoom, not two separate trees.**

- The HLD shows blocks and what passes between them.
- An LLD takes **one block** from the HLD and opens it up.
- They are linked by the shared `<system-slug>`, and by the LLD stating in its first
  line which HLD block it expands.

**Not every HLD block needs an LLD.** Write an LLD when a block is genuinely complex,
contested, or about to be built. An LLD for every block is busywork, and it produces
a repo full of diagrams that restate their parent with more rectangles.

### Versions

Git tracks them. Do not keep `-v2` files, do not keep an `old/` folder. If you need
to show how a design evolved — which is a genuinely interesting thing to show — write
it up in prose in a **Change Log** section of the document, and let git hold the
diagrams.

---

## NotebookLM and other machine-generated material

**Rule: machine output is never canonical.**

The failure this prevents: a repo where AI-generated text and the author's actual
understanding are mixed together and indistinguishable, so a year later nobody — the
author included — can tell which parts were thought through and which were generated
and skimmed.

How it works:

1. Raw NotebookLM output goes into `99-inbox/notebooklm-raw/`. Nowhere else.
2. That folder has a README stating plainly that its contents are unverified.
3. To promote something into `02-concepts/` or anywhere else canonical, you
   **rewrite it in your own words**. Not reformat. Not lightly edit. Rewrite, from
   understanding.
4. If you cannot rewrite it without looking at it, you do not understand it yet, and
   it is not ready to be promoted. That test is the whole mechanism.
5. Sources are recorded as **links only** in `99-inbox/notebooklm-raw/sources.md`.
   No PDF or article copies — this repo is public and that is a copyright problem
   nobody needs.

The rewrite requirement is not about style. Copy-pasting a correct explanation
produces a repo that is correct and useless, because the understanding never moved
from the source into you.

---

## Unfiled notes

`99-inbox/unfiled.md` exists for the thing you discover mid-session with nowhere to
put it.

Append to the bottom. One `##` heading with the date, then whatever you have. Do not
tidy it, do not decide where it belongs, do not create a folder for it.

File it later, in batches, when you can see the shape of several notes at once. The
cost of capture must stay near zero or you will not capture, and the notes you lose
that way are the good ones — the ones that only occur to you while teaching.

---

## Status marking

Exactly one marker, and it is removed when no longer true:

```markdown
> **Status:** stub
```

No `draft`, no `wip`, no `review`, no `deprecated`, no percentage complete. If a
document is wrong, fix it or delete it. Deprecated documents that linger get read by
someone eventually.

---

## Do not over-engineer this repository

This section exists because every structured repo decays the same way — not by
becoming messy, but by becoming so much work to maintain that nobody maintains it.
These are the things already considered and deliberately rejected. Reconsider them
only when a specific problem forces it, not in anticipation.

**Deliberately absent:**

- **No CI/CD, no GitHub Actions.** Nothing here needs building, testing or deploying.
- **No GitHub Pages.** GitHub already renders Markdown and `.drawio.svg` well.
- **No scripts, no tooling, no generators.** A script to generate index files is
  a thing that breaks and then silently stops.
- **No issue templates, no PR templates, no CONTRIBUTING.md.** Single author.
  Process for a team of one is just friction.
- **No frontmatter, no YAML metadata, no tag taxonomy.** Location carries the
  metadata.
- **No knowledge graph, no concept map, no explicit typed relationships.** The link
  structure between documents is the graph, and it maintains itself. A formal graph
  needs updating in two places every time anything changes, which means it will be
  wrong within a month.
- **No dated folders.** Nothing here is named after 2026 or after a workshop that
  happens once. The workshop is a folder that links out; remove it and the repo still
  stands.
- **No one-folder-per-document.** A folder is justified when something has a diagram
  or more than one file. A lone `README.md` inside its own folder is a folder that
  earns nothing.
- **No exported PNGs.** `.drawio.svg` is both source and render.
- **No `docs/`, `notes/`, `images/`, `misc/`, `assets/`.** Those names describe file
  formats, not ideas, and they are where things go to be never found again.
- **No separate HLD and LLD trees.** Same system, two zoom levels, one place.

**Signals the structure has gone wrong — watch for these:**

| Signal | What it means |
|---|---|
| A new note has two plausible homes | Categories overlap. Merge them. |
| Folders with one file that has no diagram | Over-nested. Flatten. |
| `99-inbox/` growing and never draining | Promotion is too hard, or the inbox is being used as storage. |
| A directory `README.md` index that is out of date | It is doing work the file tree already does. Cut it back to links. |
| Hesitating before adding a note | **The most important signal.** Friction here means the structure is losing. Fix the structure, not your habits. |

**The test, whenever you are tempted to add structure:** does this make it easier to
*add* a note, or only easier to *admire* the repo? Only the first one counts.
