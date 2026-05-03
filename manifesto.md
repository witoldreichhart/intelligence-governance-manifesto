# The Intelligence Governance Manifesto

**Principles for governing the domain intelligence that AI systems depend on.**

*Authors: **[Witold Reichhart](https://github.com/witoldreichhart) and [Arnaud Gelas](https://github.com/arnaudgelas)***
*Version: 1.4 — May 2026*

> **Terminology note (v1.4).** Supersedes v1.3's "rename confidence → epistemic tier." The IGM uses three terms with a clean division of labour: **confidence** (human-facing presentation-layer term — decks, dashboards, informal scoring), **epistemic tier** (formal governance term for the four discrete evidence levels: **Provisional → Emerging → Validated → Foundational**, mapped 1:1 to consequence classes), and **epistemic quality** (composite assessment of a reasoning chain, surfaced at decision time). Tier names always pair with "epistemic tier" — never with "confidence". The four-tier ladder is a clean break from the v1.0–v1.3 five-tier vocabulary (Provisional → Candidate → Confirmed → High Confidence → Authoritative). See [manifesto-principles.md](manifesto-principles.md) for the full note and the unified glossary's term-collision appendix for cross-version mappings.

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

## Intelligence, Not Knowledge

A governed knowledge graph is not intelligent. It is the substrate from which intelligence can be exercised. The distinction matters because it determines what the lifecycle produces and what agents can do with it.

**Knowledge** is structured content: validated claims, causal relations, provenance, confidence, temporal validity, scope, and governance status. Knowledge is what the system holds.

**Organizational intelligence** is the system-level capacity to perceive institutionally relevant patterns, infer their consequences, and select or recommend action opportunities aligned with organizational purpose under changing constraints. Intelligence is not a property of the model alone. It is a property of the agent-substrate system — the interaction between inferential capability, governed knowledge, and the institutional constraints that define what "aligned" means.

**Governed intelligence** is what emerges when AI capability operates over knowledge that is current, contextual, connected, validated, scoped, auditable, and capable of learning from use. It is the capacity of the institution — not the model — to reason and act reliably.

This hierarchy prevents two errors. The first is treating knowledge infrastructure as intelligence — building a graph and calling it done. The second is treating model capability as organizational intelligence — deploying capable models without governed domain knowledge and expecting institutional judgment.

The intelligence lifecycle specified below maintains the substrate. What agents do with that substrate — from executing assigned tasks (autonomy) to surfacing action opportunities aligned with institutional purpose before being asked (initiative) — depends on the depth, fertility, and governance integrity of what the lifecycle produces. Shallow substrate supports autonomy. Deep, governed, continuously enriched substrate supports initiative. The manifesto governs the substrate. What emerges on top is determined by how well the substrate is built and maintained.

### Which layer are you governing?

The IGM uses two layering schemes that readers sometimes conflate. They are orthogonal and both are needed.

The **three-level hierarchy** above (*Knowledge → Organizational Intelligence → Governed Intelligence*) describes **what is being produced**: structured content, the institutional capacity to reason over it, the capacity that emerges when capable models operate over governed knowledge. It is an external lens — what the institution offers to the world.

The **L1 / L2 / L3 memory layers** (specified in `manifesto-principles.md` Principle 9) describe **where intelligence physically lives** at decision time: working memory loaded for an action (L1), the curated domain graph (L2), the foundational structural knowledge that rarely changes (L3). It is an internal lens — what the system holds and where.

| If your governance question is about… | …you are governing this layer | Primary controls |
|---|---|---|
| Whether the institution can reason and act reliably | Governed intelligence (the outcome) | All twelve principles plus the four integrity preconditions operating in concert; governance relocation is the emergent indicator |
| Whether the institution can perceive patterns and select action opportunities | Organizational intelligence (the capacity) | Principles 8, 9, 10, 13, 16; substrate depth, fertility, validation events |
| Whether structured claims with provenance, tier, scope are present | Knowledge (the content) | Principles 1, 2, 3, 4, 5, 7; the intelligence lifecycle on L2 |
| What the agent or practitioner has loaded right now | L1 (working memory) | Scope-match enforcement, freshness gates, tier floors, contradiction surfacing |
| What the institution has curated and connected | L2 (institutional memory) | The full intelligence lifecycle; epistemic debt is the L2 health metric |
| What rarely changes but cascades when it does | L3 (foundational intelligence) | Change detection with cascade analysis; human-reviewed L3 revalidation |

A useful rule of thumb: the *three-level hierarchy* answers the question "what does this manifesto produce?"; the *L1/L2/L3 layers* answer the question "where does the next decision come from?". The lifecycle and the principles operate at L2 (and detect L3 changes); agents act on L1 assembled from L2; what emerges from this — when relocation has occurred — is governed intelligence.

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

**Preserve always; halt action conditionally.** Contradictions are always preserved as first-class objects — never silently overwritten. Whether a contradiction additionally *halts action* is a separate, narrower decision: action is halted when the contradiction is **material** to the action being taken **and** the action's consequence class is **High or Critical** (per the epistemic-circuit-breaker spec in `manifesto-principles.md` Principle 11). Material contradictions on Low or Medium-consequence actions surface as warnings; immaterial contradictions (out-of-scope, superseded, extraction-error pending review) do not gate action at all. Preservation is universal; halting is consequence-class-gated.

When an agent's reasoning chain encounters a contradiction at runtime, the response is governed by the canonical decision tree in [`/integration/contradiction-handling-decision-tree.md`](../integration/contradiction-handling-decision-tree.md), which maps `contradiction-type × consequence-class × claim-tier` to a response class (Block / Escalate / Restrict scope / Advisory only / Continue with enhanced monitoring) per AEnt-M Principle 11. The substrate's preservation of the contradiction (this Value) is unchanged by the runtime response — IGM preserves; the decision tree determines what the agent does with what is preserved.

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

**Curate** → Maintain quality. Validate, promote, demote, manage contradictions, monitor decay. Maintains nodes and edges. This is the immune function — the stage that defends the substrate against the six failure modes of epistemic degradation: pollution, staleness, fragmentation, amnesia, cascade failure, and structural distortion.

**Expand** → Generate claims the graph suggests should exist. Gap detection, cross-domain links, frontier expansion. Creates new nodes. Expand produces acquisition hypotheses and gap candidates — never operational claims. Every suggestion enters the standard validation pipeline. Nothing reaches operational use without human approval.

**Apply** → Deliver the relevant subgraph to a specific task. Epistemic-tier filtering, depth control, role-scoping. Observations feed back to Ingest. Extracts context.

Not sequential — concurrent. All five stages run continuously. Every engagement is both consumer and generator of intelligence. Usage reveals deficiency. The graph improves the more it is used.

### Governance relocation

The lifecycle does more than maintain knowledge quality. As the substrate deepens — more validated claims, richer causal connections, more cross-domain edges — something structural changes in how governance operates.

At low substrate depth, governance is external friction: explicit pre-action constraint checking, human approval for every agent action, hard boundaries enforced before anything happens. As the substrate deepens, the causal rationale those constraints protect becomes structurally represented in the graph itself. An agent reasoning over a deep, well-governed substrate encounters the consequence structure that governance was encoding — during normal reasoning, not as a separate compliance check.

Governance does not disappear. Its enforcement locus migrates from synchronous pre-action gating to the substrate's own causal architecture. Explicit checks shift from universal requirement to risk-based monitoring and audit sampling — per action class, measurably, reversibly. If the substrate degrades, governance re-tightens for affected action classes.

This is governance relocation — the operational locus shifting from external rules to substrate-resident structure. It is the mechanism that converts a governed knowledge base into a substrate for institutional initiative. And it is measurable: declining governance intervention rates with stable or improving decision quality indicate relocation. Flat or rising rates indicate insufficient substrate depth.

The specific quantitative signals — leading indicators (provenance completeness, claims-within-revalidation-window, contradictions-with-assigned-review, authority assignment, feedback-loop completion), lagging indicators (epistemic-debt ratio, circuit-breaker activation trend, governance interventions per 1,000 agent actions, time-to-revalidate, scope-mismatch incidents), and the inverse-indicator framing of circuit-breaker frequency — are specified in `implementation-guide.md` ("Metrics") and `manifesto-principles.md` Principle 11. For the regulated-industry mapping (CSDR / DORA / EU AI Act / MiFID II) of these signals onto first-, second-, and third-line oversight, see `domains/financial-services.md`.

---

## The Domain Graph

The intelligence lifecycle maintains knowledge. But knowledge at which level?

Foundation models provide broad pattern density at low domain specificity. Application context provides high specificity at low pattern density. Neither crosses the depth threshold required for domain-specific institutional intelligence in regulated industries.

The domain graph sits between them — the missing middle layer. Accumulated, governed, reusable domain substrate that no single client owns but every client needs. How SWIFT message types relate to settlement workflows. How Basel III capital requirements cascade through product hierarchies. How operational workarounds interact with control frameworks. This is knowledge that any experienced practitioner carries but that no current AI system possesses as structured, validated, traversable intelligence.

The domain graph satisfies four properties:

**Scope** — domain-specific knowledge between public domain (regulations, standards) and client-walled (engagement-specific). The shared institutional substrate.

**Provenance** — every claim carries source, validation status, epistemic tier, temporal validity, and named authority. Governed L3 knowledge, not accumulated reference material.

**Compounding** — each engagement that operates on the domain graph enriches it. Gaps identified, claims validated against operational reality, cross-domain edges discovered. The graph grows by generation — each use producing new connections — rather than by accumulation alone. This is fertility: the rate at which existing knowledge generates new knowledge through operation.

**Decay management** — different knowledge types decay at different rates. The Curate process runs different maintenance cadences per decay class.

The domain graph matters for intelligence governance because it is the substrate the lifecycle maintains. Without it, the lifecycle maintains scattered engagement-specific knowledge that never compounds. With it, the lifecycle maintains shared institutional intelligence that deepens through every engagement.

The competitive implication is worth noting. Capability commoditises as foundation models converge. The domain graph does not commoditise because it compounds through governed operation. A competitor can replicate the schema. They cannot purchase the generative history.

---

## Intelligence Definition of Done

Eight criteria for a domain's intelligence to be operationally ready:

1. **Populated** — Claims ingested from all major source types (documentary, expert, operational)
2. **Connected** — Entity resolution complete, cross-domain links established, contradiction map current
3. **Validated** *(domain-level criterion; distinct from the Validated epistemic tier — see glossary)* — Domain expert review complete, epistemic tiers assigned across the domain's claims, provenance verified
4. **Governed** — Four authorities assigned to named roles, decay monitoring active, revision workflow operational
5. **Applied** — At least one delivery engagement consuming intelligence with active feedback loop
6. **Traceable** — Every agent-consumed claim traceable from action to claim to source
7. **Accountable** — Governance roles staffed, authority boundaries documented, escalation paths defined
8. **Funded** — Ongoing curation capacity allocated, priced into the commercial model, and protected from delivery reallocation

---

## Substrate Integrity — Four Integrity Preconditions (v1.3)

Beyond the twelve principles that describe what the substrate looks like and how to run it, four **integrity preconditions** address what protects the substrate once it is treated as load-bearing infrastructure for AI agents. They are numbered Principles 13–16 for stable cross-reference, but they are preconditions in role: an IGM substrate cannot be claimed operational without them. These are stated in full in [manifesto-principles.md](manifesto-principles.md); the short form is:

**Principle 13 — Claims must be validatable, not only corroborated.** Multiple sources agreeing is necessary but insufficient. Promotion to the **Validated** epistemic tier requires a recorded *validation event* against an observable reality not used as a corroborating source — regulatory text for regulatory claims, system behaviour for operational claims, transaction data for procedural claims. This wires IGM to AEM Principle 8 (*Evaluations are the contract*) and prevents *confidence laundering* — high epistemic tier earned by stacking weak corroboration.

**Principle 14 — Claims are attack surfaces.** The substrate is a high-value asset and must be threat-modelled. Threats include claim poisoning, provenance spoofing, tier manipulation, indirect prompt injection in Ingest, contradiction injection, and insider tampering by authority-holders. Mitigations include cryptographic provenance signatures, write-path access controls separated from read-path, integrity monitoring, quarterly red-team of the graph itself, and a **substrate-security function reporting through an independent CISO (or equivalent) line — not a fifth governance authority** — with operational override during integrity incidents. This wires IGM to AEM Principle 10 (*Assume emergence; engineer containment*) for adversarial failure.

**Principle 15 — Architectural enforcement is assumed, not provided.** IGM governs the knowledge layer. Architectural defense-in-depth — machine-enforced policies, repository gates, type contracts, lint rules, domain ownership maps, CI checks, runtime sandboxes — is delegated to AEM Principle 3. A perfectly governed knowledge base on an architecturally unprotected system is a liability. IGM operational readiness requires evidence that AEM Principle 3 is implemented for the consuming system.

**Principle 16 — Containment is required for substrate-driven emergence.** Multi-agent systems reading and writing the same substrate produce emergent behaviour that no single agent's design accounts for: feedback loops, cascading promotions, self-corroborating false claims, contradiction churn. Containment requires rate limits on tier promotions per source per window, detection of self-corroboration cycles, circuit breakers on cascading retirements, and an audit trail of which agents touched which claims. This wires IGM to AEM Principle 10 for emergent failure in the knowledge layer.

---

## Failure Modes of This Manifesto

No framework is immune to misuse. These are the ways intelligence governance fails in practice:

**Intelligence theatre.** Claims are created but never curated. The graph grows but doesn't improve. Epistemic tiers exist on paper but nobody challenges or updates them. The system looks governed but is actually static. *Symptom: high claim count, zero contradictions detected, zero epistemic-tier changes in 90 days.*

**Authority vacuum.** The four authorities are defined in a document nobody reads. No individual owns governance in practice. Claims are created by whoever is available and never reviewed. *Symptom: no claim promotions or retirements in a quarter.*

**Extraction without feedback.** Intelligence flows from the graph to engagements but observations never flow back. The graph becomes a one-way repository — a more expensive version of what it replaced. *Symptom: zero feedback events per engagement.*

**Decay denial.** The graph is treated as correct-once-built. No decay monitoring. Claims from three years ago carry the same epistemic tier as claims from last week. *Symptom: no staleness alerts, no validity windows set.*

**Over-governance.** Every claim requires approval from multiple authorities. Curation overhead exceeds the value of the intelligence. The system is technically governed and practically unusable. *Symptom: curation backlog growing faster than delivery demand.*

**Capture fetishism.** Disproportionate investment in expert interviews while Harvest and Extract modes are underused. The most expensive acquisition mode becomes the default. *Symptom: >60% of claims originate from Capture, <10% from Harvest.*

**Epistemic monoculture.** The governed intelligence base becomes the institution's only recognised memory. Communities of practice, apprenticeship, and informal knowledge-sharing wither. Diverse ways of knowing collapse into whatever the claim schema can represent. *Symptom: experts consult the graph instead of each other; knowledge that doesn't fit the claim schema is treated as non-existent.*

**Adversarial compromise.** The intelligence base is treated as a trusted internal system without integrity controls. Claim injection, provenance spoofing, or epistemic-tier manipulation go undetected. *Symptom: no integrity verification on provenance chains; no anomaly detection on claim creation or promotion patterns.*

All of these failure modes have cultural preconditions. Governance architecture is necessary but not sufficient. The organisational playbook (companion document) addresses adoption, incentive design, and change management.

---

## Regulatory Alignment

This manifesto is designed for regulated industries. Its governance model maps to the Three Lines of Defence framework that supervisory authorities expect:

**First line** — domain teams operating assertion and semantic authority. They create, validate, and curate claims within their operational scope. Responsible for intelligence quality at the point of use.

**Second line** — revision authority and independent validation. Reviews epistemic tiers, challenge history, contradiction resolution, and compliance of the intelligence base with regulatory requirements. Does not create claims — validates and challenges them.

**Third line** — external audit using the traceability chain. The provenance, epistemic-tier history (the audit-trail formal name for what is colloquially called "confidence history"), and decision logs produced by the governance model create the audit trail that third-line assurance requires.

The intelligence lifecycle produces supervisory observables: contradiction resolution activity, epistemic-tier movements, claim retirement rates, feedback loop metrics, and staleness alerts. Absence of these signals is itself a red flag.

---

## Connection to the Agentic Governance Stack

This manifesto governs the intelligence substrate — what agents know. The agentic governance stack is a set of manifestos governing *different surfaces* — engineering loop (AEM), delivery pipeline (ASDLC), individual product behaviour (APLC), substrate of governed claims (IGM), enterprise coordination (AEnt-M). They are connected by **structural dependency, not by hierarchy**. The explicit dependency direction is:

```
Agentic Engineering Manifesto (AEM)
   ├─ Agentic SDLC (ASDLC) — engineering-side governance of agent-built code
   ├─ Agentic Product Lifecycle (APLC) — product-side governance of agent behavior
   ├─ Intelligence Governance Manifesto (IGM) — substrate that agents reason over
   └─ Agentic Enterprise Manifesto (AEnt-M) — enterprise coordination of multiple agents on a shared substrate
       ├─ depends on IGM (substrate)
       └─ inherits AEM principles
```

This diagram is the canonical statement of the relationship. It supersedes any earlier "complementary" or "companion" framing in the IGM document set. See [`/agentic-governance-stack.md`](../agentic-governance-stack.md) for the canonical one-page reference.

The layered relationship in narrative form:

| Layer | Scope | Governs | Source |
|---|---|---|---|
| **Engineering (AEM)** | How human-agent loops build software | The engineering process | [Agentic Engineering Manifesto](https://github.com/arnaudgelas/agentic-engineering-manifesto) (Gelas) |
| **Delivery (ASDLC)** | How agent-built software reaches production | The delivery pipeline | [ASDLC](https://github.com/arnaudgelas/asdlc) (Gelas) |
| **Product (APLC)** | How agent products behave in production | Individual agent behavior | [APLC](https://github.com/arnaudgelas/aplc) (Gelas) |
| **Intelligence (IGM)** | What agents know and how knowledge is maintained | The shared substrate | This manifesto (Reichhart and Gelas) |
| **Enterprise (AEnt-M)** | How governed agents on governed intelligence produce institutional value | The organization | [Agentic Enterprise Manifesto](https://github.com/witoldreichhart/agentic-enterprise-manifesto) (Reichhart and Gelas) |

IGM inherits AEM principles (the substrate-building loop is itself an agentic engineering system) and is required by AEnt-M (the enterprise coordinates over the substrate IGM defines). IGM is standalone-usable only when its consuming agents are built and operated inside an AEM-conformant engineering loop or an equivalent declared substitute; the standalone-usable claim is conditional, not free.

The accountability chain runs through all five layers. The Engineering Manifesto traces an agent's action to the specification that authorised it. The ASDLC traces the specification to the delivery pipeline that produced it. The APLC traces the product behavior to its composite state. This manifesto traces the intelligence to its governed claims. Together: a complete, auditable chain from what the agent did, through the constraint that allowed it, the product that contained it, the pipeline that delivered it, to the knowledge that justified it.

The bridge to agent governance is specific. The Engineering Manifesto's Principle 6 declares that "knowledge and memory are distinct infrastructure" requiring governance. This manifesto is the architecture behind that declaration. The APLC's composite state includes "knowledge base" as one of five components that determine an agent product's behavioral identity. This manifesto governs that component. When the knowledge base changes — a claim is promoted, demoted, contradicted, or retired — the agent product's composite state changes with it.

---

*See [manifesto-principles.md](manifesto-principles.md) for the twelve principles and four integrity preconditions, each with minimum bars. See [companion-guide.md](companion-guide.md) for the claim model in detail, the L1/L2/L3 memory spectrum, and worked examples. See [implementation-guide.md](implementation-guide.md) for the adoption path. See [domains/financial-services.md](domains/financial-services.md) for the FS regulatory mapping. See [governance/queries.md](governance/queries.md) for the 25 canonical governance queries. See [glossary.md](glossary.md) for term definitions. See [positioning.md](positioning.md) for how intelligence governance differs from data governance, knowledge management, and RAG.*

---

## Revision Log

| Version | Changes | Date |
|---|---|---|
| v1.0 | Initial publication | April 2026 |
| v1.1 | KM lineage acknowledged, contradiction taxonomy, regulatory alignment, failure modes expanded, provenance integrity, Expand guardrails. See detailed changelog in repo history. | April 2026 |
| v1.2 | Added "Intelligence, Not Knowledge" section defining organizational intelligence. Added governance relocation mechanism to lifecycle. Added domain graph as enterprise substrate. Updated connection section to five-layer governance stack. Linked to companion guide, implementation guide, FS domain mapping, and canonical governance queries. | May 2026 |
| v1.3 | Renamed "confidence" → "epistemic tier" (terminology note added). Added "Substrate Integrity — Four Additional Principles" section summarising new principles 13 (validatable claims, AEM P8 hook), 14 (claims as attack surfaces, AEM P10 hook for adversarial failure), 15 (architectural delegation to AEM P3), and 16 (containment for substrate-driven emergence, AEM P10 hook for emergent failure). Driven by IGM ↔ AEnt-M coherence review (B2 / B3 / W2.2 / W2.5). | May 2026 |
| v1.3 | Internal coherence pass: tightened Value 3 (preserve always; halt action when contradiction is material AND consequence-class is High/Critical); added "Which layer are you governing?" section reconciling external three-level hierarchy with internal L1/L2/L3 layers; cross-referenced governance-relocation to implementation-guide metrics, principle 11 quantitative signals, and `domains/financial-services.md`. | May 2026 |
| v1.4 | **Supersedes v1.3 rename.** Three-term division of labour: *confidence* (presentation), *epistemic tier* (formal governance), *epistemic quality* (composite reasoning chain). Leakage rule: tier names pair only with "epistemic tier". **Tier-ladder rename and 5→4 collapse:** Provisional → Candidate → Confirmed → High Confidence → Authoritative ⇒ Provisional → Emerging → Validated → Foundational. P11 consequence-class mapping is now 1:1 (Provisional ↔ Low, Emerging ↔ Medium, Validated ↔ High, Foundational ↔ Critical). P3 retitled "Epistemic tier is earned, not assigned"; P13 promotion threshold updated to "Validated"; Substrate Integrity short forms updated. v1.0–v1.3 tier names remap per the unified glossary's term-collision appendix. | May 2026 |
| v1.5 | **Reframed as "twelve principles plus four integrity preconditions."** Title of `manifesto-principles.md` updated; preamble and Part III heading clarify that P13–P16 are *preconditions in role, principles in numbering* — they protect the substrate, the twelve principles maintain it. Stable P-numbers retained for cross-reference continuity. **P14 substrate-security DRAFT resolved:** the substrate-security function is *not* a fifth governance authority; it reports through an independent CISO (or equivalent) line, holds operational override during integrity incidents, and consults/audits the four authorities outside incidents. **Stack framing retired altitude language:** across `positioning.md`, `README.md`, and this document, "one layer in the stack" / "parallel companion" prose is replaced with "*different surfaces*, connected by structural dependency, not hierarchy". Dependency direction (AEnt-M depends on IGM; AEM is inherited) unchanged. | May 2026 |
