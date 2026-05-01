# Intelligence Governance — Implementation Guide

**Witold Reichhart and Arnaud Gelas**

This guide provides an adoption path for intelligence governance. It is organized by maturity level, starting from minimum viable governance through to full operational governance in regulated industries.

---

## Starting principles

Intelligence governance does not require a complete implementation to be useful. It does require a minimum threshold to be honest.

A system that claims governance but cannot answer "where did this claim come from?" and "is it still current?" does not have governance. It has documentation with a governance label.

Start where you are. Build governance incrementally. Do not wait for the perfect system before governing the one you have.

---

## Minimum viable intelligence governance

The smallest useful implementation. Suitable for a team beginning to build a domain graph or retrofitting governance onto an existing knowledge base.

**You have minimum viable governance when:**

1. Every claim has a recorded source (Principle 2 — provenance at entry)
2. Every claim has a type and a declared scope (Principle 1 — the claim is the unit)
3. Every claim has a confidence level, earned through defined criteria (Principle 3)
4. Claims approaching their revalidation deadline are flagged (Principle 5 — decay awareness)
5. A named person is responsible for claim accuracy in each domain (Principle 6 — assertion authority at minimum)

**You do not yet need:** Full four-authority governance, typed contradictions, cascade analysis, cross-domain linking, automated decay monitoring, L1/L2/L3 separation, engagement feedback loops.

**Time to implement:** 2-4 weeks for a single domain, assuming the knowledge base already exists in some form. The work is tagging, not building.

---

## Five maturity levels

### Level 1: Ad hoc

Knowledge exists in documents, wikis, SharePoint, Confluence, individual expertise. No claim-level governance. No provenance tracking. No decay management. AI systems retrieve from document stores with no governance at the retrieval level.

**Indicators:** Knowledge quality depends on who you ask. Different team members give different answers about the same domain question. Nobody knows which operational procedures are current. Onboarding takes months because institutional knowledge is distributed across people and implicit.

**Risk profile:** High epistemic operational risk. AI agents operating at this level are retrieving from ungoverned sources and treating all retrieved content as equally reliable.

### Level 2: Structured

Knowledge has been extracted into a structured form — a knowledge graph, a structured database, a governed taxonomy. Claims exist as identifiable units. Provenance is recorded at ingestion. Basic scope metadata exists.

**Indicators:** You can point to where institutional knowledge lives. Claims have sources. The structure is queryable. But confidence is informal ("we think this is right"), decay is unmanaged (claims are current until someone notices they are not), and contradictions are resolved silently rather than preserved.

**Risk profile:** Medium-high. Better than Level 1 because the structure is explicit, but confidence and decay governance are missing. Agents operating at this level may act on stale or weakly supported claims without knowing it.

### Level 3: Governed

Claims carry confidence levels earned through defined criteria. Decay monitoring is active — claims are revalidated on schedule. The four governance authorities are assigned. Contradictions are typed and tracked. Engagement feedback loops exist. Provenance chains are complete and auditable.

**Indicators:** You can answer IGQ-01 through IGQ-10 (see governance/queries.md). You know what is stale, what is contradicted, and what confidence level each claim carries. Named authorities are accountable for semantic, assertion, inference, and revision governance.

**Risk profile:** Medium. Governance is active but may not cover the full graph. Some domains are well-governed; others lag. The primary risk is uneven coverage rather than absent governance.

### Level 4: Operational

Intelligence governance is embedded in operational workflows. Agents respect confidence-to-action thresholds. Epistemic circuit breakers halt action on defective knowledge. L1 working memory is scope-checked and freshness-gated. Cross-domain linking is active. Cascade analysis runs on confidence changes. The system can answer all 25 canonical queries.

**Indicators:** Agent actions are traceable to specific claims with specific confidence levels. Governance interventions are measurable — you can track how often the system blocks or escalates based on epistemic quality. Epistemic debt is measured and managed as a system health metric.

**Risk profile:** Low-medium. Governance is operational and measurable. Residual risk comes from edge cases, novel domains not yet covered, and L3 foundational changes whose cascading effects are partially tracked.

### Level 5: Adaptive

The intelligence governance system learns from its own operation. Decay models are calibrated by observed decay rates rather than preset schedules. Confidence propagation is refined by tracking which prediction-error patterns correlate with which governance failures. The system identifies its own gaps — domains where coverage is thin, claim types where staleness outpaces revalidation capacity, cross-domain boundaries where scope confusion is most frequent.

**Indicators:** Governance improves through use, not through periodic review. The system surfaces its own weaknesses. Epistemic debt trends downward over time. New domains are onboarded faster because governance patterns from existing domains transfer.

**Risk profile:** Low. Residual risk is genuinely novel situations the system has not encountered — irreducible uncertainty rather than governance failure.

---

## Adoption sequence

### Phase 1: Foundation (weeks 1-4)

**Goal:** Minimum viable governance for one domain.

**Actions:**
- Select a single domain with high operational risk and existing knowledge assets (in FS: settlement operations, regulatory reporting, or compliance interpretation)
- Extract claims from existing documentation. Tag with source, type, scope, and initial confidence
- Assign assertion authority — one named domain expert per subdomain
- Set decay schedules by claim type
- Implement IGQ-01, IGQ-03, IGQ-10 (provenance, confidence, staleness) as operational queries

**Deliverable:** A governed domain graph for one domain with provenance, confidence, scope, and decay tracking. Level 2 maturity for that domain.

### Phase 2: Governance activation (weeks 5-10)

**Goal:** Full governance for the initial domain. Level 3 maturity.

**Actions:**
- Assign all four governance authorities (semantic, assertion, inference, revision)
- Implement typed contradiction tracking
- Activate decay monitoring with automated alerts
- Run first engagement with structured feedback loop (start, mid-point, close)
- Implement confidence-to-action thresholds for any agents operating on this domain
- Deploy IGQ-01 through IGQ-16 as operational queries

**Deliverable:** Active governance with measurable intervention rates. Named authorities. Contradiction tracking. Agent guardrails.

### Phase 3: Operational integration (weeks 11-16)

**Goal:** Intelligence governance embedded in operational workflows. Level 4 maturity.

**Actions:**
- Implement L1 working memory governance (scope-checking, freshness-gating, confidence floors)
- Activate cascade analysis on confidence changes
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
- Establish governance feedback loops that refine confidence propagation, scope enforcement, and cascade analysis based on operational evidence

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
| Agent actions blocked by epistemic circuit breakers | Declining trend | Rising trend |
| Governance interventions per 1000 agent actions | Declining trend | Flat or rising |
| Time to revalidate after regulatory change | <5 business days for directly affected claims | >15 business days |
| Scope-mismatch incidents (claim used outside declared scope) | <1 per month per domain | >5 per month |

---

## Epistemic circuit breakers — operational specification

The manifesto states that the system fails closed when epistemic confidence falls below threshold. This requires operational specification.

**Consequence thresholds** determine when circuit breakers engage. A consequence threshold is the estimated institutional impact of an incorrect action — measured by financial exposure, regulatory risk, client impact, or reputational damage. Each organization defines its own threshold levels. As a starting point:

| Consequence level | Example (FS) | Circuit breaker behavior |
|---|---|---|
| Low | Internal research query, non-client-facing | Log epistemic quality warning. Agent proceeds. |
| Medium | Client recommendation, internal report | Agent pauses. Human reviewer sees epistemic quality summary. Human decides. |
| High | Trade execution, regulatory filing, compliance determination | Agent halts. Named accountable human reviews full reasoning chain with confidence levels, provenance, and contradiction flags. |
| Critical | Cross-border regulatory submission, systemic risk assessment | Agent halts. Two-person review with escalation to governance authority. |

**When the circuit breaks:** The agent does not silently degrade to best-effort. It produces a structured escalation: which claims triggered the breaker, what their confidence levels are, what the specific defect is (staleness, contradiction, scope mismatch, broken provenance), and what action is blocked pending resolution.

**SLA for resolution:** Circuit breaker escalations carry a deadline tied to the operational context. A settlement-related breaker in an active trading window requires resolution within hours. A compliance interpretation breaker outside reporting season may allow days. The SLA is set per workflow, not per breaker type.

---

## Decay triage — managing revalidation at scale

At enterprise scale, the claim graph may contain tens or hundreds of thousands of claims. Revalidating all of them on schedule is not realistic without triage.

**Priority 1: Critical-path claims.** Claims on the active reasoning path of agent workflows currently in production. These are revalidated first and carry the shortest decay windows. At scale, this is typically 5-15% of the graph.

**Priority 2: High-dependency claims.** Claims with many downstream dependents (identified through IGQ-17 and IGQ-18). A stale high-dependency claim is a systemic risk — its blast radius justifies prioritized revalidation. Typically 10-20% of the graph.

**Priority 3: Active-domain claims.** Claims in domains where engagements are currently running or recently completed. These were recently tested against operational reality and should be maintained at high freshness. Typically 20-30% of the graph.

**Priority 4: Dormant claims.** Claims in domains with no current engagements and no active agent workflows. These are revalidated on a longer cycle — quarterly or semi-annually rather than monthly. They retain their last confidence level with a "revalidation pending" flag. If an engagement reactivates the domain, Priority 4 claims are promoted to Priority 3 and revalidated before agent use.

Auto-revalidation handles cases where the signal is unambiguous: if a regulatory source has not been amended since last validation, the decay clock resets automatically. Human review is reserved for ambiguous signals and high-impact claims. In practice, auto-revalidation handles 40-60% of revalidation volume, reducing the human labor requirement to a manageable level.

---

## Common failure patterns

**Intelligence theatre.** Governance structures exist on paper. Authorities are named. Processes are documented. But no claims are actually being revalidated, no contradictions are being reviewed, and no engagement feedback is being captured. The governance is performative. Test: can the system answer IGQ-24 (epistemic debt load) with real numbers? If not, governance is theatrical.

**Authority vacuum.** Governance authorities are assigned but not empowered. The semantic authority cannot enforce ontological decisions because the delivery team overrides them. The revision authority cannot demote claims because stakeholders resist losing "their" knowledge. Test: has any authority exercised a governance decision that was operationally inconvenient in the last quarter?

**Decay denial.** The organization acknowledges decay in principle but does not fund revalidation in practice. Decay schedules exist. Revalidation staff does not. Claims silently expire while the graph reports healthy metrics because nobody is measuring staleness. Test: what percentage of claims have been revalidated within their declared window?

**Over-governance.** The opposite failure. Every claim requires committee review. Ingestion takes weeks. The graph is small, perfect, and irrelevant — it cannot keep pace with the operational reality it is supposed to govern. Test: is the graph growing at a rate sufficient to cover the domains it serves?

**Feedback starvation.** The lifecycle runs but the feedback loops are closed. Engagements consume from the graph but do not feed back into it. The graph reflects what was true when it was built, not what the most recent engagement discovered. Test: when was the last claim added or updated through engagement feedback?

---

*This is an implementation guide for the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
