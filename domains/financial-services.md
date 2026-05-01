# Intelligence Governance in Financial Services

**Domain mapping for the Intelligence Governance Manifesto**

This document maps the manifesto's twelve principles to the regulatory and operational context of financial services. It identifies where each principle connects to existing regulatory requirements and where it addresses gaps that current frameworks leave open.

Intelligence governance does not claim to satisfy these regulations. It provides an architectural framework designed to support the knowledge-substrate requirements that these regulations increasingly imply but do not specify how to implement. Compliance determinations require domain-specific legal and regulatory analysis.

---

## Regulatory context

Financial services intelligence governance operates under overlapping regulatory obligations:

| Regulation | Scope | Intelligence governance relevance |
|---|---|---|
| **EU AI Act** (phasing in 2025-2027) | AI systems in EU, risk-classified | High-risk system requirements: risk management, technical documentation, human oversight, data governance. Intelligence governance is designed to support the substrate architecture these requirements imply. |
| **SR 11-7** (Federal Reserve) | Model risk management in US banking | Model validation, governance, documentation. Intelligence governance extends SR 11-7's logic from model risk to the knowledge substrate models act on — what we call epistemic operational risk. |
| **DORA** (EU, Jan 2025) | Digital operational resilience | ICT risk management, third-party risk, incident reporting. Intelligence governance addresses knowledge infrastructure as operational infrastructure subject to resilience requirements. |
| **MiFID II** | Investment services in EU | Best execution, suitability, record-keeping, transparency. Intelligence governance provides claim-level audit trails for AI-assisted investment advice. |
| **Basel III/IV** | Capital adequacy, risk management | Risk data aggregation (BCBS 239), internal model governance. Intelligence governance extends risk data principles to knowledge substrate governance. |
| **GDPR** | Personal data protection in EU | Data subject rights, retention, erasure. Intelligence governance must support governed disposition — demote, archive, seal, anonymize, dispose — as first-class operations. |

---

## Principle-by-principle mapping

### Principle 1: The claim is the unit

**FS application.** Regulatory guidance is currently governed at the document level — a firm "has" the MiFID II suitability requirements documented somewhere. Intelligence governance moves this to claim level: "MiFID II Article 25(2) requires that investment firms obtain necessary information regarding the client's knowledge and experience" is a governed claim with provenance, scope (EU, investment services), temporal validity (since January 3, 2018), and confidence level (Authoritative — primary regulatory source).

**Regulatory connection.** BCBS 239 (Principles for Effective Risk Data Aggregation) already requires that risk data be "accurate, complete, and timely." The claim model operationalizes this at the knowledge level — each claim carries the metadata needed to assess accuracy (provenance, confidence), completeness (scope, contradictions), and timeliness (temporal validity, decay monitoring).

**Gap addressed.** Current FS knowledge management tracks documents. When an agent acts on a claim extracted from a document, there is no governance at the claim level — no way to know whether the specific assertion is current, scoped correctly, or contradicted by another source. The claim model fills this gap.

### Principle 2: Provenance is non-negotiable

**FS application.** Regulatory examinations routinely ask: "How did you arrive at this conclusion?" and "What information was this decision based on?" When agents participate in advisory, trading, or compliance workflows, the provenance chain from action to claim to source must be reconstructable. Every claim in the intelligence graph carries source, extraction method, and validation history.

**Regulatory connection.** EU AI Act Article 13 (transparency), MiFID II record-keeping requirements, SR 11-7 documentation requirements for model inputs. DORA Article 11 requires ICT systems to maintain "sufficient and appropriate records" — intelligence governance extends this to knowledge infrastructure.

**Gap addressed.** Current AI audit trails typically record model inputs and outputs. They do not record the provenance of the knowledge those inputs were drawn from. A claim with broken provenance — no traceable path from assertion to source — cannot satisfy regulatory examination standards.

### Principle 3: Confidence is earned, not assigned

**FS application.** A compliance officer's assertion about regulatory interpretation carries a different confidence profile than a published regulatory text. Both may be correct; they have different evidentiary standing. The five confidence levels (Provisional through Authoritative) map to FS decision-making: a Provisional claim is usable for internal research but not for client-facing advice or agent action.

**Regulatory connection.** SR 11-7 requires that model inputs be "appropriate for the model's intended use" and that "uncertainty about inputs" be assessed. Intelligence governance operationalizes this through confidence levels that gate what actions may be taken on each claim.

**Gap addressed.** Current systems treat all knowledge as equally reliable once it enters the system. An AI-extracted claim from an analyst note and a direct regulatory citation carry the same weight in retrieval. Confidence scoring prevents agents from acting on weakly supported claims with the same authority as well-supported ones.

### Principle 4: Contradictions are information

**FS application.** Financial services is full of legitimate contradictions: US and EU regulatory requirements that conflict, operational reality that diverges from documented procedures, competing interpretations of evolving guidance. A firm's OTC derivatives documentation may say one thing while its operational practice does another — and both may be defensible in different contexts.

**Regulatory connection.** DORA incident reporting requires identifying root causes. Untyped contradictions in the knowledge substrate are a root cause category that current incident analysis frameworks miss. MiFID II best-execution obligations require considering multiple competing factors — contradictions in market data or execution venue assessments are expected, not errors.

**Gap addressed.** Current knowledge systems force resolution — one answer per question. Intelligence governance types contradictions (jurisdictional, temporal, logical, scope, extraction) and preserves them with their context. An agent operating on a graph with typed contradictions can reason about which interpretation applies in the current scope rather than receiving a silently arbitrated single answer.

### Principle 5: Intelligence decays. Govern the decay.

**FS application.** Decay rates in financial services vary by claim type:

| Claim type | Decay rate | Trigger |
|---|---|---|
| Regulatory framework structure | Years | Legislative amendment, framework revision |
| Regulatory interpretation | Months | Enforcement action, supervisory guidance, court ruling |
| Operational procedures | Months | System migration, organizational restructure, process redesign |
| Market intelligence | Weeks | Market event, vendor change, competitive action |
| Client-specific operational claims | Weeks | Staffing change, system upgrade, client restructure |

**Regulatory connection.** BCBS 239 Principle 3 (timeliness) requires that risk data be "available on a timely basis." Intelligence governance extends timeliness from risk data to the knowledge substrate — a stale claim used in a timely data pipeline is a governed failure.

**Gap addressed.** Current knowledge management systems have no decay model. Knowledge enters and persists until someone manually notices it is wrong. In an agentic environment, stale claims are not just inefficient — they produce automated action on expired knowledge.

### Principle 6: Four authorities govern the graph

**FS application.** In financial services, the four governance authorities map to existing institutional roles:

| Authority | FS mapping | Responsibility |
|---|---|---|
| **Semantic authority** | Enterprise data office / ontology team | What concepts exist in the graph, how they relate, when to decompose hub nodes |
| **Assertion authority** | Domain SMEs, regulatory affairs, compliance | Whether specific claims are accurate within their declared scope |
| **Inference authority** | Model risk, quantitative analytics | Whether reasoning chains across claims are valid, whether confidence propagation is correct |
| **Revision authority** | Knowledge governance committee / CISO for security-sensitive claims | When claims should be superseded, demoted, sealed, or disposed |

**Regulatory connection.** SR 11-7 requires "effective challenge" — independent review of model assumptions and outputs. The four-authority model extends effective challenge from models to the knowledge substrate models operate on.

**Gap addressed.** Current FS knowledge management has no defined authority structure for claim-level governance. Documents have owners. Claims do not. The four-authority model makes governance accountability explicit at the claim level.

### Principle 7: Acquisition has modes

**FS application.** Four acquisition modes operate in financial services:

- **Harvest:** Structured extraction from regulatory texts, internal policies, system documentation. High-volume, automatable, requires synthetic-origin labeling when AI performs extraction.
- **Extract:** Semi-structured capture from analyst reports, audit findings, examination letters. Requires human review of extraction quality.
- **Capture:** Expert knowledge sessions with practitioners. Settlement operations, trading desk knowledge, compliance interpretation. Voluntary, disclosed, structured as claims rather than transcripts.
- **Emerge:** New claims generated through graph operation — cross-domain edges discovered during query, implications surfaced through causal reasoning, gaps identified through expansion. Requires explicit marking as system-generated.

**Regulatory connection.** GDPR and data protection requirements apply to Capture mode when practitioner knowledge includes information that could identify individuals. Intelligence governance must support governed disposition for claims that intersect personal data obligations.

### Principle 8: Expert knowledge is a point of view, not ground truth

**FS application.** A head of settlement operations knows things no document captures. That knowledge is valuable and governable — but a single expert's operational claim cannot reach Authoritative confidence without independent corroboration. The expert may be right. The system governs the *confidence with which it acts on that claim* based on evidentiary standing, not personal authority.

**Regulatory connection.** SR 11-7 warns against "key person risk" in model governance — over-reliance on individual experts. Intelligence governance extends this to the knowledge substrate: institutional knowledge must not depend on a single person's uncorroborated claims at the highest confidence levels.

### Principle 9: The graph must support structured inquiry

**FS application.** Structured inquiry in FS means answering questions that span domains: "What is our total exposure to CSDR penalty risk across all CSDs, including second-order effects through collateral management?" This requires cross-domain linking (settlement → penalties → collateral → liquidity), gap analysis (which CSDs lack coverage?), and conflict surfacing (do our operational claims about CSD exception handling contradict the regulatory text?).

**Regulatory connection.** BCBS 239 Principle 6 (adaptability) requires that risk data systems "be adaptable to changes in the regulatory environment." Structured inquiry over a governed graph supports adaptability because new regulatory questions can be answered through graph traversal rather than new data collection exercises.

### Principle 10: Every engagement feeds the graph

**FS application.** Three structured capture points per engagement: at start (what does the graph get wrong about this client's operational reality?), at mid-point (what has the team learned that contradicts or extends existing claims?), at close (what would the next team need to know?). Without these feedback loops, the graph fossilizes. With them, each engagement compounds the institutional substrate.

**Regulatory connection.** SR 11-7 requires "ongoing monitoring" of model performance. Intelligence governance extends this to ongoing enrichment of the knowledge substrate — the model may be performing correctly on stale knowledge, which SR 11-7's model-focused monitoring would not catch.

### Principle 11: Traceability is the response to acceleration

**FS application.** When an agent recommends a trade, a compliance classification, or a settlement configuration, the reasoning chain must be traceable from action through reasoning through claims through provenance to source. In financial services, this traceability must satisfy regulatory examination standards — not just internal logging but reconstructable audit trails with confidence levels, scope qualifications, and contradiction flags at every step.

**Regulatory connection.** EU AI Act Article 14 (human oversight for high-risk systems), MiFID II suitability record-keeping, SR 11-7 documentation requirements. Intelligence governance is designed to support the substrate-level traceability that these regulations increasingly demand.

### Principle 12: No unfunded mandates

**FS application.** Intelligence governance requires dedicated budget, staffing, and institutional commitment — not a side project run by the architecture team when they have spare capacity. Curation alone requires continuous domain expert involvement. In financial services, where regulatory penalties for knowledge failures can be substantial, the cost of intelligence governance is measured against the cost of epistemic operational risk.

**Regulatory connection.** DORA Article 5 requires that ICT risk management frameworks be "adequately resourced." Intelligence governance is knowledge infrastructure — under DORA's logic, its resourcing is not optional once agents operate on it in regulated workflows.

---

## Epistemic operational risk in FS

The manifesto introduces epistemic operational risk as a new category: the risk of institutional harm from acting on defective knowledge. In financial services, this surfaces in specific ways:

**Settlement risk.** An agent configuring settlement parameters based on stale operational claims about CSD behavior produces configurations that work under normal conditions and fail under stress — exactly the failure mode regulators are most concerned about.

**Advisory risk.** An agent providing investment advice based on a regulatory interpretation that has been superseded by a recent enforcement action gives advice that was correct six months ago and wrong today.

**Compliance risk.** An agent classifying transactions for regulatory reporting based on a jurisdiction-scoped claim applied outside its declared scope produces misclassifications that are individually plausible but institutionally wrong.

**Model risk extension.** SR 11-7 governs model risk. Epistemic operational risk extends the same logic to the knowledge substrate: even a well-validated model produces bad outputs when operating on stale, polluted, or mis-scoped knowledge.

---

*This is a domain mapping for the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*
