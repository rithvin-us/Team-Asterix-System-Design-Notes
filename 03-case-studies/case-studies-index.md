# Case Studies

Whole systems traced end to end through all five moves. Long, self-contained, with a
complete design record.

| | |
|---|---|
| 🛠 **[How to draw a system](how-to-draw-a-system.md)** | The six-pass method. Read this before studying anything. |
| 📚 **[Reference architectures](reference-architectures.md)** | Real systems with public sources — Autoware, Apollo, ROS 2, CAN/AUTOSAR, Netflix, Uber, Discord, the classic papers |
| 📊 **[HLD Scorecard](https://claude.ai/artifact/2tr1jH6Zyyt6LCDXTPfsGR)** | Paste your design and have it scored, or count the six metrics yourself |
| 📝 **[Case study template](case-study-template.md)** | The structure every study here follows |

---

## Written up here

| System | Domain | Difficulty | Teaches |
|---|---|---|---|
| **[Autoware](autoware/autoware.md)** | Automotive | Intermediate | Boundaries, stating what you exclude, an architecture rewrite and why |
| **[Netflix](netflix-streaming/netflix-streaming.md)** | Software | Intermediate | Control vs data flow as separate systems, a published failure mode |

Both were written with [the six-pass method](how-to-draw-a-system.md) against primary
sources, and both cite them. A case study with no primary source is a rumour.

## Good candidates

**Vehicles and robotics** — Autoware perception pipeline · PX4 flight stack ·
a CAN bus network on a real vehicle · ROS 2 node graph for a rover ·
vehicle diagnostics over UDS · a sensor fusion pipeline

**Software** — a chat application · ride-sharing dispatch · a video platform ·
URL shortener (the classic starter) · notification delivery · a robot fleet
coordinator, which spans both domains and is the most interesting of these

---

## Structure

Each case study is a folder:

```
<system-slug>/
├── <system-slug>.md       the study, following the template
└── diagrams/
    ├── <slug>-context.drawio.svg
    ├── <slug>-hld.drawio.svg
    └── <slug>-lld-<subject>.drawio.svg
```

Name the write-up after the system, not `README.md` — see
[the naming convention](../CONVENTIONS.md#file-naming).

Start from [`case-study-template.md`](case-study-template.md): open it on GitHub and
hit **Copy raw file**, top-right.

One file with sections, not nine subfolders. Nine subfolders per study gives you nine
mostly-empty folders per study, and headings do the same job for free.

---

## Organised by nothing, indexed by everything

There are **no domain subfolders**. Automotive and software studies sit side by side,
because they are the same five moves with different nouns.

Difficulty, domain and architectural pattern are **columns in the table above**, not
folders. A study has one location but can appear in as many indexes as you like, and
that is the right way round.
