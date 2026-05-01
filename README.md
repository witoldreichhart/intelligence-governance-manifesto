# Intelligence Governance Manifesto

**Principles for governing the domain intelligence that AI systems depend on.**

*Authors: **[Witold Reichhart](https://github.com/witoldreichhart) and [Arnaud Gelas](https://github.com/arnaudgelas)***

---

## What this is

A manifesto for intelligence governance in regulated industries.

When AI agents enter regulated workflows, the domain intelligence they operate on becomes load-bearing infrastructure. An agent configuring a settlement system without governed domain intelligence is fast, fluent, and catastrophically incomplete.

Most organisations already perform intelligence governance informally — experts interpret sources, architects reconcile contradictions, control functions judge reliability. The work exists. The structure doesn't.

This manifesto defines the structure.

---

## Six values

| We value more | | over what we also value |
|---|---|---|
| **Governed claims** | | Stored documents |
| **Traceable provenance** | | Trusted sources |
| **Preserved contradictions** | | Forced consensus |
| **Continuous curation** | | Periodic review |
| **Organisational reasoning capability** | | Individual expertise |
| **Domain-specific intelligence** | | General knowledge |

---

## Reading guide

| Document | What it covers |
|---|---|
| [manifesto.md](manifesto.md) | Core manifesto: why this exists, six values, intelligence lifecycle, governance relocation, domain graph, definition of done, failure modes |
| [manifesto-principles.md](manifesto-principles.md) | Twelve principles with minimum bars: Intelligence Architecture (1-5) and Intelligence Operations (6-12) |
| [companion-guide.md](companion-guide.md) | Claim model, L1/L2/L3 memory spectrum, confidence levels and thresholds, engagement archetypes, authority conflicts, boundary conditions |
| [implementation-guide.md](implementation-guide.md) | Five maturity levels, phased adoption, metrics, epistemic circuit breakers, decay triage, failure patterns |
| [glossary.md](glossary.md) | Term definitions as used in this framework |
| [positioning.md](positioning.md) | How intelligence governance differs from data governance, knowledge management, knowledge graphs, and RAG |
| [domains/financial-services.md](domains/financial-services.md) | Principle-by-principle mapping to FS regulations: EU AI Act, SR 11-7, DORA, MiFID II, BCBS 239, GDPR |
| [governance/queries.md](governance/queries.md) | 25 canonical governance queries across six concerns |

---

## The governance stack

This manifesto governs the intelligence layer — what agents know. It sits within a five-layer governance architecture:

| Layer | Governs | Source |
|---|---|---|
| **Engineering** | How human-agent loops build software | [Agentic Engineering Manifesto](https://github.com/arnaudgelas/agentic-engineering-manifesto) (Gelas) |
| **Delivery** | How agent-built software reaches production | [ASDLC](https://github.com/arnaudgelas/asdlc) (Gelas) |
| **Product** | How agent products behave in production | [APLC](https://github.com/arnaudgelas/aplc) (Gelas) |
| **Intelligence** | What agents know and how knowledge is maintained | **This repo** (Reichhart and Gelas) |
| **Enterprise** | How governed agents on governed intelligence produce institutional value | [Agentic Enterprise Manifesto](https://github.com/witoldreichhart/agentic-enterprise-manifesto) (Reichhart and Gelas) |

Each layer is necessary. None is sufficient alone.

---

## Status

Version 1.2 — May 2026. This is a living document. We welcome critical engagement.

## License

CC BY-SA 4.0
