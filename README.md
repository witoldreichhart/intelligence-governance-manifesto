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
| [manifesto-principles.md](manifesto-principles.md) | Twelve principles plus four integrity preconditions, each with minimum bars: Intelligence Architecture (1-5), Intelligence Operations (6-12), Substrate-Integrity Preconditions (13-16) |
| [companion-guide.md](companion-guide.md) | Claim model, L1/L2/L3 memory spectrum, epistemic-tier ladder and thresholds, engagement archetypes, authority conflicts, boundary conditions |
| [implementation-guide.md](implementation-guide.md) | Five maturity levels, phased adoption, metrics, epistemic circuit breakers, decay triage, failure patterns |
| [glossary.md](glossary.md) | Term definitions as used in this framework |
| [positioning.md](positioning.md) | How intelligence governance differs from data governance, knowledge management, knowledge graphs, and RAG |
| [domains/financial-services.md](domains/financial-services.md) | Principle-by-principle mapping to FS regulations: EU AI Act, SR 11-7, DORA, MiFID II, BCBS 239, GDPR |
| [governance/queries.md](governance/queries.md) | 25 canonical governance queries across six concerns |

---

## Position in the agentic governance stack

The Intelligence Governance Manifesto (IGM) and the other manifestos in the agentic governance stack govern *different surfaces*, not different altitudes. The relationship is a **structural dependency, not a hierarchy** — IGM specifies the substrate of governed claims; AEnt-M specifies how agents coordinate over it; AEM, ASDLC, and APLC specify how the agents themselves are built, delivered, and operated. The dependency direction is explicit:

```
Agentic Engineering Manifesto (AEM)
   ├─ Agentic SDLC (ASDLC) — engineering-side governance of agent-built code
   ├─ Agentic Product Lifecycle (APLC) — product-side governance of agent behavior
   ├─ Intelligence Governance Manifesto (IGM) — substrate that agents reason over
   └─ Agentic Enterprise Manifesto (AEnt-M) — enterprise coordination of multiple agents on a shared substrate
       ├─ depends on IGM (substrate)
       └─ inherits AEM principles
```

What this means for IGM:

- **IGM inherits AEM principles.** AEM's twelve principles — outcomes, specifications, autonomy tiers, knowledge & memory (P6), evaluations (P8), accountability (P12) — apply to any system that builds, operates, or consumes a governed substrate. IGM specialises P6 and adds claim-level governance, lifecycle, and authority structure on top of the AEM contract; it does not replace it.
- **IGM is required by AEnt-M.** The Agentic Enterprise Manifesto coordinates *multiple* governed agents on a *shared* substrate. That substrate is what IGM defines. AEnt-M Principle 1 ("the domain graph is enterprise infrastructure") and Principle 5 ("agents share a substrate; they do not share a mind") are unbuildable without IGM.
- **IGM is standalone-usable when only one of the two sufficient conditions holds.** A single-team or single-agent context that needs governed claims, provenance, contradiction handling, and decay management can adopt IGM independently of AEnt-M — *if and only if* the consuming agents already operate inside an AEM-conformant engineering loop (or an equivalent declared substitute). IGM does not specify how agents are built or operated; that responsibility belongs to AEM, ASDLC, and APLC.
- **IGM and AEnt-M are connected by structural dependency, not by parity or altitude.** Earlier drafts framed the two as parallel companions; that framing is retired. AEnt-M depends on IGM (the substrate it coordinates over); IGM does not depend on AEnt-M. Neither sits above or below the other — they govern different surfaces.

See [`/agentic-governance-stack.md`](../agentic-governance-stack.md) for the canonical one-page stack reference, [`glossary.md`](glossary.md) and the repo-root `glossary.md` for term-collision resolution, and `governance/governance-integration-note.md` (DRAFT — author review needed) and `governance/authority-accountability-matrix.md` (DRAFT — author review needed) for the cross-stack integration artefacts.

---

## Status

Version 1.5 — May 2026. This is a living document. We welcome critical engagement.

## License

CC BY-SA 4.0
