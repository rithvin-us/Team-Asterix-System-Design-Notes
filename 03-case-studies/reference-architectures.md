# Reference Architectures — Real Systems, Public Sources

Where to read how real systems are actually built, written by the people who built
them.

**Why a link list and not write-ups?** Because a summary of an architecture is worth
far less than the original, and because a confident-sounding summary of a system
nobody here has seen is exactly the failure mode described in
[when AI is wrong](../06-workshop/ai-prompts/when-ai-is-wrong.md). Everything below is
a primary source. Read it, then write your own analysis using
[the case study template](case-study-template.md) — that analysis is worth keeping;
a paraphrase is not.

> **Honest note on ATV manufacturers.** Polaris, Can-Am, Yamaha and Arctic Cat do not
> publish their internal vehicle architectures. Anything claiming to show one in
> detail is reconstructed or invented. What *is* public: the standards they build on,
> and complete open-source vehicle stacks. Those are listed below and they teach the
> same lessons.

---

## 🚗 Vehicles, robotics and embedded

### Complete open architectures — the best things on this page

| System | What it is | Why study it |
|---|---|---|
| **[Autoware](https://autoware.org/)** | Open-source autonomous driving stack | A full, real, documented AV architecture — sensing, perception, planning, control. Every module boundary is public. |
| **[Apollo](https://github.com/ApolloAuto/apollo)** | Baidu's open autonomous driving platform | Complete system with published architecture docs. Shows how perception, prediction and planning are separated. |
| **[ROS 2 design docs](https://design.ros2.org/)** | The reasoning behind ROS 2 | Rare and valuable: documents **why** the architecture is as it is, including rejected options. Exactly what a trade-off section should look like. |
| **[PX4](https://docs.px4.io/main/en/concept/architecture.html)** | Flight control stack | Clean, readable module/interface decomposition for a safety-critical real-time system. |
| **[ArduPilot](https://ardupilot.org/dev/docs/learn-about-ardupilot.html)** | Autopilot for many vehicle types | Shows one architecture stretched across planes, rovers and boats — a lesson in where abstraction pays and where it hurts. |

### Standards — how vehicles actually talk

| Standard | Covers |
|---|---|
| **[CAN bus](https://www.bosch-semiconductors.com/)** (Bosch) | The bus almost every vehicle uses. Learn arbitration and why message IDs carry priority. |
| **SAE J1939** | Higher-layer protocol over CAN for heavy vehicles. A real, documented interface spec. |
| **[AUTOSAR](https://www.autosar.org/)** | The layered architecture standard behind most production ECUs. Heavy, but it is the real thing. |
| **ISO 26262** | Functional safety for road vehicles. Where safety requirements come from. |
| **[OBD-II / UDS](https://en.wikipedia.org/wiki/Unified_Diagnostic_Services)** | Vehicle diagnostics. A good small interface to study end to end. |

### Hardware platforms

- **[NVIDIA Jetson documentation](https://developer.nvidia.com/embedded/jetson-modules)** — real power budgets, thermal limits and I/O constraints. The numbers you need for an honest design.
- **[OpenXC](http://openxcplatform.com/)** (Ford) — open vehicle data platform. A manufacturer-published vehicle interface.

### Student competitions

- **[BAJA SAE](https://www.bajasae.net/)** / **[SAE India](https://www.saeindia.org/)** — rules documents are effectively a requirements and constraints specification. Read one as a system design artifact; it is the closest public thing to what Asterix actually builds.
- **[Formula Student Germany](https://www.formulastudent.de/)** — publishes rules and many teams publish design reports.

---

## 💻 Software and distributed systems

### Engineering blogs — architectures by the people who built them

| Source | Known for |
|---|---|
| **[Netflix Tech Blog](https://netflixtechblog.com/)** | Streaming at scale, chaos engineering, resilience. The canonical source on designing for failure. |
| **[Uber Engineering](https://www.uber.com/en-US/blog/engineering/)** | Real-time dispatch, geospatial systems, a documented monolith-to-microservices migration. |
| **[Discord Blog](https://discord.com/blog/)** | Famously clear write-ups on scaling messaging and storage. Unusually honest about what went wrong. |
| **[Cloudflare Blog](https://blog.cloudflare.com/)** | Networking, edge systems, and excellent incident post-mortems. |
| **[Dropbox Tech](https://dropbox.tech/)** | Storage systems, and the rare case of migrating *off* the cloud, with numbers. |
| **[Stripe Blog](https://stripe.com/blog/engineering)** | API design, idempotency, correctness under money constraints. |
| **[Meta Engineering](https://engineering.fb.com/)** | Very large scale storage, caching and networking. |
| **[AWS Architecture Center](https://aws.amazon.com/architecture/)** | Reference architectures with diagrams, plus the Well-Architected Framework. |
| **[Google SRE Books](https://sre.google/books/)** | Free, full books on running systems in production. |

### Papers worth reading once

| Paper | Idea |
|---|---|
| **Dynamo** (Amazon, 2007) | Availability over consistency — a trade-off made explicitly, and the paper says what it cost. |
| **MapReduce** (Google, 2004) | A hard problem made simple by choosing the right abstraction. |
| **Bigtable** / **Spanner** (Google) | Data models and the consistency ladder. |
| **Raft** (2014) | Consensus, written specifically to be understandable. |

### Collections

- **[The System Design Primer](https://github.com/donnemartin/system-design-primer)** — the most-used free resource for software system design. Start here if the software side is new.
- **[High Scalability](http://highscalability.com/)** — architecture breakdowns of named companies.
- **[ByteByteGo](https://blog.bytebytego.com/)** — clear diagrams, good for seeing how others draw systems.

---

## How to actually use this page

Reading architectures passively teaches very little. Do this instead:

1. **Pick one** system from above.
2. **Read the primary source** — the blog post, the design doc, the paper.
3. **Draw its HLD yourself** from the
   [starter template](../02-concepts/diagrams/starter-template.drawio.svg). Do not
   copy their diagram; draw what you understood.
4. **Fill in [the case study template](case-study-template.md)** — especially the
   **trade-offs** section. Find the decision they made and the option they rejected.
5. **Find the gap.** Every public architecture leaves something out. What did they not
   tell you, and why might that be?

Step 5 is where the learning is. Step 3 is where you find out whether you actually
understood it.

---

## Contributing one

Finish steps 1–5 above, save it as a folder under `03-case-studies/`, and add a row to
[the index](case-studies-index.md). Cite the source you read at the top — a case study
with no primary source is a rumour.
