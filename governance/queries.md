# Canonical Intelligence Governance Queries

**Standard questions that any governed intelligence system must be able to answer.**

These queries define the minimum interrogation capability of an intelligence governance implementation. A system that cannot answer these queries does not have intelligence governance — it has a knowledge base with documentation.

Queries are organized by governance concern. Each query specifies what it asks, why it matters, and what a failure to answer indicates.

---

## Provenance and trust

**IGQ-01: What is the provenance chain for this claim?**
Trace from assertion through extraction method, source document, and original authority. A claim without reconstructable provenance cannot satisfy regulatory examination standards.

**IGQ-02: Is this claim derived from AI extraction? If so, has it been independently validated?**
AI-extracted claims carry synthetic-origin risk. A claim that entered through AI extraction and has not been validated by an independent source or human expert should carry Provisional or Emerging epistemic tier at most.

**IGQ-03: What is the epistemic tier of this claim, and what evidence supports that tier?**
A tier without evidence is opinion. The system must show exactly which corroborating sources, expert validations, structural checks, and (for Validated and above) which recorded validation event produced the current epistemic tier.

**IGQ-04: Which claims in this reasoning chain have the lowest epistemic tier?**
A conclusion cannot rest on a higher tier than its weakest necessary premise. This query identifies the weakest links in any reasoning chain an agent traverses; the chain-level summary it feeds is the *epistemic quality* surfaced at decision time.

**IGQ-05: Has this claim's epistemic tier changed in the last 90 days? In which direction?**
Epistemic-tier trends matter. A claim that was Foundational and is now Validated has a different risk profile from one that has been Validated for two years.

---

## Scope and applicability

**IGQ-06: What is the declared scope of this claim?**
Jurisdiction, entity, process, system, temporal boundary, authority boundary. A claim used outside its declared scope is a governance failure regardless of whether the assertion happens to be correct.

**IGQ-07: Is this claim being used outside its declared scope?**
The system must detect when an agent or query attempts to apply a claim beyond its scope boundaries. This is the single most common knowledge failure in multi-jurisdictional financial services.

**IGQ-08: Which claims in the current working memory (L1) have scope mismatches with the task context?**
At the point of decision, every loaded claim should be scope-compatible with the task. This query surfaces mismatches before they produce action.

---

## Staleness and decay

**IGQ-09: Which claims are within 30 days of their revalidation deadline?**
Early warning for approaching staleness. Claims near their decay window should be flagged for proactive revalidation rather than allowed to silently expire.

**IGQ-10: Which claims have passed their revalidation deadline without being revalidated?**
Active governance failure. Stale claims that remain in the graph at their previous epistemic tier are epistemic debt accumulating in real time.

**IGQ-11: What is the staleness rate across the graph? By domain? By claim type?**
System-level health metric. A graph with 5% stale claims in a well-maintained domain is healthy. A graph with 30% stale claims in an actively used domain is an operational risk.

**IGQ-12: Which stale claims are on the critical path for active agent workflows?**
Not all staleness is equally dangerous. A stale claim about a deprecated system is low risk. A stale regulatory interpretation on the critical path of a compliance workflow is high risk. This query prioritizes revalidation effort.

---

## Contradictions and conflicts

**IGQ-13: What active contradictions exist in this domain scope?**
The system must surface all typed contradictions (jurisdictional, temporal, logical, scope, extraction) within a given scope, with provenance for each conflicting claim.

**IGQ-14: Are there unresolved contradictions on the critical path of the current agent task?**
An agent reasoning through a contradiction it has not been made aware of may select either side arbitrarily. This query ensures contradictions are visible at the point of decision.

**IGQ-15: What is the contradiction type, and does it require resolution or preservation?**
Jurisdictional contradictions (US vs. EU rules) should be preserved. Logical contradictions (two claims that cannot both be true in the same scope) require resolution. The system must distinguish them.

**IGQ-16: Has this contradiction been reviewed by the relevant assertion authority?**
Contradictions without authority review are unmanaged risk. This query tracks governance coverage of identified conflicts.

---

## Dependencies and cascade risk

**IGQ-17: What claims depend on this claim?**
Forward dependency tracing. If this claim is compromised, what else is affected? Critical for assessing the blast radius of any epistemic-tier change.

**IGQ-18: What is the maximum dependency depth in this claim's downstream chain?**
Deep dependency chains amplify cascade risk. A claim with 15 downstream dependents across 5 levels of indirection is systemically important and should be governed accordingly.

**IGQ-19: If this claim's epistemic tier dropped to Provisional, which agent workflows would be affected?**
Impact analysis before it happens. The system should be able to simulate a tier change and identify all affected downstream consumers.

**IGQ-20: Are there circular dependencies in this claim's dependency graph?**
Circular dependencies create governance loops where two claims support each other without independent grounding. They must be detected and resolved.

---

## Agent action governance

**IGQ-21: What claims is this agent currently authorized to act on?**
Scoped by the agent's authorization level, the task context, and epistemic-tier-to-action thresholds. An agent should never act on claims it has not been explicitly authorized to use for action.

**IGQ-22: Has this agent's recommended action been traced to specific claims at sufficient epistemic tier?**
Every agent action recommendation must be traceable to the claims that support it, each meeting the epistemic-tier threshold for the action's consequence class. If any supporting claim falls below threshold, the action should be blocked or escalated.

**IGQ-23: What would change about this recommendation if the lowest-tier supporting claim were removed?**
Sensitivity analysis. If a recommendation depends critically on a single Validated-tier claim and would change without it, that dependency should be visible to the accountable human.

---

## System health

**IGQ-24: What is the current epistemic debt load?**
Composite metric: percentage of stale claims, unresolved contradictions, broken provenance chains, epistemic tiers that have not been reviewed within their decay window, and claims with degraded dependency chains. The system-level indicator of knowledge infrastructure health.

**IGQ-25: What changed in the graph in the last 24 hours / 7 days / 30 days, and what governance actions resulted?**
Change log with governance response. A graph that changes frequently with no governance actions is ungoverned. A graph that never changes is dead. Both are failure modes.

---

## Using the queries

These queries serve three purposes:

**Operational governance.** Run IGQ-09, IGQ-10, IGQ-12, IGQ-14, and IGQ-24 daily. These are the early-warning queries that catch governance failures before they produce action on defective knowledge.

**Agent guardrails.** IGQ-04, IGQ-07, IGQ-08, IGQ-21, IGQ-22, and IGQ-23 should run automatically before any agent action that exceeds a defined consequence threshold. They are the epistemic circuit breakers.

**Audit and examination.** IGQ-01, IGQ-02, IGQ-03, IGQ-06, IGQ-13, and IGQ-25 support regulatory examination readiness. A system that can answer these queries with full traceability satisfies the documentation and transparency requirements that EU AI Act, SR 11-7, and MiFID II impose.

---

*These queries are canonical — implementations may add domain-specific queries but should not remove any from this set. Part of the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
