# Intelligence Governance for Personal Data and the EU Data Act

**Domain mapping for the Intelligence Governance Manifesto**

This document maps the manifesto's twelve principles to systems that process personal data under the EU General Data Protection Regulation (GDPR) and to data-sharing obligations under the EU Data Act (Regulation (EU) 2023/2854, binding since 12 September 2025). It identifies where each principle connects to existing regulatory requirements and where it addresses gaps that current frameworks leave open.

Intelligence governance does not claim to satisfy these regulations. It provides an architectural framework designed to support the knowledge-substrate requirements that these regulations increasingly imply but do not specify how to implement. Compliance determinations require domain-specific legal and regulatory analysis.

> **DRAFT — privacy / data-protection counsel review needed.** This mapping was drafted from public regulatory text and supervisory authority decisions. Items marked DRAFT below should be reviewed by a qualified data-protection officer (DPO) and counsel before operational use.

---

## Regulatory context

Personal-data intelligence governance operates under overlapping regulatory obligations:

| Regulation | Scope | Intelligence governance relevance |
|---|---|---|
| **GDPR Article 5** | Principles relating to processing of personal data | Lawfulness, fairness, transparency, purpose limitation, data minimisation, accuracy, storage limitation, integrity and confidentiality, accountability. Intelligence governance must record each as a structural property of the substrate, not a compliance attestation. |
| **GDPR Article 6** | Lawful basis for processing | Six lawful bases. Intelligence governance must record lawful basis as part of provenance for every personal-data-derived claim. |
| **GDPR Article 9** | Special-category data (health, biometric, genetic, religion, political, etc.) | Default prohibition with narrow exceptions. Intelligence governance must mark special-category claims and constrain agentic action accordingly. |
| **GDPR Article 22** | Automated decision-making, including profiling | Right not to be subject to solely automated decisions producing legal or similarly significant effects, with limited exceptions. Intelligence governance must constrain what agents may do with personal-data-derived claims in solely automated paths. |
| **GDPR Article 25** | Data protection by design and by default | Substrate architecture is design. Intelligence governance is a candidate "by design" measure. |
| **GDPR Article 30** | Records of processing activities | Substrate-level records of processing must reconcile with record-of-processing-activities (ROPA) entries. |
| **GDPR Article 32** | Security of processing | Integrity, confidentiality, availability, resilience. Intelligence governance extends these to the substrate. |
| **GDPR Article 35** | Data Protection Impact Assessment (DPIA) | Required for high-risk processing, including large-scale special-category and Article 22 processing. Intelligence governance produces DPIA-relevant structural evidence. |
| **EU Data Act Articles 3–13** | B2B / B2C data sharing for connected products and related services | Access by users, sharing with third parties on user request, fair-and-non-discriminatory terms. Intelligence governance must support claim-level scoping for sharable vs non-sharable claims. |
| **EU Data Act Articles 14–22** | B2G data sharing for exceptional need | Public-sector access in defined exceptional circumstances. Intelligence governance must support governed disposition for B2G request response. |
| **National DPA enforcement** | Member-state supervisory authority decisions | Italian Garante, French CNIL, Spanish AEPD and others have taken decisions against AI-system operators that touch substrate-level questions. Intelligence governance is designed to produce the evidence such investigations seek. |

DRAFT — counsel review needed: The Data Act's interaction with GDPR (especially where shared "data" includes personal data) is governed by Article 1(3) and recital interactions; institution-specific application requires legal review.

---

## Principle-by-principle mapping

### Principle 1: The claim is the unit

**Personal-data application.** Personal-data systems currently govern at the *record* level — an institution "has" a customer record with attributes. Intelligence governance moves this to claim level: "Subject S has consented to marketing email under lawful basis Article 6(1)(a) on date D, scope = direct-to-consumer offers from controller C, withdrawn date = null" is a governed claim with provenance, scope, temporal validity, and epistemic tier (Foundational — captured at user interface with logged consent ceremony, primary-source traceable, structurally integrated).

**Regulatory connection.** GDPR Article 5(1)(d) (accuracy) and Article 25 (data protection by design) imply assertion-level governance: a record may be partly accurate and partly stale. The claim model expresses this directly.

**Worked example.** A profile attribute "interest = sports" is one claim with one provenance and one decay class; "consent to receive sports newsletter" is a different claim with a different provenance (the consent ceremony) and a different decay class (potentially indefinite or until withdrawal). Treating both as fields of the same record obscures the asymmetry.

**Gap addressed.** Current personal-data systems track records and consent flags. When an agent acts on an extracted attribute, there is no governance at the claim level. The claim model fills this gap and makes Article 25 ("by design") concrete.

### Principle 2: Provenance is non-negotiable

**Personal-data application.** Every personal-data-derived claim must trace to its source — the data-subject submission, the inference engine that derived it, the third-party broker that supplied it — *with the lawful basis that authorised the processing*. Lawful basis is not external metadata; it is part of the provenance chain. A claim whose lawful basis is unknown is, for processing purposes, a claim without provenance.

**Regulatory connection.** GDPR Articles 5(2) and 30 (accountability and ROPA), Article 6 (lawful basis), Article 14 (information when data not obtained from data subject — must include source), and supervisory authority decisions consistently turning on inability to demonstrate where data came from and why processing was lawful.

**Worked example.** An agent personalising offers must reason over claims whose provenance includes lawful basis. If a claim's lawful basis is "legitimate interests" (Article 6(1)(f)) the agent's permitted action set is narrower than if it is "consent" (Article 6(1)(a)) — and entirely different if the underlying claim is special-category under Article 9.

**Gap addressed.** Current AI audit trails record model inputs and outputs but rarely record the lawful basis under which each input was processed. A claim whose lawful basis cannot be reconstructed cannot satisfy ROPA or DPIA evidence requirements when an agent acts on it.

### Principle 3: Epistemic tier is earned, not assigned

**Personal-data application.** A claim asserted by the data subject themselves (e.g. self-declared employment status) carries a different epistemic tier than a claim inferred by a model from behavioural signals. Both may be useful; they have different evidentiary standing for different uses. The four tiers (Provisional → Emerging → Validated → Foundational) gate what actions an agent may take. Inferences that drive Article 22 decisions cannot rest on Provisional or Emerging tiers — Article 22 maps to High consequence, which requires ≥ Validated.

**Regulatory connection.** GDPR Article 5(1)(d) (accuracy), Article 22 (constraints on solely automated decisions). Intelligence governance operationalizes accuracy through tiers that gate action.

**Worked example.** A "high creditworthiness" claim inferred at Emerging tier is suitable for ranking marketing audiences (Medium consequence) but not for declining a credit application (High consequence — requires Validated). Tiering enforces this without ad-hoc per-feature rules.

**Gap addressed.** Current personal-data systems treat all attributes as equally reliable once stored. An attribute self-declared by the subject and one inferred by a profiling model carry the same weight in retrieval. Tiering prevents agents from acting on weakly supported personal-data claims with the same authority as well-supported ones.

### Principle 4: Contradictions are information

**Personal-data application.** Personal data is full of legitimate contradictions: the data subject's correction request contradicts the model's inference; one source says the subject is in country A, another says country B (both may be true at different times); a marketing-consent flag is "yes" in one system and "withdrawn" in another. Auto-resolution destroys the most important signal — including the data subject's right to rectification.

**Regulatory connection.** GDPR Article 16 (rectification) requires that contradictions raised by data subjects be processable and resolvable. Article 5(1)(d) (accuracy) requires that inaccurate data be erased or rectified "without delay." Intelligence governance types contradictions and preserves them with their context, which is a precondition for handling rectification correctly.

**Worked example.** A data subject corrects their date of birth via a DSAR response. The corrected claim must supersede the prior claim — but the prior claim cannot be silently overwritten if downstream agents have already acted on it (e.g. age-gated service decisions). The contradiction must be typed (data-subject correction = temporal supersession plus primary-source promotion to Foundational tier) and the propagation must be governed.

**Gap addressed.** Current personal-data systems force resolution. Intelligence governance preserves contradictions with their type — including data-subject corrections, source-of-truth divergence, temporal supersession, and extraction errors.

### Principle 5: Intelligence decays. Govern the decay.

**Personal-data application.** Decay rates for personal-data claims map to retention rules and to Article 5(1)(e) (storage limitation):

| Claim type | Decay rate | Trigger |
|---|---|---|
| Identity claims (name, date of birth) | Years | Subject correction, life event |
| Contact details | Months | Subject correction, undeliverable signal |
| Consent claims | Until withdrawal or scope expiry | Withdrawal, scope change, regulator action |
| Inferred preferences | Weeks to months | Behaviour change, model retraining, drift |
| Behavioural events | Days to months | Retention policy expiry |
| Special-category claims (Art. 9) | As short as compatible with purpose | Stricter than baseline |

**Regulatory connection.** GDPR Article 5(1)(e) (storage limitation) and Article 17 (right to erasure). Intelligence governance must support governed disposition — demote, archive, seal, anonymise, dispose — as first-class operations that propagate to derived claims.

**Worked example.** A retention policy says behavioural-event claims expire after 24 months. An agent reasoning over a profile must not surface an event at month 25. Decay monitoring per claim type with linkage to retention rules makes this enforceable rather than dependent on a quarterly batch job.

**Gap addressed.** Current personal-data systems apply retention at the table level. Claim-level decay aligns disposition with the actual lawful-basis temporal scope, which Article 5(1)(e) requires.

### Principle 6: Four authorities govern the graph

**Personal-data application.** The four governance authorities map to existing institutional roles:

| Authority | Personal-data mapping | Responsibility |
|---|---|---|
| **Semantic authority** | Data architecture / data dictionary owner | Vocabulary and ontology — what attributes exist, how they relate, how special-category fields are flagged |
| **Assertion authority** | Data steward (for source-of-truth claims); the data subject (for self-asserted claims and corrections); model owner (for inferred claims, with tier ceiling) | Whether specific claims are accurate within their declared scope |
| **Inference authority** | Model risk / responsible-AI / DPO (for Article 22-implicating inferences) | Whether reasoning chains across claims are valid; whether Article 22 thresholds are crossed |
| **Revision authority** | DPO / privacy office (for personal-data disposition); data governance committee | When claims should be superseded, demoted, sealed, or disposed; rectification, erasure, restriction propagation |

**Regulatory connection.** GDPR Articles 37–39 (DPO designation, position, tasks). The four-authority model gives the DPO an explicit, claim-level accountability locus rather than a document-level "policy owner" role.

**Worked example.** When a data subject exercises Article 16 (rectification) or Article 17 (erasure), the revision authority is the institutional locus that processes the request, propagates the disposition to derived claims, and produces the audit trail.

**Gap addressed.** Current personal-data governance has policy owners and stewards but rarely claim-level accountability for rectification and erasure propagation. The four-authority model makes this explicit.

### Principle 7: Acquisition has modes

**Personal-data application.** Four acquisition modes operate over personal data:

- **Harvest:** Direct collection from the data subject (forms, account creation). Lowest provenance ambiguity, clearest lawful basis.
- **Extract:** Tool-assisted extraction from system logs, third-party feeds, broker data. Lawful basis must be reconstructable per source; Article 14 information obligations apply when data is not obtained from the subject.
- **Capture:** Operational observations recorded by staff (e.g. complaint summaries, service notes). Requires explicit lawful basis and minimum-necessary scoping.
- **Emerge:** Model-derived inferences from existing claims. Marked as derived; subject to Article 22 constraints when the inference drives a solely automated decision.

**Regulatory connection.** GDPR Article 14 (information when data not obtained from the subject) requires the controller to inform the subject of source. Acquisition mode is a structural input to that obligation.

**Data Act overlay.** Under EU Data Act Articles 3–6, users of connected products have a right to access data generated by their use. Acquisition-mode metadata determines whether a given claim falls under Data Act access rights — a Harvest claim from the user's device falls in scope; a downstream Emerge claim derived from it has a different status. DRAFT — counsel review needed for the precise scope boundary.

### Principle 8: Expert knowledge is a point of view, not ground truth

**Personal-data application.** A senior agent or analyst may have operational knowledge about a specific subject or segment. That knowledge is governable but cannot reach Validated tier (let alone Foundational) without independent corroboration *and* a recorded validation event (Principle 13) — and cannot be used as a basis for an Article 22 decision on its own. The expert's view is a Capture-mode claim subject to the same epistemic tiering as any other source.

**Regulatory connection.** GDPR Article 5(1)(a) (fairness) and Article 22 protect against opaque, individually-asserted bases for automated decisions.

### Principle 9: The graph must support structured inquiry

**Personal-data application.** Structured inquiry over personal data means answering: "For subject S, what claims do we hold, with what lawful basis, sourced from where, with what retention, and which were used by which agent in which decision?" This is the substrate of an Article 15 (right of access) response, an Article 30 record, and an Article 35 DPIA. It is not a data export — it is a structured account of the institution's reasoning over the subject.

**Regulatory connection.** GDPR Articles 15 (right of access), 20 (data portability), 30 (ROPA), and EU Data Act portability obligations. Structured inquiry over a governed graph is the substrate that makes timely DSAR response and Data Act response feasible at scale.

### Principle 10: Every engagement feeds the graph

**Personal-data application.** Every DSAR, every rectification request, every erasure request, every consent withdrawal is a feedback event. These should not be processed as exceptions; they are observations about the substrate's correctness from the only source whose claims about a subject can reach Foundational tier — the subject. Three structured capture points: at request intake (what does the graph claim about this subject?), during fulfilment (what corrections / disposals were required?), at close-out (what claim-level lessons propagate to similar subjects?).

**Regulatory connection.** GDPR Articles 12(3)–(4) (timeliness and reasoned response), Article 16 (rectification), Article 17 (erasure). Intelligence governance treats DSAR responses as first-class feedback into the substrate, not as a parallel compliance workflow.

### Principle 11: Traceability is the response to acceleration

**Personal-data application.** When an agent acts on personal-data claims — to personalise, score, classify, recommend, or decide — the reasoning chain must be traceable from action through reasoning through claims through provenance (including lawful basis) to source. For Article 22-implicating decisions, the chain must include the safeguards applied: human-in-the-loop checkpoint, right-to-explanation evidence, contestability path.

**Regulatory connection.** GDPR Article 22(3) (right to obtain human intervention, express a point of view, contest the decision), Article 13(2)(f) and 14(2)(g) (meaningful information about the logic involved). Intelligence governance is designed to support the substrate-level traceability these rights imply.

**Worked example: Italy DPA OpenAI fine 2026.** DRAFT — public-record review needed. The Italian Garante's 2026 enforcement action against OpenAI cited gaps in lawful basis identification, transparency to data subjects, and substrate-level evidence of how training-data and runtime-input claims were handled. Whether or not the institution is a foundation-model operator, the structural lessons map to substrate governance: lawful basis must travel with the claim; the path from agent action to claim to source must be reconstructable; the rights pathway (Article 22, 15, 16, 17) must reach the substrate, not stop at a UI.

DRAFT — public-record review needed: The specific findings, fines, and remediation orders of the Italy DPA 2026 OpenAI decision should be cited from the Garante's published decision before this is used as a worked example.

### Principle 12: No unfunded mandates

**Personal-data application.** Intelligence governance for personal data requires DPO time, data-steward time, privacy-engineering capacity, and DSAR response capacity. Article 24 (responsibility of the controller) and Article 32 (security of processing) require "appropriate technical and organisational measures." Substrate governance is a candidate appropriate measure — but only if resourced.

**Regulatory connection.** GDPR Articles 24, 32, and 39 (DPO tasks) presuppose ongoing resourced operations. EU Data Act Articles 4–6 likewise presuppose that data-holder obligations are operationalised, not declared.

---

## Cross-references

- See [`governance/authority-accountability-matrix.md`](../governance/authority-accountability-matrix.md) for the named-role mapping of the four authorities plus the DPO and substrate-security owner. *(Planned by A11.)*
- See [`governance/foundation-model-third-party-register.md`](../governance/foundation-model-third-party-register.md) for the register of foundation models and third-party data sources whose claims enter the substrate, and the lawful basis under which each is processed. *(Planned by A11.)*

---

## Epistemic operational risk in personal-data systems

The manifesto introduces epistemic operational risk as the risk of institutional harm from acting on defective knowledge. In personal-data systems, this surfaces in specific ways:

**Lawful-basis drift.** A claim acquired under one lawful basis is reused for a purpose that requires a different basis. The claim is correct; its processing is not. An agent reasoning without lawful-basis-aware provenance produces decisions that are individually plausible and structurally non-compliant.

**Stale-consent risk.** A consent withdrawal at time T is not propagated to derived claims used by an agent at time T+ε. The agent's action looks like an Article 22 decision on consented data when in fact consent has been withdrawn.

**Rectification non-propagation.** An Article 16 rectification updates the source record but not the derived claims that downstream agents act on. The institution has acknowledged the correction in policy and ignored it in practice.

**Article 22 amplification.** An agent operating without epistemic-tier gating uses Provisional inferences to drive solely automated decisions producing legal or similarly significant effects — exactly the harm Article 22 is designed to prevent.

**Data Act mis-scoping.** The Data Act gives users access and sharing rights over data generated through their use of connected products. Without claim-level scoping that distinguishes user-generated data from controller-derived inferences, a controller either over-shares (releasing claims that are not in scope) or under-shares (failing to release claims that are).

---

*This is a domain mapping for the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*

*DRAFT status: items marked DRAFT in this document require domain expert review before operational use.*
