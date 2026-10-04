# Projects

Substantial builds with a full design record. Days to weeks, open-ended.

Shorter practice goes in [05-exercises](../05-exercises/).

## Index

| Project | Status | Domain |
|---|---|---|
| _none yet_ | | |

## Structure

Each project is a folder:

```
<project-slug>/
├── README.md          the design record, following the template
└── diagrams/
    ├── <slug>-context.drawio.svg
    ├── <slug>-hld.drawio.svg
    └── <slug>-lld-<subject>.drawio.svg
```

Start from **[`_TEMPLATE/`](_TEMPLATE/)**.

### Why one file and not nine folders

A design record has nine parts — problem, requirements, assumptions, HLD, LLD,
implementation, testing, trade-offs, retrospective. Those are **nine headings in one
`README.md`**, not nine directories.

Nine directories per project gives you nine mostly-empty directories per project, a
navigation cost on every read, and no benefit — a heading is linkable, greppable and
visible in one scroll. The only thing that earns its own folder is `diagrams/`,
because it holds binaries-in-spirit and there are several of them.

## The part that matters most

The **retrospective** and the **change log**.

A project with a clean design and no record of what changed is a project where you
either got lucky or quietly fixed things without noticing what they cost. The record
of what broke, what you missed, and what you would cut differently is the part that
makes the project worth keeping — and the part that is interesting to anyone reading
it later.
