# Intelligence Governance Manifesto — Companion Guide

**Witold Reichhart and Arnaud Gelas**

This guide provides operational detail for the concepts introduced in the manifesto. It covers the claim model, the memory spectrum, worked examples, engagement archetypes, and boundary conditions for regulated industries.

---

## The Claim Model

The atomic unit of governed intelligence is the claim — a discrete, verifiable assertion carrying metadata that makes it governable. Documents are sources. Claims are what the system reasons over. A claim that cannot be validated, scoped, or updated independently is not a governed claim — it is text.

### Claim structure

Every governed claim carries ten properties:

**Assertion** — The content of the claim. Example: "CSDR imposes cash penalties on settlement fails, calculated daily at CSD-set rates."

**Type** — What kind of claim this is: Regulatory, Operational, Technical, Domain-mechanical, or External-intelligence.

**Source** — Where the claim originated. Example: EU Regulation 909/2014, Article 7(2).

**Provenance chain** — How the claim arrived in the graph: source → extraction method → validation steps → current state.

**Confidence level** — How much the system trusts the claim: Provisional → Candidate → Confirmed → High Confidence → Authoritative (see below).

**Scope** — Where the claim is valid: jurisdiction, entity, process, system, temporal boundary, authority boundary. Example: Jurisdiction: EU. Process: settlement. System: TARGET2-Securities.

**Temporal validity** — When the claim is/was true. Includes valid-from date and decay class (regulatory, operational, external) determining revalidation schedule.

**Contradiction status** — Whether conflicting claims exist. If active, typed as: jurisdictional, temporal, logical, scope, or extraction.

**Dependencies** — What other claims this one rests on. Tracked for cascade analysis — if a dependency's confidence drops, everything downstream is flagged.

**Governance status** — What action may be taken from this claim: Searchable, Recommendable, Reasoning-eligible, Action-eligible, or Regulatory-evidence.

### What makes a claim governable

A claim is governable when it can be independently validated, updated, or contradicted without affecting unrelated claims. "CSDR imposes cash penalties on settlement fails" is governable. "Settlement is complex and evolving" is not — it cannot be invalidated, scoped, or connected to anything actionable.

The test: can a domain expert confirm or deny this specific assertion? Can a regulatory change invalidate it? Can another claim contradict it? If yes to any of these, it is a claim. If no to all three, it is commentary.

### Confidence levels

Confidence is earned through a deterministic process, not assigned by human judgment.

| Level | Criteria | Permitted use |
|---|---|---|
| **Provisional** | Source identified, provenance recorded, no validation | Search results with caveat. Not for agent reasoning. |
| **Candidate** | Passed structural checks (type, scope, temporal validity), awaiting expert review | Search results. Human-reviewed recommendations. Not for agent action. |
| **Confirmed** | Expert-validated by one qualified domain practitioner | Search. Recommendations. Agent reasoning with confidence flag. |
| **High Confidence** | Corroborated by two or more independent sources | Search. Recommendations. Agent reasoning. Agent action with audit trail. |
| **Authoritative** | Corroborated, stable over time, traceable to primary regulatory or institutional source | Full use including regulatory evidence and autonomous agent action. |

Confidence moves in both directions. A High Confidence claim that loses a corroborating source drops to Confirmed. An Authoritative claim whose regulatory basis changes drops to Candidate pending revalidation.

Corroboration requires independent origin. Two documents citing the same source count as one corroboration. An AI extraction and its source document count as one corroboration. Multiple copies of the same LLM-generated output count as zero corroboration.

### Confidence-to-action thresholds

The higher the autonomy of the consumer, the stronger the epistemic requirements:

| Consumer type | Minimum confidence for action | Rationale |
|---|---|---|
| Human expert reviewing results | Provisional | Expert can compensate for uncertainty |
| Human with AI recommendation | Candidate | Recommendation carries implicit authority |
| Agent reasoning within human review | Confirmed | Agent conclusions are checked before action |
| Agent acting autonomously | High Confidence | No human compensation for bad knowledge |
| Regulatory evidence submission | Authoritative | Regulatory standard of proof |

---

## The Memory Spectrum: L1, L2, L3

Intelligence in a governed system operates at three layers. Each has different characteristics, different governance requirements, and different decay profiles.

### L1: Working Memory — Claims at the Point of Decision

What the agent or practitioner has loaded in active context at the moment of action. L1 is a governed window into L2 and L3, filtered by task scope, authorization level, and recency.

**Characteristics:** Small. Relevant. Current. Scoped to the immediate task. Refreshed per decision cycle.

**Governance concern:** What gets loaded into L1 determines the quality of every decision. If working memory includes stale claims, low-confidence assertions, or out-of-scope knowledge, the decision inherits those defects — regardless of how good the reasoning is.

**Controls:** Scope-match enforcement (claims must match the task's declared scope). Freshness gates (stale claims flagged or excluded). Confidence floors (minimum confidence for inclusion varies by action type). Contradiction surfacing (if loaded claims contradict each other, the contradiction is visible, not silently resolved).

### L2: Institutional Memory — The Governed Domain Graph

The curated, validated, connected knowledge that the institution has accumulated across engagements, regulatory cycles, and operational history. L2 is the domain graph — the governed substrate.

**Characteristics:** Large. Structured. Continuously maintained. Decay-managed. Contradiction-aware.

**Governance concern:** L2 is where epistemic debt accumulates. Every claim that silently goes stale, every contradiction that goes untyped, every dependency chain that goes unchecked adds to the debt. L2 governance is the system's immune function.

**Controls:** The full Governed Intelligence Lifecycle operates on L2. Ingest controls what enters. Consolidate structures it as claims. Curate maintains its integrity. Expand grows it beyond what was explicitly put in. Apply governs what leaves for L1.

### L3: Foundational Intelligence — Principles, Archetypes, Boundary Conditions

The deep structural knowledge that changes rarely but shapes everything: domain mechanics, regulatory architectures, institutional patterns, professional archetypes. L3 is the geological layer — it moves slowly but everything above rests on it.

**Characteristics:** Stable. Deeply connected. High confidence. Rarely updated but when it changes, everything above may shift.

**Governance concern:** L3 changes are rare but high-impact. When a foundational regulatory framework changes (Basel III to Basel IV, MiFID II amendments, new EU AI Act obligations), the cascading effects touch every L2 claim that depends on the changed L3 structure.

**Controls:** Change detection with cascade analysis. When an L3 claim changes, the system traces forward through every L2 claim that depends on it and flags them for revalidation. L3 revalidation is always human-reviewed — automated revalidation is not appropriate for foundational claims.

### How the layers interact

L3 provides the structural foundation. L2 builds institutional knowledge on that foundation. L1 selects from L2 what is relevant to the current decision.

A worked example: An agent is advising on settlement penalty exposure.

- **L3** contains: CSDR regulatory architecture, penalty calculation methodology, CSD fee structures (foundational, rarely changing)
- **L2** contains: Current penalty rates by CSD, known exception patterns, operational workaround claims validated by practitioners, cross-domain edges linking settlement penalties to collateral management impacts (institutional knowledge, curated and maintained)
- **L1** loads: The specific client's settlement volumes, applicable CSD, current penalty rates for that CSD, known exception patterns for that client type, relevant contradiction flags (working memory for this specific advisory task)

If the agent acts on L1 that was correctly assembled from current L2 built on valid L3, the advice is traceable, auditable, and institutionally grounded. If any layer is defective — stale L3, polluted L2, mis-scoped L1 — the defect propagates into the advice.

---

## Engagement Archetypes

Intelligence governance does not operate the same way in every engagement. Four archetypes describe different governance profiles.

### Archetype 1: Domain Entry

First engagement in a new domain. The graph is sparse or empty. Almost everything is being built for the first time.

**Governance profile:** Heavy ingestion, heavy consolidation, light curation (not enough to curate yet), heavy expansion (identifying what the graph does not yet know). Entity resolution is the critical bottleneck — two to four days of domain expert time for initial resolution.

**Risk:** Building fast on unvalidated foundations. The pressure to populate the graph quickly can compromise provenance discipline. Every shortcut taken during domain entry becomes epistemic debt that compounds through every subsequent engagement.

**Minimum bar:** No claim enters without source provenance. No entity is unified without confidence scoring. Contradictions are typed even if resolution is deferred.

### Archetype 2: Domain Deepening

Subsequent engagements in an established domain. The graph has coverage. The task is enrichment, validation against operational reality, and identifying what the existing graph gets wrong.

**Governance profile:** Moderate ingestion (new material fills known gaps), heavy consolidation (connecting new claims to existing structure), heavy curation (each engagement tests existing claims against operational reality), moderate expansion.

**Risk:** Stale claims surviving because they look complete. Domain deepening is where decay monitoring earns its investment — the team encounters existing claims that look valid but have silently expired.

**Minimum bar:** Every engagement includes a structured feedback session at mid-point and close. Claims that the engagement contradicts are flagged for revalidation, not silently worked around.

### Archetype 3: Cross-Domain Extension

The engagement spans two or more domains that were previously governed independently. Settlement meets collateral management. Regulatory reporting meets operational risk.

**Governance profile:** Light ingestion (both domains exist), heavy consolidation (building cross-domain edges that did not exist), heavy curation (contradictions between domain-specific claims surface at boundaries), heavy expansion (the cross-domain space is where the most valuable new knowledge lies).

**Risk:** Scope confusion. A claim validated in one domain may not be valid when applied across the boundary. Scope metadata becomes critical — every cross-domain edge must carry scope qualifiers.

**Minimum bar:** Cross-domain claims carry explicit scope limitations. No claim is promoted to High Confidence based on single-domain evidence when it is being used in a cross-domain context.

### Archetype 4: Regulatory Change

A regulatory change triggers revalidation across the affected graph. The engagement is not building new knowledge — it is testing whether existing knowledge survives the change.

**Governance profile:** Heavy curation (cascade analysis from the changed regulatory claim through all dependencies), moderate consolidation (new regulatory claims replacing superseded ones with tracked succession chains), light ingestion (the regulatory text itself), heavy expansion (identifying second-order effects the initial cascade analysis missed).

**Risk:** Incomplete cascade propagation. A regulatory change touches more than the directly affected claims. Second-order and third-order dependencies are where the real risk lies — the claim two hops away that nobody flagged.

**Minimum bar:** Cascade analysis runs to exhaustion, not to a fixed depth. Every affected claim is reviewed. Supersession chains are maintained — the old claim is demoted, not deleted.

---

## Authority Conflicts and Escalation

The four governance authorities (semantic, assertion, inference, revision) will conflict. A semantic authority decision to decompose a hub node may be challenged by an assertion authority who maintains the unified concept is correct. An inference authority may flag a reasoning chain as invalid that revision authority has already approved.

**Escalation rules:**

Within-scope conflicts (two authorities disagree about a claim within one domain) are resolved by the assertion authority for factual disputes and the semantic authority for structural disputes. If they disagree with each other, the revision authority adjudicates.

Cross-scope conflicts (a decision in one domain affects governance in another) are escalated to the knowledge governance committee — or whatever institutional body has cross-domain authority. The key constraint: escalation has a deadline. A conflict that remains unresolved for more than 10 business days must be escalated. A conflict that remains unresolved for more than 30 business days triggers a temporary governance hold on affected claims — they remain in the graph but are flagged as governance-pending, which lowers their effective confidence for agent action thresholds.

No authority can unilaterally promote a claim to Authoritative or unilaterally dispose of a claim with active downstream dependencies. Both actions require two-authority agreement.

---

## Practitioner Knowledge: Barriers and Realistic Capture

The manifesto describes "Capture" mode — expert knowledge sessions with practitioners. This is the right mechanism. It will face institutional resistance that the implementation must anticipate.

**Trading desks** will resist documenting unwritten market knowledge that constitutes competitive advantage within the firm. Do not position capture sessions as knowledge extraction. Position them as quality assurance — the desk is validating or correcting claims the graph already contains, not volunteering new knowledge under documentation liability.

**Operations teams** will resist formally attesting to workarounds that create documentation liability — "we sometimes bypass this CSD requirement because it causes false failures" is knowledge the team holds but will not sign. Capture this through structured inquiry about what the graph gets wrong, not through direct attestation. The claim enters as Provisional with "operational practice — unattested" provenance, not as a validated operational truth.

**Compliance teams** will resist attesting to interpretations that could be used against the firm in examination. Frame compliance capture as recording the interpretation landscape at a point in time, scoped to the current regulatory state. The claim carries temporal validity and a note that it reflects the firm's interpretation as of the capture date.

The general principle: capture is a governance conversation, not a deposition. The system must make it safe for practitioners to contribute without creating personal or institutional liability. Claims captured from practitioner sessions carry their own provenance type and cannot be promoted to High Confidence without independent corroboration — the practitioner's contribution is valuable but is a point of view, not ground truth (Principle 8).

---

## Boundary Conditions for Regulated Industries

Intelligence governance does not solve every problem in regulated AI deployment. These boundaries define where the manifesto's scope ends.

**Model governance is adjacent, not included.** This manifesto governs the intelligence substrate — what agents know. Model governance — bias testing, fairness auditing, performance monitoring, model validation — is a separate discipline with its own established frameworks (SR 11-7, EU AI Act model requirements). The manifesto intersects model governance at the point where model outputs enter the intelligence graph: AI-extracted claims require synthetic-origin labeling and cannot be self-corroborating.

**Data governance is prerequisite, not replaced.** Data quality, master data management, data lineage at the record level — these are prerequisites for intelligence governance, not things it replaces. A governed intelligence graph built on ungoverned data inherits every defect in the underlying data estate.

**The manifesto does not determine compliance.** It provides governance architecture that regulated industries need. Whether a specific implementation satisfies specific regulatory requirements is a compliance determination that requires domain-specific legal and regulatory analysis. The manifesto structures the system; the compliance team determines whether the structure satisfies the regulation.

**Human expertise is augmented, not replaced.** The governed intelligence graph does not replace domain experts. It structures, validates, connects, and maintains what they know — and surfaces what they need — so that institutional knowledge survives individual departures, scales across engagements, and is available to agents operating in regulated workflows. The expert's judgment remains the validation authority for operational reality claims.

**Perfect knowledge is not the goal.** The system should be safely incomplete rather than falsely complete. A governed graph that accurately represents its own gaps — declaring what it does not know — is more trustworthy than one that appears comprehensive but contains silent staleness, untyped contradictions, and untraced provenance.

---

*This is a companion to the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
