# Intelligence Governance — Glossary

**Witold Reichhart and Arnaud Gelas**

Terms as used in the Intelligence Governance Manifesto, companion guide, and implementation guide. Definitions are scoped to this framework — some terms carry broader meanings elsewhere.

> **Terminology note (v1.3).** What earlier IGM revisions called *confidence level* / *confidence tier* is renamed **epistemic tier** to free the word *confidence* for AEM-style verification meaning ("did the change pass the gates we agreed on?"). The five tier names (Provisional → Candidate → Confirmed → High Confidence → Authoritative) and their semantics are unchanged. References to "confidence" in the body text of v1.0–v1.2 should be read as "epistemic tier" unless the surrounding text refers to AEM verification confidence. See the term-collision appendix at the end of this glossary for cross-framework mappings.

---

## Core Concepts

**Claim** — The atomic unit of governed intelligence. A discrete, verifiable assertion carrying metadata that makes it governable: type, source, provenance chain, epistemic tier, scope, temporal validity, contradiction status, dependencies, and governance status. Documents are sources. Claims are what the system reasons over. A claim that cannot be validated, scoped, or updated independently is not a governed claim — it is text.

**Governed intelligence** — What emerges when AI capability operates over knowledge that is current, contextual, connected, validated, scoped, auditable, and capable of learning from use. It is the capacity of the institution — not the model — to reason and act reliably. Governed intelligence is not a product. It is an operational discipline applied to the substrate that agents depend on.

**Organizational intelligence** — The system-level capacity to perceive institutionally relevant patterns, infer their consequences, and select or recommend action opportunities aligned with organizational purpose under changing constraints. Intelligence is not a property of the model alone. It is a property of the agent-substrate system — the interaction between inferential capability, governed knowledge, and the institutional constraints that define what "aligned" means. *Authorial choice (v1.3): IGM uses the manifesto definition as canonical; earlier glossary phrasing that introduced an additional interpretation is retired.*

**Domain graph** — The missing middle layer between foundation model capability (broad pattern density, low domain specificity) and application context (high specificity, low pattern density). Accumulated, governed, reusable domain substrate that no single client owns but every client needs. Satisfies four properties: scope, provenance, compounding, and decay management.

**Subdomain** — A bounded slice of a domain treated as the unit of assertion authority and the unit of phased rollout. A subdomain is defined by a coherent jurisdictional/functional scope (for example: "EU CSDR settlement penalties" within the broader "settlement" domain). Phase 1 onboarding (implementation-guide) names one assertion authority *per subdomain*; the four-authority model in Principle 6 binds at the domain or cross-domain level. *DRAFT — author review needed: confirm whether subdomain boundaries are formally registered or emerge through engagement experience.*

**Critical path** — In the decay-triage model (manifesto-principles Principle 5; implementation-guide), the set of claims on the active reasoning path of agent workflows currently in production. Critical-path claims are revalidated first and carry the shortest decay windows. At enterprise scale this is typically 5–15% of the graph. Critical-path status is a runtime property, not a permanent label: a claim becomes critical-path when an agent workflow above the Low consequence class loads it into L1; it ceases to be critical-path when no such workflow has loaded it within the configured observation window.

**Intelligence lifecycle** — Five concurrent stages that maintain the domain graph: Ingest (populate), Consolidate (connect), Curate (maintain quality), Expand (generate hypotheses), Apply (deliver to tasks). Not sequential — all five run continuously. Any system that treats them as sequential is performing document management with extra steps.

---

## Epistemic Tiers and Trust

**Epistemic tier** *(was: confidence level)* — How much institutional support a claim carries under defined conditions. Earned through a deterministic process, not assigned by judgment. Five tiers: Provisional → Candidate → Confirmed → High Confidence → Authoritative. The tier moves in both directions. It does not certify truth. It does not remove the need for scope judgment. It does not authorise action by itself. *Backward-compat note: v1.0–v1.2 of the IGM used "confidence level" and "confidence tier" for this concept; references to "confidence" in those revisions read as "epistemic tier" unless the surrounding text refers to AEM verification confidence.*

The canonical tier table — single source of truth, aligning manifesto, companion-guide and glossary:

| Tier | Criteria | Permitted use |
|---|---|---|
| **Provisional** | Source identified, provenance recorded, no validation. | Search results with caveat. Not for agent reasoning. |
| **Candidate** | Passed structural checks (type, scope, temporal validity), awaiting expert review. | Search results. Human-reviewed recommendations. Not for agent action. |
| **Confirmed** | Expert-validated by one qualified domain practitioner. | Search. Recommendations. Agent reasoning with epistemic-tier flag. |
| **High Confidence** | Corroborated by two or more independent sources. | Search. Recommendations. Agent reasoning. Agent action with audit trail. |
| **Authoritative** | Corroborated, stable over time, traceable to primary regulatory or institutional source. | Full use including regulatory evidence and autonomous agent action. |

**Provenance** — Where a claim came from, how it was validated, when it was last challenged, and what corroborates it. Includes source type, date of acquisition, acquisition mode, and the social process of challenge and acceptance. Provenance chains must be verifiable for integrity, not just recorded.

**Corroboration** — Independent evidence supporting a claim. Requires independent origin — two documents citing the same source count as one corroboration. Multiple copies of the same LLM-generated output count as zero.

**Epistemic-tier-to-action threshold** *(was: confidence-to-action threshold)* — The minimum epistemic tier required before a claim may be used for a given action type. The higher the autonomy of the consumer, the stronger the epistemic requirements. A human expert reviewing results needs only Provisional. An agent acting autonomously requires High Confidence. Regulatory evidence submission requires Authoritative.

---

## Governance Architecture

**Four authorities** — Functional governance roles that govern the graph. *Semantic authority*: defines vocabulary, ontology, and allowed relation types. *Assertion authority*: creates, validates, promotes, supersedes, or retires claims. *Inference authority*: defines rules by which claims support, contradict, or entail each other. *Revision authority*: handles challenge, contradiction, epistemic-tier downgrade, and decay. These are functional authorities, not job titles. One role may exercise multiple authorities in smaller implementations.

**Five contradiction types** — Five typed conflicts between claims; untyped conflict is noise, not signal. Each type carries different operational implications:

- **Logical contradiction** — both claims cannot be true within the same scope. *Worked example:* one claim states "CSDR penalties are calculated daily on net fail value"; another (same jurisdiction, same date) states "CSDR penalties are calculated on gross fail value." At least one is wrong; revision authority must adjudicate.
- **Jurisdictional divergence** — both claims are valid within their respective jurisdictions. *Worked example:* "EU CSDR settlement-fail penalty rate = X bps/day" and "UK CREST post-Brexit penalty rate = Y bps/day". Both must be preserved; cross-border programmes need both.
- **Temporal supersession** — one claim has replaced another over time. *Worked example:* "MiFID II Article 27 best-execution top-5 venue reporting" is superseded by "MiFID II Quick Fix removes RTS 28 reporting requirement (2021)." The old claim is demoted with a tracked succession chain, not deleted.
- **Scope variation** — claims apply to different contexts and are mistakenly compared. *Worked example:* "T+1 settlement applies" (US equities, post 2024) versus "T+2 settlement applies" (EU equities). Both are correct within their declared scope; the conflict is an artefact of stripping scope metadata.
- **Extraction error** — the conflict is an artefact of how the claim was captured. *Worked example:* an OCR pipeline extracts "penalty = 1.0 bps" from a table where the true value is "0.1 bps"; the apparent contradiction with the underlying regulation disappears once the extraction error is corrected.

**Acquisition modes** — Four ways claims enter the graph. Each mode has different cost, reliability, and entry-tier expectations:

| Mode | Description | Typical entry tier |
|---|---|---|
| **Harvest** | Automated, public sources, lowest cost, highest volume. | Provisional |
| **Extract** | Tool-assisted from credentialed sources (project archives, vendor portals, defect logs). | Provisional → Candidate |
| **Capture** | Human-led structured interviews, most expensive, captures operational knowledge. | Candidate (single SME) → Confirmed (validated) |
| **Emerge** | Graph self-extension; connections and gaps the system surfaces. | Hypothesis only — never operational |

Emerge produces hypotheses requiring validation, never operational claims.

**Emerge mode** — Standalone entry for the fourth acquisition mode. Graph self-extension: relationships, gap candidates, and entailment hypotheses the system surfaces from existing structure without human prompting. Emerge outputs are *acquisition hypotheses*, not claims. They enter the standard validation pipeline and become claims only after human validation and promotion through the standard intake gate. Uncontrolled Emerge — where machine-generated suggestions bypass validation — is a failure mode (see Principle 7).

**Decay class** — A bucket assigned at claim creation that determines the claim's expected validity window and revalidation cadence. Three primary classes:

- **Regulatory** — bound to a specific regulation, directive, or rule. Decays on amendment cycle of the issuing authority (typically 12–36 months); cascade-revalidated immediately on amendment notice.
- **Operational** — describes how a process is currently run, including workarounds. Decays fastest (typically 30–90 days); a workaround valid last quarter may not survive a system upgrade.
- **External** — externally observed phenomena (vendor configurations, third-party APIs, market data definitions). Decays per release cadence of the external source; bound to monitorable change events.

A fourth class — **Foundational/L3** — applies to deep structural knowledge (regulatory architectures, domain mechanics) that decays rarely but cascades widely; revalidation is event-driven, not schedule-driven. *DRAFT — author review needed: confirm whether decay-class taxonomy is normative or illustrative.*

**Governance status** — What action may be taken from a claim: Searchable, Recommendable, Reasoning-eligible, Action-eligible, or Regulatory-evidence. Distinct from epistemic tier — governance status reflects institutional permission, not epistemic strength.

---

## Memory and Substrate

**L1: Working memory** — Claims and practitioners' situated knowledge loaded in active context at the moment of action. A governed window into L2 and L3, filtered by task scope, authorization level, and recency. Small, relevant, current, refreshed per decision cycle. *(This entry is now aligned with the companion-guide L1 description, which explicitly includes the practitioner alongside the agent.)*

**L2: Institutional memory** — The curated, validated, connected knowledge the institution has accumulated. L2 is the domain graph — the governed substrate. Where epistemic debt accumulates. The full intelligence lifecycle operates on L2.

**L3: Foundational intelligence** — Deep structural knowledge that changes rarely but shapes everything: domain mechanics, regulatory architectures, institutional patterns. The geological layer. When L3 changes, cascade analysis traces forward through every L2 claim that depends on it.

**L1 / L2 / L3 memory layers** — The composite three-layer model. L3 provides the structural foundation; L2 builds institutional knowledge on that foundation; L1 selects from L2 (and references L3) what is relevant to the current decision. Promoted from companion-guide-only to a normative model under Principle 9 (manifesto-principles.md). For the relationship between this internal layer model and the external Knowledge / Organizational Intelligence / Governed Intelligence three-level model, see the "Which layer are you governing?" section in `manifesto.md`.

**Fertility** — The rate at which existing knowledge generates new knowledge through operation. A property of the domain graph. The graph grows by generation — each use producing new connections — rather than by accumulation alone. Fertility is why governed intelligence compounds and why competitors cannot purchase the generative history.

---

## Risk and Failure

**Epistemic operational risk** — The risk of institutional harm from acting on stale, polluted, fragmented, or mis-scoped knowledge. Distinct from model risk (which concerns model behavior) and data risk (which concerns record-level quality). Epistemic operational risk concerns the governed intelligence layer between data and model.

**Epistemic debt** — The accumulated cost of deferred intelligence governance. Every claim that silently goes stale, every contradiction that goes untyped, every dependency chain that goes unchecked adds to the debt. Measured as: (stale + broken + unreviewed claims) / total claims. Analogous to technical debt but in the knowledge substrate.

**Epistemic circuit breaker** — A normative mechanism (specified under Principle 11 in `manifesto-principles.md`) that halts agent action when the epistemic-tier of claims required for the current action falls below the threshold for that action's consequence class. The agent does not silently degrade to best-effort. It produces a structured escalation identifying which claims triggered the breaker, the specific defect (staleness, contradiction, scope mismatch, broken provenance), and what action is blocked pending resolution. **Frequency framing:** circuit-breaker activation rate is the *inverse indicator of governance relocation success*. Rising activation rates with stable substrate depth indicate insufficient relocation; declining rates with stable decision quality indicate relocation is working. Activation is a measurement, not only a halt mechanism.

**Intelligence theatre** — The failure mode where governance structures exist on paper but no claims are actually being revalidated, no contradictions reviewed, no engagement feedback captured. The governance is performative. Test: can the system answer IGQ-24 (epistemic debt load) with real numbers?

> **Note on Level 2 "informal confidence" vs intelligence theatre.** Implementation-guide Level 2 ("Structured") describes confidence as *informal* — claims have sources, structure is queryable, but no deterministic tier criteria. Intelligence theatre is the failure mode where Level 2 confidence is *labelled as governed* without the deterministic criteria that distinguish Level 3+. Level 2 informal confidence is acceptable as a transient maturity stage on the path to Level 3; it is **not** acceptable as a steady state, and is **not** acceptable for any agent action above the Low consequence class. Systems that remain at Level 2 while presenting themselves as governed exhibit intelligence theatre.

**Epistemic monoculture** — The failure mode where the governed intelligence base becomes the institution's only recognised memory. Communities of practice, apprenticeship, and informal knowledge-sharing wither. Diverse ways of knowing collapse into whatever the claim schema can represent. *Symptom: experts consult the graph instead of each other; knowledge that doesn't fit the claim schema is treated as non-existent.* Promoted from manifesto-only failure-modes section to a glossary-resident concept because it is referenced normatively in Principle 8 and the implementation-guide.

---

## Governance Dynamics

**Governance relocation** — The mechanism by which governance enforcement migrates from synchronous pre-action gating to the substrate's own causal architecture as the domain graph deepens. At low substrate depth, governance is external friction. As the substrate deepens, the causal rationale those constraints protect becomes structurally represented in the graph itself. Governance does not disappear — its enforcement locus shifts. Measurable: declining governance intervention rates with stable or improving decision quality indicate relocation. Flat or rising rates indicate insufficient substrate depth.

**Autonomy** — An agent's capacity to execute assigned tasks reliably within defined constraints. Supported by shallow substrate. The agent does what it is told, well.

**Initiative** — An agent's capacity to surface action opportunities aligned with institutional purpose before being asked. Requires deep, governed, continuously enriched substrate. The difference between autonomy and initiative is substrate depth, not model capability.

**Capability** — What the model can do. Commoditises as foundation models converge. Distinct from organizational intelligence, which is what the institution can do with capability applied over governed substrate.

---

## Engagement and Operations

**Engagement archetypes** — Four governance profiles for different engagement types: *Domain Entry* (first engagement, sparse graph), *Domain Deepening* (enrichment and validation against operational reality), *Cross-Domain Extension* (spanning previously independent domains), *Regulatory Change* (revalidation triggered by regulatory amendment).

**Definition of Done** — Eight criteria for a domain's intelligence to be operationally ready, listed below in canonical form (manifesto.md is the source). A domain is *operationally ready* only when **all eight** are satisfied; partial satisfaction is reported with named gaps.

1. **Populated** — Claims ingested from all major source types (documentary, expert, operational).
2. **Connected** — Entity resolution complete, cross-domain links established, contradiction map current.
3. **Validated** — Domain expert review complete, epistemic tiers assigned, provenance verified.
4. **Governed** — Four authorities assigned to named roles, decay monitoring active, revision workflow operational.
5. **Applied** — At least one delivery engagement consuming intelligence with active feedback loop.
6. **Traceable** — Every agent-consumed claim traceable from action to claim to source.
7. **Accountable** — Governance roles staffed, authority boundaries documented, escalation paths defined.
8. **Funded** — Ongoing curation capacity allocated, priced into the commercial model, and protected from delivery reallocation.

**Canonical governance queries (IGQ-01 through IGQ-25)** — Twenty-five operational queries across seven concerns: provenance and trust, scope and applicability, staleness and decay, contradictions and conflicts, dependencies and cascade risk, agent action governance, and system health. Three usage categories: operational governance (daily), agent guardrails (per-action), and audit/examination.

---

## Term-collision appendix (IGM ↔ AEM ↔ AEnt-M)

For readers using IGM alongside the Agentic Engineering Manifesto (AEM) and the Agentic Enterprise Manifesto (AEnt-M):

| Term | IGM (this document) | AEM | AEnt-M |
|---|---|---|---|
| **Confidence** | Renamed to **epistemic tier** (this glossary) | Binary verification gate ("did the change pass the gates we agreed on") | Epistemic quality summary surfaced at decision time |
| **Knowledge** | Structured claims with provenance, epistemic tier, scope (L2/L3) | Durable curated facts (subset of IGM L2/L3) | Governed substrate (delegated to IGM) |
| **Governance** | Knowledge-object stewardship | Agent-action oversight | Enterprise-coordination layer |
| **Scope** | Claim validity context | Task / specification boundary | View filtering |
| **Validation** | Domain-expert claim review (intake) | "Did we build the right thing" outcome validation | Delegated |
| **Initiative** | Substrate-depth-driven (Principle 10) | Not defined | Three-conditions-driven |

When in doubt, prefer the IGM term in IGM contexts; the cross-references in `manifesto.md` and `manifesto-principles.md` flag boundary cases explicitly.

---

*This is a companion to the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
