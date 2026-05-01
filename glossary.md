# Intelligence Governance — Glossary

**Witold Reichhart and Arnaud Gelas**

Terms as used in the Intelligence Governance Manifesto, companion guide, and implementation guide. Definitions are scoped to this framework — some terms carry broader meanings elsewhere.

---

## Core Concepts

**Claim** — The atomic unit of governed intelligence. A discrete, verifiable assertion carrying metadata that makes it governable: type, source, provenance chain, confidence level, scope, temporal validity, contradiction status, dependencies, and governance status. Documents are sources. Claims are what the system reasons over. A claim that cannot be validated, scoped, or updated independently is not a governed claim — it is text.

**Governed intelligence** — What emerges when AI capability operates over knowledge that is current, contextual, connected, validated, scoped, auditable, and capable of learning from use. It is the capacity of the institution — not the model — to reason and act reliably. Governed intelligence is not a product. It is an operational discipline applied to the substrate that agents depend on.

**Organizational intelligence** — The system-level capacity to perceive institutionally relevant patterns, infer their consequences, and select or recommend action opportunities aligned with organizational purpose under changing constraints. Intelligence is not a property of the model alone. It is a property of the agent-substrate system — the interaction between inferential capability, governed knowledge, and the institutional constraints that define what "aligned" means.

**Domain graph** — The missing middle layer between foundation model capability (broad pattern density, low domain specificity) and application context (high specificity, low pattern density). Accumulated, governed, reusable domain substrate that no single client owns but every client needs. Satisfies four properties: scope, provenance, compounding, and decay management.

**Intelligence lifecycle** — Five concurrent stages that maintain the domain graph: Ingest (populate), Consolidate (connect), Curate (maintain quality), Expand (generate hypotheses), Apply (deliver to tasks). Not sequential — all five run continuously. Any system that treats them as sequential is performing document management with extra steps.

---

## Confidence and Trust

**Confidence level** — How much institutional support a claim carries under defined conditions. Earned through a deterministic process, not assigned by judgment. Five levels: Provisional → Candidate → Confirmed → High Confidence → Authoritative. Confidence moves in both directions. It does not certify truth. It does not remove the need for scope judgment.

**Provenance** — Where a claim came from, how it was validated, when it was last challenged, and what corroborates it. Includes source type, date of acquisition, acquisition mode, and the social process of challenge and acceptance. Provenance chains must be verifiable for integrity, not just recorded.

**Corroboration** — Independent evidence supporting a claim. Requires independent origin — two documents citing the same source count as one corroboration. Multiple copies of the same LLM-generated output count as zero.

**Confidence-to-action threshold** — The minimum confidence level required before a claim may be used for a given action type. The higher the autonomy of the consumer, the stronger the epistemic requirements. A human expert reviewing results needs only Provisional. An agent acting autonomously requires High Confidence. Regulatory evidence submission requires Authoritative.

---

## Governance Architecture

**Four authorities** — Functional governance roles that govern the graph. *Semantic authority*: defines vocabulary, ontology, and allowed relation types. *Assertion authority*: creates, validates, promotes, supersedes, or retires claims. *Inference authority*: defines rules by which claims support, contradict, or entail each other. *Revision authority*: handles challenge, contradiction, confidence downgrade, and decay. These are functional authorities, not job titles. One role may exercise multiple authorities in smaller implementations.

**Contradiction types** — Five types of conflict between claims: *logical contradiction* (both cannot be true within the same scope), *jurisdictional divergence* (both valid within their respective jurisdictions), *temporal supersession* (one claim has replaced another over time), *scope variation* (claims apply to different contexts), *extraction error* (conflict is an artifact of how the claim was captured). Untyped conflict is noise, not signal.

**Acquisition modes** — Four ways claims enter the graph. *Harvest*: automated, public sources, lowest cost, highest volume. *Extract*: tool-assisted from credentialed sources (project archives, vendor portals, defect logs). *Capture*: human-led structured interviews, most expensive, captures operational knowledge. *Emerge*: graph self-extension, connections and gaps the system surfaces. Emerge produces hypotheses requiring validation, never operational claims.

**Governance status** — What action may be taken from a claim: Searchable, Recommendable, Reasoning-eligible, Action-eligible, or Regulatory-evidence. Distinct from confidence level — governance status reflects institutional permission, not epistemic strength.

---

## Memory and Substrate

**L1: Working memory** — Claims loaded in active context at the moment of action. A governed window into L2 and L3, filtered by task scope, authorization level, and recency. Small, relevant, current, refreshed per decision cycle.

**L2: Institutional memory** — The curated, validated, connected knowledge the institution has accumulated. L2 is the domain graph — the governed substrate. Where epistemic debt accumulates. The full intelligence lifecycle operates on L2.

**L3: Foundational intelligence** — Deep structural knowledge that changes rarely but shapes everything: domain mechanics, regulatory architectures, institutional patterns. The geological layer. When L3 changes, cascade analysis traces forward through every L2 claim that depends on it.

**Fertility** — The rate at which existing knowledge generates new knowledge through operation. A property of the domain graph. The graph grows by generation — each use producing new connections — rather than by accumulation alone. Fertility is why governed intelligence compounds and why competitors cannot purchase the generative history.

---

## Risk and Failure

**Epistemic operational risk** — The risk of institutional harm from acting on stale, polluted, fragmented, or mis-scoped knowledge. Distinct from model risk (which concerns model behavior) and data risk (which concerns record-level quality). Epistemic operational risk concerns the governed intelligence layer between data and model.

**Epistemic debt** — The accumulated cost of deferred intelligence governance. Every claim that silently goes stale, every contradiction that goes untyped, every dependency chain that goes unchecked adds to the debt. Measured as: (stale + broken + unreviewed claims) / total claims. Analogous to technical debt but in the knowledge substrate.

**Epistemic circuit breaker** — A mechanism that halts agent action when epistemic confidence falls below threshold for the consequence level of the action. The agent does not silently degrade to best-effort. It produces a structured escalation identifying which claims triggered the breaker, the specific defect, and what action is blocked pending resolution.

**Intelligence theatre** — The failure mode where governance structures exist on paper but no claims are actually being revalidated, no contradictions reviewed, no engagement feedback captured. The governance is performative. Test: can the system answer IGQ-24 (epistemic debt load) with real numbers?

**Epistemic monoculture** — The failure mode where the governed intelligence base becomes the institution's only recognised memory. Communities of practice, apprenticeship, and informal knowledge-sharing wither. Diverse ways of knowing collapse into whatever the claim schema can represent.

---

## Governance Dynamics

**Governance relocation** — The mechanism by which governance enforcement migrates from synchronous pre-action gating to the substrate's own causal architecture as the domain graph deepens. At low substrate depth, governance is external friction. As the substrate deepens, the causal rationale those constraints protect becomes structurally represented in the graph itself. Governance does not disappear — its enforcement locus shifts. Measurable: declining governance intervention rates with stable or improving decision quality indicate relocation. Flat or rising rates indicate insufficient substrate depth.

**Autonomy** — An agent's capacity to execute assigned tasks reliably within defined constraints. Supported by shallow substrate. The agent does what it is told, well.

**Initiative** — An agent's capacity to surface action opportunities aligned with institutional purpose before being asked. Requires deep, governed, continuously enriched substrate. The difference between autonomy and initiative is substrate depth, not model capability.

**Capability** — What the model can do. Commoditises as foundation models converge. Distinct from organizational intelligence, which is what the institution can do with capability applied over governed substrate.

---

## Engagement and Operations

**Engagement archetypes** — Four governance profiles for different engagement types: *Domain Entry* (first engagement, sparse graph), *Domain Deepening* (enrichment and validation against operational reality), *Cross-Domain Extension* (spanning previously independent domains), *Regulatory Change* (revalidation triggered by regulatory amendment).

**Definition of Done** — Eight criteria for a domain's intelligence to be operationally ready: Populated, Connected, Validated, Governed, Applied, Traceable, Accountable, Funded.

**Canonical governance queries (IGQ-01 through IGQ-25)** — Twenty-five operational queries across seven concerns: provenance and trust, scope and applicability, staleness and decay, contradictions and conflicts, dependencies and cascade risk, agent action governance, and system health. Three usage categories: operational governance (daily), agent guardrails (per-action), and audit/examination.

---

*This is a companion to the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
