# Intelligence Governance — Implementation Guide

**[Witold Reichhart](https://github.com/witoldreichhart) and [Arnaud Gelas](https://github.com/arnaudgelas)**

This guide provides an adoption path for intelligence governance. It is organized by maturity level, starting from minimum viable governance through to full operational governance in regulated industries.

---

## Starting principles

Intelligence governance does not require a complete implementation to be useful. It does require a minimum threshold to be honest.

A system that claims governance but cannot answer "where did this claim come from?" and "is it still current?" does not have governance. It has documentation with a governance label.

Start where you are. Build governance incrementally. Do not wait for the perfect system before governing the one you have.

---

## Minimum viable intelligence governance

The smallest useful implementation. Suitable for a team beginning to build a domain graph or retrofitting governance onto an existing knowledge base. The MVG checklist below is **normative**: an implementation that cannot answer Yes-with-evidence to every numbered item does not yet have minimum viable governance, regardless of how mature its tooling looks.

> **v1.3 update.** Earlier versions of the MVG omitted scope enforcement (P1), contradiction tracking (P4), L1/L2/L3 separation, and decay-class taxonomy. Coherence review item W2.25 added these. The list below is the tightened checklist. Operations relying on the prior 5-item list should treat the additions as remediation work, not optional polish.
>
> **v1.4 update.** The MVG checklist tier names below were rewritten for the v1.4 four-tier ladder (Provisional → Emerging → Validated → Foundational). Operations holding evidence against the v1.0–v1.3 five-tier names (Provisional → Candidate → Confirmed → High Confidence → Authoritative) should remap per the unified glossary's term-collision appendix; the structural intent of each MVG item is unchanged.

**MVG checklist — Yes / No (with evidence) per item:**

1. **Provenance at entry (P2).** Every claim has a recorded source — at minimum source type, date of acquisition, and acquisition mode. *Evidence:* sample of 20 random claims from each active domain, all with complete source attribution.
2. **Claim as unit, with type (P1).** Every claim has a declared type (Regulatory, Operational, Technical, Domain-mechanical, External-intelligence). *Evidence:* claim-type distribution report; zero claims of type Unknown or Untyped.
3. **Scope declared and enforced (P1).** Every claim has a declared scope (jurisdiction, entity, process, system, temporal boundary). The Apply stage filters claims by task scope before they reach L1; out-of-scope retrievals are blocked or flagged, not silently included. *Evidence:* scope-mismatch incident log with response history; sample of Apply-stage queries showing scope filter applied.
4. **Epistemic tier earned, not assigned (P3).** Every claim carries a visible epistemic tier (Provisional → Emerging → Validated → Foundational). Promotion above Provisional requires recorded corroboration; promotion to Validated requires a recorded validation event (P13). *Evidence:* tier-transition audit log with provenance of each promotion.
5. **Decay awareness with class taxonomy (P5).** Every claim has a declared decay class (regulatory / operational / external / domain-mechanical / configuration) determining its revalidation schedule. Claims approaching their revalidation deadline are flagged. Decay-class assignment is not "default" — it is a decision recorded at intake. *Evidence:* per-domain decay-class distribution and staleness-alert log.
6. **Contradiction tracking (P4).** Contradiction detection is automated. Every detected contradiction carries a type (logical / jurisdictional / temporal / scope / extraction). Resolution is human-gated; no contradiction is silently overwritten. *Evidence:* open and closed contradiction register with type and resolution status per entry.
7. **L1 / L2 / L3 separation.** The system distinguishes working memory (L1, claims at the point of decision), institutional memory (L2, the curated domain graph), and foundational intelligence (L3, structural knowledge). L1 retrievals are scope-checked and freshness-gated; L3 changes trigger cascade analysis on dependent L2 claims. *Evidence:* a claim's L-level is recorded; a worked example showing an L3 change triggering downstream L2 review.
8. **Named assertion authority per domain (P6).** A named person (or named role with a named current incumbent) is accountable for claim accuracy in each domain. Authority assignment is recorded in a register that is current. *Evidence:* domain → assertion-authority map, dated within the last quarter.

**You do not yet need (above MVG):** Full four-authority governance, full cascade analysis depth, cross-domain linking, automated decay-rate calibration, engagement feedback loops, L4-tier operational integration, the Adaptive maturity capabilities.

**Time to implement:** 4-8 weeks for a single domain, assuming the knowledge base already exists in some form. The MVG checklist above is heavier than the prior 5-item list; budget accordingly. The additional work is largely tagging (scope, decay class) and instrumentation (contradiction detection, scope-filter enforcement), not building new systems.

---

## Five maturity levels

### Level 1: Ad hoc

Knowledge exists in documents, wikis, SharePoint, Confluence, individual expertise. No claim-level governance. No provenance tracking. No decay management. AI systems retrieve from document stores with no governance at the retrieval level.

**Indicators:** Knowledge quality depends on who you ask. Different team members give different answers about the same domain question. Nobody knows which operational procedures are current. Onboarding takes months because institutional knowledge is distributed across people and implicit.

**Risk profile:** High epistemic operational risk. AI agents operating at this level are retrieving from ungoverned sources and treating all retrieved content as equally reliable.

### Level 2: Structured

Knowledge has been extracted into a structured form — a knowledge graph, a structured database, a governed taxonomy. Claims exist as identifiable units. Provenance is recorded at ingestion. Basic scope metadata exists.

**Indicators:** You can point to where institutional knowledge lives. Claims have sources. The structure is queryable. But epistemic-tier assessment is *informal* ("we think this is right"), decay is unmanaged (claims are current until someone notices they are not), and contradictions are resolved silently rather than preserved.

> **Note on informal tier assessment vs intelligence theatre.** Level 2 informal tier assessment is acceptable as a transient stage on the path to Level 3 (where deterministic tier criteria apply). It is **not** acceptable as a steady state, and it is **not** acceptable for any agent action above the Low consequence class. A system that remains at Level 2 while presenting itself as governed exhibits *intelligence theatre* — the failure mode where governance structures exist on paper but no deterministic criteria back them up.

**Risk profile:** Medium-high. Better than Level 1 because the structure is explicit, but epistemic-tier and decay governance are missing. Agents operating at this level may act on stale or weakly supported claims without knowing it.

### Level 3: Governed

Claims carry epistemic tiers earned through defined criteria. Decay monitoring is active — claims are revalidated on schedule. The four governance authorities are assigned. Contradictions are typed and tracked. Engagement feedback loops exist. Provenance chains are complete and auditable.

**Indicators:** You can answer IGQ-01 through IGQ-10 (see governance/queries.md). You know what is stale, what is contradicted, and what epistemic tier each claim carries. Named authorities are accountable for semantic, assertion, inference, and revision governance.

**Risk profile:** Medium. Governance is active but may not cover the full graph. Some domains are well-governed; others lag. The primary risk is uneven coverage rather than absent governance.

### Level 4: Operational

Intelligence governance is embedded in operational workflows. Agents respect epistemic-tier-to-action thresholds. Epistemic circuit breakers halt action on defective knowledge. L1 working memory is scope-checked and freshness-gated. Cross-domain linking is active. Cascade analysis runs on epistemic-tier changes. The system can answer all 25 canonical queries.

**Indicators:** Agent actions are traceable to specific claims with specific epistemic tiers. Governance interventions are measurable — you can track how often the system blocks or escalates based on epistemic quality. Epistemic debt is measured and managed as a system health metric.

**Risk profile:** Low-medium. Governance is operational and measurable. Residual risk comes from edge cases, novel domains not yet covered, and L3 foundational changes whose cascading effects are partially tracked.

### Level 5: Adaptive

The intelligence governance system learns from its own operation. Decay models are calibrated by observed decay rates rather than preset schedules. Epistemic-tier propagation is refined by tracking which prediction-error patterns correlate with which governance failures. The system identifies its own gaps — domains where coverage is thin, claim types where staleness outpaces revalidation capacity, cross-domain boundaries where scope confusion is most frequent.

**Indicators:** Governance improves through use, not through periodic review. The system surfaces its own weaknesses. Epistemic debt trends downward over time. New domains are onboarded faster because governance patterns from existing domains transfer.

**Risk profile:** Low. Residual risk is genuinely novel situations the system has not encountered — irreducible uncertainty rather than governance failure.

---

## Definition of Done × Maturity Level — mapping

The eight Definition of Done criteria from `manifesto.md` are not all-or-nothing — they are progressively satisfied as a domain advances through the five maturity levels. The table below maps each DoD criterion to the level at which it is **first achievable** (early) and the level at which it is **fully satisfied** (mature). A domain that claims DoD must demonstrate both coverage and depth — Level 3 minimum for *Validated*, *Governed*, *Traceable*, *Accountable*; Level 4 for *Applied* and *Funded* in regulated workflows.

| DoD criterion | Lvl 1 (Ad hoc) | Lvl 2 (Structured) | Lvl 3 (Governed) | Lvl 4 (Operational) | Lvl 5 (Adaptive) |
|---|---|---|---|---|---|
| **1. Populated** | Implicit (knowledge in documents/heads) | First achievable — claims extracted as units | Coverage measurable per domain | Coverage maintained against gap-detection | Gap-detection drives ingestion priorities |
| **2. Connected** | Not tracked | Partial (basic entity resolution) | First fully achievable — entity resolution + cross-domain edges + contradiction map | Cross-domain links continuously refreshed | New connections surfaced by graph self-extension |
| **3. Validated** | No tier | Informal tier | First fully achievable — tier earned through deterministic criteria; provenance verified | Validation events recorded as P13 first-class objects | Validation cadence calibrated by observed decay |
| **4. Governed** | No authorities | Authority informal | First fully achievable — all four authorities named, decay monitoring active, revision workflow operational | Authorities + escalation SLOs (10/30 day) reportable to second line | Authority workload calibrated by observed conflict patterns |
| **5. Applied** | Ad hoc consumption | Structured retrieval | At least one engagement consuming with feedback loop | First fully achievable — agent action gated by epistemic-tier-to-action thresholds; circuit breakers operational | Feedback drives substrate fertility metrics |
| **6. Traceable** | None | Document trace | Provenance chain complete and auditable | First fully achievable — every agent action traceable to claims with tier and provenance at time of action | Trace data feeds governance-relocation metrics |
| **7. Accountable** | Implicit | Named owner per domain | First fully achievable — four authorities staffed, boundaries documented, escalation paths defined | Accountability anchored in evidence bundles per release | Authority succession + portfolio limits enforced |
| **8. Funded** | Volunteer / unfunded | Project-funded | Funded as line item with named curation capacity | First fully achievable in regulated workflows — ongoing capacity protected from delivery reallocation | Funding scaled by epistemic-debt and decay-load metrics |

**Reading the table.** A domain at Level 3 satisfies DoD criteria 1–4 fully and 5–8 minimally; a domain at Level 4 satisfies all eight at the operational bar required for regulated agent action. *Operational readiness* per the manifesto requires **all eight** criteria; the table specifies the maturity level at which each is first achievable, not where it may stop.

---

## Adoption sequence

### Phase 1: Foundation (weeks 1-4)

**Goal:** Minimum viable governance for one domain.

**Actions:**
- Select a single domain with high operational risk and existing knowledge assets (in FS: settlement operations, regulatory reporting, or compliance interpretation)
- Extract claims from existing documentation. Tag with source, type, scope, and initial epistemic tier
- Assign assertion authority — one named domain expert per subdomain
- Set decay schedules by claim type
- Implement IGQ-01, IGQ-03, IGQ-10 (provenance, epistemic tier, staleness) as operational queries

**Deliverable:** A governed domain graph for one domain with provenance, epistemic tier, scope, and decay tracking. Level 2 maturity for that domain.

### Phase 2: Governance activation (weeks 5-10)

**Goal:** Full governance for the initial domain. Level 3 maturity.

**Actions:**
- Assign all four governance authorities (semantic, assertion, inference, revision)
- Implement typed contradiction tracking
- Activate decay monitoring with automated alerts
- Run first engagement with structured feedback loop (start, mid-point, close)
- Implement epistemic-tier-to-action thresholds for any agents operating on this domain
- Deploy IGQ-01 through IGQ-16 as operational queries

**Deliverable:** Active governance with measurable intervention rates. Named authorities. Contradiction tracking. Agent guardrails.

### Phase 3: Operational integration (weeks 11-16)

**Goal:** Intelligence governance embedded in operational workflows. Level 4 maturity.

**Actions:**
- Implement L1 working memory governance (scope-checking, freshness-gating, epistemic-tier floors)
- Activate cascade analysis on epistemic-tier changes
- Deploy epistemic circuit breakers for agent workflows above defined consequence thresholds (see below)
- Begin cross-domain linking if adjacent domains have been onboarded
- Implement all 25 canonical governance queries
- Establish epistemic debt as a reportable system health metric

**Deliverable:** Full operational governance for the initial domain. Agent actions traceable and governed. Epistemic debt measured.

### Phase 4: Domain expansion (ongoing)

**Goal:** Extend governance to additional domains. Each new domain follows Phases 1-3 with decreasing time-to-governance as patterns transfer.

**Expected timeline by domain:**
- Domain 2: 8-12 weeks (patterns from domain 1 transfer, especially entity resolution and governance authority structure)
- Domain 3+: 6-10 weeks (cross-domain linking begins to surface shared claims and reduce duplication)

### Phase 5: Adaptive governance (6+ months post initial domain)

**Goal:** Level 5 maturity. The system improves through its own operation.

**Actions:**
- Calibrate decay models against observed decay rates
- Track governance intervention patterns to identify systematic weaknesses
- Implement gap detection — domains, claim types, and cross-domain boundaries where coverage is insufficient
- Establish governance feedback loops that refine epistemic-tier propagation, scope enforcement, and cascade analysis based on operational evidence

---

## Metrics

### Leading indicators (predict governance quality)

| Metric | Target | Warning threshold |
|---|---|---|
| Claims with complete provenance | >95% | <85% |
| Claims within revalidation window | >90% | <80% |
| Active contradictions with assigned authority review | >80% | <60% |
| Domains with all four authorities assigned | 100% | <100% |
| Engagement feedback loop completion rate | >90% | <70% |

### Lagging indicators (measure governance outcomes)

| Metric | Target | Warning threshold |
|---|---|---|
| Epistemic debt ratio (stale + broken + unreviewed claims / total) | <10% | >20% |
| Agent actions blocked by epistemic circuit breakers (*inverse indicator of governance relocation success*) | Declining trend with stable/improving decision quality | Rising trend, or declining trend with falling decision quality |
| Governance interventions per 1000 agent actions | Declining trend | Flat or rising |
| Time to revalidate after regulatory change | <5 business days for directly affected claims | >15 business days |
| Scope-mismatch incidents (claim used outside declared scope) | <1 per month per domain | >5 per month |

---

## Epistemic circuit breakers — implementation notes

> **Normative source.** The epistemic circuit-breaker specification is normative under `manifesto-principles.md` Principle 11. The consequence-class table (Low / Medium / High / Critical) and the structured-escalation requirement are not optional; this section provides implementation-level notes on consequence-threshold definition and SLA setting. Activation rate is reframed there as the *inverse indicator of governance relocation* rather than only a halt mechanism.

**Defining consequence thresholds locally.** Each organisation defines its own threshold levels using the four named consequence classes. A consequence threshold is the estimated institutional impact of an incorrect action — measured by financial exposure, regulatory risk, client impact, or reputational damage. The mapping of specific actions to consequence classes is published and maintained by the assertion authority for the domain in which the action runs.

**SLA for resolution.** Circuit-breaker escalations carry a deadline tied to operational context, set per workflow rather than per breaker type. A settlement-related breaker in an active trading window requires resolution within hours; a compliance-interpretation breaker outside reporting season may allow days. SLA breaches are reported alongside activation rates as governance-relocation signals.

**Logging.** Each activation is logged with: the claims that triggered the breaker, their epistemic tiers and provenance chains at the time of action, the specific defect (staleness, contradiction, scope mismatch, broken provenance), the action that was blocked, the human(s) notified, the resolution timeline, and the resolution outcome. This log is the primary evidence base for the inverse-indicator metric.

---

## Decay triage — implementation notes

> **Normative source.** The four-priority decay-triage model (P1 Critical-path → P4 Dormant) is normative under `manifesto-principles.md` Principle 5. The priorities, typical share bands, and the requirement that P1 revalidates before P3/P4 are non-negotiable. This section provides implementation-level guidance on operating the model at scale.

**Identifying P1 (Critical-path) claims at runtime.** Critical-path status is a runtime property: a claim becomes critical-path when an agent workflow above the Low consequence class loads it into L1 (per the epistemic-circuit-breaker spec). The Apply stage emits a "claim touched by critical-path workflow" event; the curate stage subscribes to these events and applies the shortest decay window.

**Identifying P2 (High-dependency) claims.** Use IGQ-17 (downstream-dependent count) and IGQ-18 (cascade reach) as the primary signals. Maintain a watchlist of the top-decile dependent claims per domain.

**Auto-revalidation envelope.** Auto-revalidation handles unambiguous cases — regulatory source unchanged since last validation, no contradiction or epistemic-tier transition since last validation, no L3 cascade event affecting the claim. When all three conditions hold, the decay clock resets automatically. When any condition is breached, the claim is queued for human review. In practice, auto-revalidation handles 40–60% of revalidation volume.

**Promotion of P4 → P3 on engagement reactivation.** Dormant claims are not deleted. When an engagement reactivates the domain, P4 claims are promoted to P3 and revalidated *before* any agent use. The Apply stage refuses to load P4 claims into L1.

---

## Epistemic Tier Waiver

> **Note.** Throughout this section, *epistemic tier* refers to the IGM v1.4 four-tier ladder (Provisional → Emerging → Validated → Foundational). The term *epistemic tier* is the formal governance label for what is colloquially called *confidence*; tier names always pair with "epistemic tier", not "confidence". See the v1.4 terminology note in [manifesto-principles.md](manifesto-principles.md).

The IGM tier system gates what agents may do with claims (see *Epistemic-tier-to-action thresholds* in the [companion guide](companion-guide.md)). In practice, operational reality occasionally requires acting on a claim at a tier below the threshold its consequence class demands — the validation evidence is partially complete, a primary regulatory source is mid-amendment, the curation backlog has not yet caught up. Without a governed waiver mechanism, teams either block legitimate operations or silently degrade the threshold. Both outcomes corrupt the substrate.

This section defines the **Epistemic Tier Waiver** — a time-bounded, named-owner accommodation that allows a claim to be used above its earned tier under defined compensating controls. It is modelled on the ASDLC waiver mechanism ([waiver-governance.md](../asdlc/waiver-governance.md)) and follows the same governance-debt discipline.

### Required fields

Every Epistemic Tier Waiver must include all of the following. A waiver missing any element is not a valid waiver and the underlying claim cannot be used above its earned tier.

**Waiver owner.** A named individual from the **Revision authority** who accepts accountability for the residual epistemic risk during the waiver period. The waiver owner is not the assertion authority that would normally promote the claim — it is the revision authority lead, or a named delegate, signing for the risk that the claim is being used above the tier its evidence supports. The waiver owner cannot be the same person who requested the waiver.

**Risk description.** A specific statement of what could go wrong as a result of using the claim at the waived tier. Not "claim is below threshold" — a specific operational consequence. *Example:* "The CSDR penalty calculation update for UK CREST is at Emerging tier (single regulatory source, no operational verification yet — no P13 validation event recorded). Using it at Foundational tier for cross-border settlement advisory exposes the firm to giving advice based on a regulatory interpretation that has not been validated against actual penalty calculations observed in production over a full settlement cycle."

**Compensating control.** A specific control that is operational *now*, not planned, that reduces the risk introduced by the elevated tier. *Examples:* dual-human review of every agent action that consumes the waived claim; restricted scope (the waived claim may only be used for advisory, not action); enhanced monitoring on outputs that depend on the claim; mandatory secondary citation requirement.

**Remediation plan.** A specific plan for earning the claim's tier through legitimate corroboration and validation before the waiver expires. The plan must name an owner, a target completion date that precedes the expiry date, and the specific evidence required (which corroborating sources, what validation event under P13).

**Expiry date.** No waiver exceeds 90 days from issue date. Extensions require escalation to the accountable human (the system steward or domain governance lead) with a written rationale; renewals are not routine. An expired waiver without remediation immediately reverts the claim to its earned tier; if the consuming workflow depended on the elevated tier, that workflow's claims become **non-operational** until the underlying tier is re-earned through corroboration and a P13 validation event.

**Linked claim.** The specific claim being waived, by claim identifier, with the earned tier and the waived tier explicitly recorded.

### Lifecycle

A waiver moves through the same five states as the ASDLC waiver: Issued → Active → Expiring → Expired-without-remediation OR Closed. The Curate stage is responsible for tracking waiver state alongside its other quality functions. Expiring-state waivers (within 30 days of expiry) are surfaced to the waiver owner and to the consumer workflow's accountable human.

### Portfolio governance

Tier waivers accumulate. Portfolio-level tracking is a Revision authority responsibility:

- More than 3 active tier waivers per domain at any time indicates a curation capacity problem (P12 — unfunded mandates) or an over-aggressive consequence-class assignment.
- More than 20% of a domain's claims at a single waived tier indicates a systemic gap in corroboration or validation evidence — the tier criteria may be miscalibrated, or the domain may lack the corroborating sources needed.
- Repeated waivers on the same claim across consecutive cycles indicate that the remediation plan is not real. Such claims are escalated to the system steward, not re-waived.

> **DRAFT — author review needed.** The 90-day cap and portfolio thresholds (3 per domain, 20% concentration) are starting points modelled on the ASDLC waiver-governance defaults. Authors should confirm whether IGM-specific calibration (e.g. shorter cap for Validated → Foundational waivers, longer for Provisional → Emerging) is warranted.

Cross-references: [governance/governance-integration-note.md](governance/governance-integration-note.md) (planned) for how an Epistemic Tier Waiver interacts with AEnt-M consequence-class accountability and AEM Tier 4 envelopes; [governance/authority-accountability-matrix.md](governance/authority-accountability-matrix.md) (planned) for Revision authority's role in tier-waiver decisions; [governance/composition-rule.md](governance/composition-rule.md) (planned) for how a waived tier participates in the autonomy × epistemic × consequence composition.

---

## Authority Continuity

The four governance authorities (Semantic, Assertion, Inference, Revision) are functional roles, not job titles, and the IGM allows them to be held by named individuals or named roles. In practice, individuals are unavailable (leave, departure, illness, role change) and roles fall vacant. Without continuity rules, a single absence can halt curation, claim promotion, or contradiction resolution for a domain — silently degrading the substrate without any visible governance failure.

This section specifies the minimum continuity requirements for each of the four authorities, plus a portfolio limit on Revision authority load.

### Named alternate per authority

For every active assignment of any of the four authorities to a named individual, an **alternate** must also be named at the time of assignment. The alternate is a peer with equivalent domain familiarity, recorded in the authority register alongside the primary. The alternate is not a backup contact — they are an authorised acting authority who steps in under defined trigger conditions.

### Activation trigger

The alternate activates when the primary is unavailable for **more than 5 business days** (planned absence such as scheduled leave) or **immediately** (unplanned unavailability — illness, urgent reassignment, departure). Activation is recorded in the authority register with the activation date and expected duration. While the alternate acts, all governance actions taken under that authority bear the alternate's identity in the audit trail, not the primary's.

### Annual review

Every authority assignment, including the named alternate, is reviewed annually. The review confirms that primary and alternate are still in role, still available, and still domain-current. **Gaps** — a primary or alternate who has left the firm, changed role, or otherwise become unavailable — are escalated within 5 business days of detection to the system steward, who is accountable for re-assignment. A domain operating with an unfilled authority slot is operating below the IGM minimum bar (P6 — four authorities govern the graph) and must be flagged in the next governance review.

### Revision authority portfolio limit

The Revision authority is the most load-sensitive of the four — challenge handling, contradiction resolution, epistemic-tier downgrade, decay management, and now Epistemic Tier Waiver ownership all flow through it. A single Revision authority may concurrently hold the role for **no more than three domains**. Above three, response time on revisions degrades and tier waivers accumulate at the portfolio level (see Epistemic Tier Waiver portfolio governance, above). Implementations must track Revision authority load and reassign when the cap is approached.

> **DRAFT — author review needed.** The 5-business-day activation trigger and the 3-domain Revision authority cap are starting points. Authors should confirm whether different caps apply to different authority types (Semantic and Inference are typically lower-volume; Assertion may exceed 3 domains depending on automation level).

### Continuity log

Authority activations, reviews, and re-assignments are recorded in a **Continuity log** maintained as part of the governance register. The log shows, per authority, per domain, the current primary, the current alternate, the most recent annual review date, and any active activation. Auditors and supervisory examiners can read continuity from this log as a single artefact.

Cross-references: [governance/authority-accountability-matrix.md](governance/authority-accountability-matrix.md) (planned) for how IGM authority continuity interacts with AEnt-M consequence-class roles, ASDLC stewards, and APLC product roles.

---

## Common failure patterns

**Intelligence theatre.** Governance structures exist on paper. Authorities are named. Processes are documented. But no claims are actually being revalidated, no contradictions are being reviewed, and no engagement feedback is being captured. The governance is performative. Test: can the system answer IGQ-24 (epistemic debt load) with real numbers? If not, governance is theatrical.

**Authority vacuum.** Governance authorities are assigned but not empowered. The semantic authority cannot enforce ontological decisions because the delivery team overrides them. The revision authority cannot demote claims because stakeholders resist losing "their" knowledge. Test: has any authority exercised a governance decision that was operationally inconvenient in the last quarter?

**Decay denial.** The organization acknowledges decay in principle but does not fund revalidation in practice. Decay schedules exist. Revalidation staff does not. Claims silently expire while the graph reports healthy metrics because nobody is measuring staleness. Test: what percentage of claims have been revalidated within their declared window?

**Over-governance.** The opposite failure. Every claim requires committee review. Ingestion takes weeks. The graph is small, perfect, and irrelevant — it cannot keep pace with the operational reality it is supposed to govern. Test: is the graph growing at a rate sufficient to cover the domains it serves?

**Feedback starvation.** The lifecycle runs but the feedback loops are closed. Engagements consume from the graph but do not feed back into it. The graph reflects what was true when it was built, not what the most recent engagement discovered. Test: when was the last claim added or updated through engagement feedback?

---

*This is an implementation guide for the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
