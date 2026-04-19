# The Intelligence Governance Manifesto

**Principles for governing the domain intelligence that AI systems depend on.**

*Authors: Witold Reichhart, Arnaud Gelas*
*Version: 1.1 — April 2026*

---

## Why This Manifesto

Domain intelligence in regulated industries is accidental, leaking, and missing.

Accidental — expertise exists only where we happened to win projects. Nobody decided to build settlement knowledge. It accreted as a side effect of delivery. Leaking — people exit and twenty years of operational judgment walks out. Projects dissolve and deep understanding scatters. Missing — entire domains where coverage is near zero despite high market demand.

This is not a new problem. Knowledge management has been working on it for decades — through structured content, communities of practice, semantic layers, and knowledge graphs. Much of that work produced real value. The best implementations already addressed governance, stewardship, decay monitoring, and structured decomposition.

What has changed is the forcing function. When AI agents enter regulated workflows, the intelligence they operate on becomes load-bearing infrastructure. An agent configuring a settlement system without governed domain intelligence is fast, fluent, and catastrophically incomplete. Speed without traceability is the actual risk — not hallucination.

Document repositories, retrieval systems, and knowledge graphs each solved part of the problem. None combined claim-level confidence, contradiction management, decay monitoring, and governance authority into an operational discipline. RAG improved recall but cannot tell you whether two retrieved passages contradict each other or what confidence to assign. Knowledge graphs structured relationships but most implementations were populated once and maintained rarely.

**This manifesto defines governed intelligence** — not as a replacement of prior work, but as the operational discipline these foundations require once AI agents consume institutional knowledge in regulated environments. Same ambition as knowledge management. Different engineering constraints. A new forcing function: machine consumption at speed, under regulatory scrutiny.

The core concepts — claims as a unit of governance, confidence scoring, provenance tracking, contradiction handling — have deep roots in knowledge management, social epistemology, structured content engineering, and semantic web traditions. The novelty is not the primitives. It is their combination into an operational governance model designed for a specific use case: AI agent consumption of institutional intelligence under regulatory constraint.

Most organisations already perform intelligence governance informally. SMEs interpret sources. Architects reconcile contradictions. Control functions judge reliability. The work exists — scattered across people, meetings, corridor conversations, and whoever happens to remember how things work. The shift is from implicit maintenance to explicit operations.

This manifesto defines the structure for that shift.

---

## Six Values

| We value more | | over what we also value |
|---|---|---|
| **Governed claims** | | Stored documents |
| **Traceable provenance** | | Trusted sources |
| **Preserved contradictions** | | Forced consensus |
| **Continuous curation** | | Periodic review |
| **Organisational reasoning capability** | | Individual expertise |
| **Domain-specific intelligence** | | General knowledge |

---

### Value 1 — Governed claims over stored documents

The unit of intelligence is not a document. It is a claim: a governed, confidence-scored, traceable assertion about how something works, scoped to a defined context. Documents bundle claims with noise, context, and formatting. Claim-level governance makes intelligence queryable, validatable, and composable.

A claim is the governable subset of institutional knowledge — what can be made explicit enough to review, challenge, scope, and use. Not all institutional knowledge can be reduced to claims without loss. Tacit judgment, situated expertise, and embodied know-how resist clean decomposition. The claim layer is a scaffold for what can be governed. Beyond it, human judgment remains irreducible — and the system must make that boundary visible.

### Value 2 — Traceable provenance over trusted sources

A claim's reliability comes from where it came from, how it was validated, when it was last challenged, and what corroborates it. Not from the reputation of whoever said it. Provenance includes acquisition mode, interpretive history, and the social process of challenge and acceptance. Trust is earned through the graph, not assumed at intake.

Provenance also serves integrity. In any system where AI agents act on institutional intelligence, the provenance chain must be verifiable — not just recorded, but resistant to manipulation.

### Value 3 — Preserved contradictions over forced consensus

In regulated environments, the gap between documented process and operational practice is where risk lives. A system that auto-resolves contradictions destroys information.

Not all conflicts are the same. The system must distinguish between genuine logical contradictions, jurisdictional divergences, temporal supersession, scope variations, and extraction errors. When UK CREST diverges from EU CSDR on settlement penalty calculations, this is a jurisdictional divergence — both positions are valid within their jurisdiction. A system that "resolves" this by choosing one has destroyed the information that a cross-border settlement programme must handle both regimes simultaneously.

In regulated workflows, material unresolved contradictions may require operational halt until human resolution — not just visibility, but action constraint.

### Value 4 — Continuous curation over periodic review

Knowledge decays. Regulations change. Operational reality drifts. A quarterly review discovers problems after they've caused damage. Continuous curation — decay detection, confidence monitoring, challenge mechanisms — keeps intelligence operationally current. Knowledge that isn't maintained isn't knowledge. It's a liability with a timestamp.

### Value 5 — Organisational reasoning capability over individual expertise

The goal is not to replace experts. It is to make their judgment durable, transferable, and challengeable. Experts remain essential — the system ensures their insights survive their tenure and can be reviewed by those who follow. Every organisation already runs an institutional reasoning function — interpreting sources, reconciling contradictions, deciding what is current, judging reliability. This work is currently implicit, scattered, and dependent on whoever happens to be in the room. Governed intelligence externalises institutional reasoning into an auditable architecture.

### Value 6 — Domain-specific intelligence over general knowledge

Generic AI knowledge is commodity. The operational intelligence that matters — what breaks at quarter-end, which workarounds hold under load, where jurisdictions conflict — is domain-specific and earned through years of delivery. RAG gives you recall. Governed domain intelligence gives you operational reasoning.

---

## The Intelligence Lifecycle

Intelligence follows a continuous lifecycle. Any system that treats these stages as sequential, or omits any one of them, is not performing intelligence governance — it is performing document management with extra steps.

**Ingest** → Populate the graph with claims from all authorised sources. Creates nodes.

**Consolidate** → Connect claims. Entity resolution, contradiction surfacing, relationship structure. Creates edges.

**Curate** → Maintain quality. Validate, promote, demote, manage contradictions, monitor decay. Maintains nodes and edges.

**Expand** → Generate claims the graph suggests should exist. Gap detection, cross-domain links, frontier expansion. Creates new nodes. Expand produces acquisition hypotheses and gap candidates — never operational claims. Every suggestion enters the standard validation pipeline. Nothing reaches operational use without human approval.

**Apply** → Deliver the relevant subgraph to a specific task. Confidence filtering, depth control, role-scoping. Observations feed back to Ingest. Extracts context.

Not sequential — concurrent. All five stages run continuously. Every engagement is both consumer and generator of intelligence. Usage reveals deficiency. The graph improves the more it is used.

---

## Intelligence Definition of Done

Eight criteria for a domain's intelligence to be operationally ready:

1. **Populated** — Claims ingested from all major source types (documentary, expert, operational)
2. **Connected** — Entity resolution complete, cross-domain links established, contradiction map current
3. **Validated** — Domain expert review complete, confidence tiers assigned, provenance verified
4. **Governed** — Four authorities assigned to named roles, decay monitoring active, revision workflow operational
5. **Applied** — At least one delivery engagement consuming intelligence with active feedback loop
6. **Traceable** — Every agent-consumed claim traceable from action to claim to source
7. **Accountable** — Governance roles staffed, authority boundaries documented, escalation paths defined
8. **Funded** — Ongoing curation capacity allocated, priced into the commercial model, and protected from delivery reallocation

---

## Failure Modes of This Manifesto

No framework is immune to misuse. These are the ways intelligence governance fails in practice:

**Intelligence theatre.** Claims are created but never curated. The graph grows but doesn't improve. Confidence tiers exist on paper but nobody challenges or updates them. The system looks governed but is actually static. *Symptom: high claim count, zero contradictions detected, zero confidence changes in 90 days.*

**Authority vacuum.** The four authorities are defined in a document nobody reads. No individual owns governance in practice. Claims are created by whoever is available and never reviewed. *Symptom: no claim promotions or retirements in a quarter.*

**Extraction without feedback.** Intelligence flows from the graph to engagements but observations never flow back. The graph becomes a one-way repository — a more expensive version of what it replaced. *Symptom: zero feedback events per engagement.*

**Decay denial.** The graph is treated as correct-once-built. No decay monitoring. Claims from three years ago carry the same confidence as claims from last week. *Symptom: no staleness alerts, no validity windows set.*

**Over-governance.** Every claim requires approval from multiple authorities. Curation overhead exceeds the value of the intelligence. The system is technically governed and practically unusable. *Symptom: curation backlog growing faster than delivery demand.*

**Capture fetishism.** Disproportionate investment in expert interviews while Harvest and Extract modes are underused. The most expensive acquisition mode becomes the default. *Symptom: >60% of claims originate from Capture, <10% from Harvest.*

**Epistemic monoculture.** The governed intelligence base becomes the institution's only recognised memory. Communities of practice, apprenticeship, and informal knowledge-sharing wither. Diverse ways of knowing collapse into whatever the claim schema can represent. *Symptom: experts consult the graph instead of each other; knowledge that doesn't fit the claim schema is treated as non-existent.*

**Adversarial compromise.** The intelligence base is treated as a trusted internal system without integrity controls. Claim injection, provenance spoofing, or confidence manipulation go undetected. *Symptom: no integrity verification on provenance chains; no anomaly detection on claim creation or promotion patterns.*

All of these failure modes have cultural preconditions. Governance architecture is necessary but not sufficient. The organisational playbook (companion document) addresses adoption, incentive design, and change management.

---

## Regulatory Alignment

This manifesto is designed for regulated industries. Its governance model maps to the Three Lines of Defence framework that supervisory authorities expect:

**First line** — domain teams operating assertion and semantic authority. They create, validate, and curate claims within their operational scope. Responsible for intelligence quality at the point of use.

**Second line** — revision authority and independent validation. Reviews confidence tiers, challenge history, contradiction resolution, and compliance of the intelligence base with regulatory requirements. Does not create claims — validates and challenges them.

**Third line** — external audit using the traceability chain. The provenance, confidence history, and decision logs produced by the governance model create the audit trail that third-line assurance requires.

The intelligence lifecycle produces supervisory observables: contradiction resolution activity, confidence tier movements, claim retirement rates, feedback loop metrics, and staleness alerts. Absence of these signals is itself a red flag.

---

## Connection to the Agentic Engineering Manifesto

This manifesto and the [Agentic Engineering Manifesto](https://github.com/arnaudgelas/agentic-engineering-manifesto) are companion documents by the same team.

| Concern | Agentic Engineering Manifesto | Intelligence Governance Manifesto |
|---|---|---|
| **Core question** | How do agents safely build software? | How do organisations govern the intelligence agents depend on? |
| **Governs** | Agent behaviour — permissions, verification, containment | Domain intelligence — claims, confidence, provenance, decay |
| **Unit of work** | Verified outcome | Governed claim |
| **Operational loop** | Specify → Plan → Execute → Verify → Observe → Learn → Govern | Ingest → Consolidate → Curate → Expand → Apply |
| **Maturity model** | Six engineering phases | L1 → L2 → L3 memory spectrum |
| **Governance** | Autonomy tiers, blast radius, defence-in-depth | Four authorities, confidence tiers, contradiction management |
| **Definition of Done** | Shipped, Observable, Verified, Provable, Learned from, Governed, Economical | Populated, Connected, Validated, Governed, Applied, Traceable, Accountable, Funded |
| **Economics** | Total cost of correctness | No unfunded mandates |
| **Self-critique** | Over-governance, evidence theatre, maturity inflation | Intelligence theatre, authority vacuum, decay denial |

**The bridge:** The Agentic Engineering Manifesto's Principle 6 declares that "knowledge and memory are distinct infrastructure" that requires governance. This manifesto is the architecture behind that declaration — defining what intelligence infrastructure is, how to build it, how to govern it, and what organisational structure sustains it.

The accountability chain: the Agentic Engineering Manifesto traces an agent's action to the specification that authorised it. This manifesto traces it further — from the specification to the domain intelligence that informed it. Together: a complete, auditable chain from what the agent did, through the constraint that allowed it, to the knowledge that justified it.

Neither manifesto is incomplete without the other. But together they form the full stack for deploying AI safely in regulated environments.

---

*Companion guide and organisational playbook in development. See [manifesto-principles.md](manifesto-principles.md) for the twelve principles with minimum bars.*

---

## Revision Log (v1.0 → v1.1)

| Change | Driven by | Classification |
|---|---|---|
| Rewrote "Why This Manifesto" — acknowledged KM lineage, reframed as evolution under new forcing function | SW-1: KM Veteran, Consulting Competitor, Devil's Advocate (straw man critique) | Structural weakness |
| Added claim boundary in Value 1 — explicit that claims are the governable subset, tacit knowledge lies outside | SW-3: Epistemologist, KM Veteran, AI Safety, Epistemologist Rewrite (tacit knowledge / context collapse) | Structural weakness |
| Added contradiction taxonomy in Value 3 — types of conflict, jurisdictional divergence example relabeled | IC-3: Epistemologist, Devil's Advocate (contradiction terminology wrong) | Important consideration |
| Added halt condition language in Value 3 — material contradictions in regulated workflows may require operational halt | PB: Regulator Rewrite (contradictions as stop conditions) | Rewrite insight |
| Strengthened Value 5 — experts remain essential, system ensures insights survive tenure | MR-1: Epistemologist (misread as "replaces experts") | Misreading fix |
| Added provenance integrity note in Value 2 | SW-5: Compliance/Regulatory, AI Safety (missing security treatment) | Structural weakness |
| Strengthened Expand description — hypotheses not claims, human approval required | IC-2: AI Safety, Devil's Advocate (Emerge is dangerous) | Important consideration |
| Added "Epistemic monoculture" failure mode | IC-6: AI Safety, Epistemologist Rewrite | Important consideration |
| Added "Adversarial compromise" failure mode | SW-5: Compliance/Regulatory, AI Safety, Full Rewrite | Structural weakness |
| Added cultural preconditions note to failure modes | IC-5: KM Veteran, Pragmatic CTO (can't architect your way out) | Important consideration |
| Added "Regulatory Alignment" section with 3LoD mapping | SW-6: Compliance/Regulatory, Full Rewrite, Regulator Rewrite | Structural weakness |
