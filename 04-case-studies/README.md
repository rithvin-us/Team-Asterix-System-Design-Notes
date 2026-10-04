# Case Studies

Whole systems, traced end to end through all five moves. Long, self-contained, with a
complete design record.

Not to be confused with [examples](../03-examples/), which illustrate a single point.

## By domain

| Domain | |
|---|---|
| [Automotive / robotics](automotive/) | Vehicles, ATVs, embedded, robotics |
| [Software](software/) | Backend, distributed, application systems |

## Structure

Each case study is a folder:

```
<system-slug>/
├── README.md          the whole study, following the template
└── diagrams/
    ├── <slug>-context.drawio.svg
    ├── <slug>-hld.drawio.svg
    └── <slug>-lld-<subject>.drawio.svg
```

Use **[_TEMPLATE.md](_TEMPLATE.md)** as the starting `README.md`. Open it on GitHub
and hit **Copy raw file** (top-right, next to Raw) to get the whole thing in one
click.

One `README.md` with sections, not nine subfolders. Nine subfolders per study means
nine mostly-empty folders per study, and the headings do the same job for free.

## Organised by domain, indexed by everything else

Folders are domain. Difficulty, architecture pattern and system type are **not**
folders — they go in the index tables inside each domain README. A file has one
location but can appear in several indexes, and that is the right way round.
