# Intelligence Governance in Healthcare

**Domain mapping for the Intelligence Governance Manifesto**

This document maps the manifesto's twelve principles and four integrity preconditions to the regulatory and operational context of healthcare AI under HIPAA and EU GDPR Article 9 (special-category personal data). It identifies where each principle connects to existing regulatory requirements and where it addresses gaps that current frameworks leave open.

Intelligence governance does not claim to satisfy these regulations. It provides an architectural framework designed to support the knowledge-substrate requirements that these regulations increasingly imply but do not specify how to implement. Compliance determinations require domain-specific clinical, legal, and regulatory analysis.

> **DRAFT — clinical / regulatory SME review needed.** This mapping was drafted from public regulatory text and enforcement summaries. Items marked DRAFT below should be reviewed by a qualified healthcare compliance officer, clinical informaticist, and privacy counsel before operational use.

---

## Regulatory context

Healthcare intelligence governance operates under overlapping regulatory obligations:

| Regulation | Scope | Intelligence governance relevance |
|---|---|---|
| **HIPAA Privacy Rule** (45 CFR 164.500–534) | Use and disclosure of Protected Health Information (PHI) in US covered entities and business associates | Minimum-necessary, accounting of disclosures, individual access. Intelligence governance is designed to support claim-level provenance and disposition for PHI-derived assertions. |
| **HIPAA Security Rule** (45 CFR 164.302–318) | Administrative, physical, technical safeguards for electronic PHI | Audit controls, integrity, transmission security. Intelligence governance extends integrity controls to the knowledge layer derived from PHI. |
| **GDPR Article 9** | Processing of special-category data including health data in the EU | Lawful basis, explicit consent, public-interest exceptions. Intelligence governance must record lawful basis as part of the provenance chain for every health-data-derived claim. |
| **FDA SaMD framework** (21 CFR Part 820 / IMDRF SaMD N12) | Software as a Medical Device, including AI/ML-based clinical decision support in the US | Predetermined Change Control Plans, clinical validation, post-market surveillance. Intelligence governance addresses the substrate that adaptive SaMD reasons over. |
| **EU MDR (2017/745) and IVDR (2017/746)** | Medical devices and in-vitro diagnostic devices in the EU, including embedded AI | Clinical evaluation, post-market clinical follow-up, performance monitoring. Intelligence governance extends post-market evidence requirements to the knowledge substrate. |
| **EU AI Act** (high-risk Annex III categories include some clinical AI) | AI systems classified high-risk | Risk management, technical documentation, human oversight, data governance. Intelligence governance is designed to support the substrate architecture these requirements imply. |
| **HHS OCR enforcement** (right of access, breach notification, minimum necessary) | HIPAA enforcement against covered entities and business associates | OCR settlements increasingly cite missing audit trails, weak access controls, and inability to reconstruct who accessed what PHI when. Intelligence governance supports claim-level reconstruction. |

DRAFT — domain expert review needed: Whether an institution-specific AI clinical decision support deployment falls under FDA SaMD enforcement, EU MDR, or both, depends on intended use, claims made, and jurisdiction. This mapping does not determine classification.

---

## Principle-by-principle mapping

### Principle 1: The claim is the unit

**Healthcare application.** Clinical guidelines, formulary rules, contraindications, and care-pathway steps are currently governed at the document level — the institution "has" the latest USPSTF recommendation documented in a guideline binder. Intelligence governance moves this to claim level: "USPSTF 2024 recommends biennial mammography screening for women aged 40-74 at average risk (Grade B)" is a governed claim with provenance, scope (US adults, average-risk population), temporal validity (since the 2024 update), and epistemic tier (Foundational — primary guideline source, structurally integrated).

**Regulatory connection.** HIPAA Security Rule 164.312(c)(1) requires integrity controls "to protect electronic protected health information from improper alteration or destruction." The claim model operationalizes this at the knowledge level — each PHI-derived claim carries the metadata needed to assess accuracy, completeness, and integrity over time.

**Worked example.** A clinical decision support agent recommending statin therapy must reason over the *specific* claim "ACC/AHA 2018 cholesterol guideline recommends moderate-intensity statin for primary prevention in adults 40-75 with LDL-C 70-189 mg/dL and 10-year ASCVD risk ≥7.5%" — not the parent document. Document-level governance cannot tell the agent that an updated 2025 guideline has superseded one specific recommendation while the rest of the document remains current.

**Gap addressed.** Current healthcare knowledge management tracks guideline documents and drug references. When an agent acts on a claim extracted from a guideline, there is no governance at the claim level — no way to know whether the specific recommendation is current, scoped to the right population, or contradicted by another professional society.

### Principle 2: Provenance is non-negotiable

**Healthcare application.** Every PHI-derived claim must trace to its source — the encounter, the order, the lab result, the imaging study — with the lawful basis or HIPAA permission that authorised its use. When an agent participates in clinical decision support, prior authorisation, coding, or quality-measure reporting, the provenance chain from action to claim to source must be reconstructable. Provenance must include source type, date, acquisition mode, and (for GDPR Article 9 contexts) the lawful basis under which the underlying data was processed.

**Regulatory connection.** HIPAA Privacy Rule 164.528 (accounting of disclosures), Security Rule 164.312(b) (audit controls), GDPR Articles 5(1)(a) and 30 (lawfulness, records of processing), EU AI Act Article 13 (transparency for high-risk systems). FDA SaMD post-market surveillance assumes reconstructable evidence trails for adverse events.

**Worked example.** An OCR resolution agreement requires a covered entity to demonstrate, for any PHI access, who accessed it, why, and under what authorisation. An AI agent that summarised a patient chart for a clinician must produce — on examination — the specific claims it consumed, their source documents, and the access authorisation chain.

**Gap addressed.** Current AI audit trails for clinical systems typically record model inputs and outputs. They do not record the provenance of the knowledge those inputs were drawn from. A claim with broken provenance cannot satisfy HIPAA accounting-of-disclosures requirements when PHI flowed through it.

### Principle 3: Epistemic tier is earned, not assigned

**Healthcare application.** A peer-reviewed Cochrane systematic review carries a different epistemic tier than a single observational study; an institutional clinical pathway carries a different tier than a single attending's stated practice. The four epistemic tiers (Provisional → Emerging → Validated → Foundational) map to clinical evidence hierarchies and to the four consequence classes (Low → Medium → High → Critical): a Provisional claim is usable for clinician-facing reference (Low consequence) but not for autonomous agent recommendation in a patient encounter (which requires Validated or Foundational depending on consequence class).

**Regulatory connection.** FDA's Good Machine Learning Practice principles (joint FDA/Health Canada/MHRA guidance) require that training data and clinical evidence be appropriate for the intended use. Intelligence governance operationalizes this through epistemic tiers that gate what actions may be taken on each claim.

**Worked example.** An agent considering a drug-drug interaction warning must distinguish between a Foundational-tier claim from FDA labelling, a Validated-tier claim from a major drug compendium, and an Emerging-tier claim extracted from a single recent case report. All three may surface the same interaction; only the first two should suppress an order without explicit clinician override.

**Gap addressed.** Current clinical knowledge bases treat all entries as roughly equivalent once curated. An AI-extracted claim from a case report and a direct FDA black-box warning carry similar weight in retrieval. Tiering prevents agents from acting on weakly supported clinical claims with the same authority as well-supported ones.

### Principle 4: Contradictions are information

**Healthcare application.** Healthcare is full of legitimate contradictions: USPSTF and a specialty society disagreeing on screening intervals, a patient's stated medication list contradicting the pharmacy fill record, a clinical guideline that conflicts with an institutional formulary policy, an evolving treatment protocol where last quarter's standard of care has been superseded. The contradictions are clinical signal, not data quality defects.

**Regulatory connection.** EU MDR post-market clinical follow-up requires identifying discrepancies between expected and observed performance. Untyped contradictions in the clinical knowledge substrate are a discrepancy category that current PMS frameworks do not name. FDA SaMD predetermined change control plans assume the institution can recognise when clinical evidence has shifted.

**Worked example.** USPSTF recommends initiating mammography screening at age 40 (2024 update). The American College of Physicians recommends discussion at 40 with routine screening from 50. This is a logical contradiction within US practice — both organisations are competent authorities and both claims reach the institution's clinicians. A system that silently picks one destroys the information that shared decision-making is the appropriate response.

DRAFT — clinical SME review needed: The specific guideline divergence above should be confirmed by a clinical informaticist before being used as a published example.

**Gap addressed.** Current clinical decision support forces resolution — one answer per question. Intelligence governance types contradictions (jurisdictional, professional-society divergence, temporal supersession, scope, extraction) and preserves them. An agent reasoning over typed contradictions can present both views to a clinician for shared decision-making rather than imposing a silent arbitration.

### Principle 5: Intelligence decays. Govern the decay.

**Healthcare application.** Decay rates in healthcare vary by claim type:

| Claim type | Decay rate | Trigger |
|---|---|---|
| Anatomy and basic physiology | Years to decades | Rare reclassification |
| Treatment guidelines / evidence-based pathways | Months to years | Society guideline update, major trial publication, regulatory action |
| Drug labelling and contraindications | Weeks to months | FDA label update, post-market safety signal |
| Local formulary, antibiogram, institutional protocol | Weeks to months | Resistance pattern shift, supply change, P&T committee decision |
| Patient-specific operational claims (current medications, allergies, code status) | Hours to days | New encounter, new order, patient statement |
| Coding and reimbursement rules | Quarterly | Payer policy update, ICD/CPT cycle |

**Regulatory connection.** FDA SaMD post-market surveillance, EU MDR Article 83 (PMS) and Article 86 (periodic safety update reports). DRAFT — regulatory expert review: PMS for SaMD increasingly assumes continuous evidence monitoring; intelligence governance extends this from device performance to the knowledge substrate.

**Worked example.** A drug-interaction claim from 2022 about a specific combination is overridden by a 2025 FDA Drug Safety Communication. A decision-support agent reasoning over the stale claim recommends a combination that is now black-boxed. Decay monitoring with linkage to FDA communications would alert review.

**Gap addressed.** Current clinical knowledge bases have manual update cycles. In an agentic environment, stale claims are not just inefficient — they produce automated recommendations on expired knowledge in patient-facing workflows.

### Principle 6: Four authorities govern the graph

**Healthcare application.** In healthcare, the four governance authorities map to existing institutional roles:

| Authority | Healthcare mapping | Responsibility |
|---|---|---|
| **Semantic authority** | Medical informaticist / terminology services / chief health information officer | Vocabulary and ontology — SNOMED CT, LOINC, ICD, RxNorm bindings; concept relationships; when to decompose hub concepts |
| **Assertion authority** | Treating clinician (for patient-specific claims); medical director / clinical specialty leadership (for institutional protocol claims); pharmacy and therapeutics committee (for formulary and drug claims) | Whether specific claims are accurate within their declared scope |
| **Inference authority** | Clinical informatics / clinical decision support governance / model-risk-equivalent function | Whether reasoning chains across claims are valid (e.g. risk-score composition, alert logic) |
| **Revision authority** | Health information governance committee / privacy officer (for PHI-derived claims) / chief medical officer | When claims should be superseded, demoted, sealed, or disposed; PHI minimum-necessary disposition |

**Regulatory connection.** HIPAA workforce-clearance and minimum-necessary obligations require defined accountability for who may create, access, and modify PHI-derived information. The four-authority model makes this explicit at the knowledge layer.

**Worked example.** When a patient requests amendment of PHI under HIPAA 164.526, the institution must identify who has authority to amend the record and propagate the amendment. The revision authority for PHI-derived claims is the institutional locus that operationalises this propagation — including downstream claims that derived from the amended record.

**Gap addressed.** Current clinical knowledge management has document owners but rarely claim-level accountability. The four-authority model makes governance accountability explicit at the claim level — particularly important when PHI flows through derived claims.

### Principle 7: Acquisition has modes

**Healthcare application.** Four acquisition modes operate in healthcare:

- **Harvest:** Structured extraction from published guidelines, FDA labels, regulatory texts, society recommendations. High-volume, automatable, requires synthetic-origin labelling when AI performs extraction.
- **Extract:** Semi-structured capture from research literature, registry data, clinical trial reports, post-market surveillance feeds. Requires expert review of extraction quality.
- **Capture:** Expert knowledge sessions with clinicians, pharmacists, and operational staff — institutional protocol nuance, workaround knowledge, transition-of-care patterns. Voluntary, disclosed, structured as claims rather than transcripts.
- **Emerge:** New claims generated through graph operation — cross-domain links discovered, gaps surfaced, hypotheses raised. Marked as system-generated; requires validation before operational use.

**Regulatory connection.** GDPR Article 9 explicit-consent and HIPAA authorisation requirements apply when Capture mode involves PHI or identifiable practitioner-patient context. Intelligence governance must support governed disposition for claims that intersect special-category personal data obligations.

**Worked example.** A claim captured from a senior pharmacist about a workaround for a specific drug shortage must enter at Provisional or Emerging tier, not Foundational. The pharmacist's expertise is real; the claim's evidentiary standing is what governs its agentic use.

### Principle 8: Expert knowledge is a point of view, not ground truth

**Healthcare application.** A senior attending knows things no guideline captures. A nurse manager knows operational reality the policy document does not describe. That knowledge is valuable and governable — but a single expert's clinical or operational claim cannot reach Validated tier (let alone Foundational) without independent corroboration *and* a recorded validation event (Principle 13). The expert may be right. The system governs the *epistemic tier with which it acts on that claim* based on evidentiary standing, not personal authority.

**Regulatory connection.** FDA Good Machine Learning Practice guidance warns against over-reliance on individual expert opinion in training and validation. Intelligence governance extends this principle to the knowledge substrate.

### Principle 9: The graph must support structured inquiry

**Healthcare application.** Structured inquiry in healthcare means answering questions that span domains: "What is our current standard of care for hospital-acquired bloodstream infection in immunocompromised patients, given current local antibiogram, formulary, and the latest IDSA guidance — and where do these contradict?" This requires cross-domain linking (infection management → antibiogram → formulary → guidelines), gap analysis (which pathogen profiles lack institutional guidance?), and conflict surfacing (does the institutional protocol diverge from the IDSA recommendation?).

**Regulatory connection.** EU MDR Article 32 (Summary of Safety and Clinical Performance) and FDA SaMD performance monitoring assume the institution can answer cross-domain queries about clinical performance. Structured inquiry over a governed graph supports this.

### Principle 10: Every engagement feeds the graph

**Healthcare application.** Every clinical encounter, every order, every quality-improvement cycle generates observations that should feed the graph. Three structured capture points: at encounter start (what does the graph get wrong about this patient or population?), during the episode (what has the team learned?), at close-out (what would the next clinician need to know?). Without these feedback loops, the clinical knowledge graph fossilizes.

**Regulatory connection.** EU MDR post-market clinical follow-up and FDA SaMD post-market surveillance both assume continuous learning loops. Intelligence governance extends this from device performance to the substrate the device or agent reasons over.

**Worked example.** A clinical decision support agent recommends a dose adjustment based on renal function. The clinician overrides because of a specific drug-drug interaction the agent did not account for. The override and its rationale should feed back as a candidate gap — not a logged event in a model-monitoring system, but a claim-level observation that the substrate did not represent the relevant interaction.

### Principle 11: Traceability is the response to acceleration

**Healthcare application.** When an agent contributes to a clinical recommendation, prior authorisation determination, coding decision, or quality measure report, the reasoning chain must be traceable from action through reasoning through claims through provenance to source. Traceability must satisfy HIPAA accounting-of-disclosures, FDA SaMD post-market evidence, and EU MDR PMS expectations — not just internal logging but reconstructable audit trails with epistemic tiers, scope qualifications, and contradiction flags at every step.

**Regulatory connection.** EU AI Act Article 14 (human oversight for high-risk systems), HIPAA 164.312(b) (audit controls), FDA SaMD post-market surveillance, EU MDR Article 83.

**Governance relocation in clinical contexts.** In low-substrate clinical AI deployments, governance is external: every agent recommendation gates on synchronous clinician approval. As the substrate deepens — validated guideline claims, scoped protocol claims, current formulary, current patient-specific PHI — the consequence structure that governance was encoding becomes structurally represented in the graph. Explicit pre-action checks shift from universal requirement to risk-based monitoring per action class. *This relocation is bounded:* high-acuity, irreversible, or novel-class clinical decisions remain synchronously human-gated regardless of substrate maturity. DRAFT — clinical SME review needed for the specific action classes that remain mandatory-gated.

### Principle 12: No unfunded mandates

**Healthcare application.** Intelligence governance in healthcare requires dedicated budget, staffing, and institutional commitment — clinical informaticists, ontology stewards, P&T committee curation time, privacy office curation time. In healthcare, where the cost of a knowledge failure can be patient harm and where OCR civil monetary penalties for HIPAA violations are substantial, the cost of intelligence governance is measured against the cost of epistemic operational risk.

**Regulatory connection.** HIPAA Security Rule 164.308(a)(1)(ii)(B) requires risk management measures to be "reasonable and appropriate." Intelligence governance is part of the reasonable-and-appropriate envelope once agents operate on PHI-derived claims in clinical workflows. EU AI Act Article 9 (risk management for high-risk systems) requires resourced ongoing risk management.

---

## Cross-references

- See [`governance/authority-accountability-matrix.md`](../governance/authority-accountability-matrix.md) for the named-role mapping of the four authorities plus the substrate-security owner across an institutional org chart. *(Planned by A11.)*
- See [`governance/foundation-model-third-party-register.md`](../governance/foundation-model-third-party-register.md) for the register of foundation models and third-party intelligence sources whose claims enter the substrate. *(Planned by A11.)*

---

## Epistemic operational risk in healthcare

The manifesto introduces epistemic operational risk as the risk of institutional harm from acting on defective knowledge. In healthcare, this surfaces in specific ways:

**Clinical decision risk.** An agent recommending therapy based on a stale guideline or a superseded drug label produces recommendations that were correct last year and wrong today.

**Coverage and authorisation risk.** An agent processing prior authorisations against a payer policy that has been updated produces denials or approvals that misrepresent current policy.

**Coding and billing risk.** An agent assigning ICD/CPT codes against a fiscal-year coding rule that has cycled produces miscoded claims with downstream payment integrity and False Claims Act exposure.

**Privacy and disclosure risk.** A claim that derives from PHI without recorded lawful basis or HIPAA permission cannot be defended in an OCR investigation. The agent that consumed it may have acted in good faith on a substrate that was not governed for disclosure accounting.

**Device performance extension.** FDA SaMD and EU MDR govern device performance. Epistemic operational risk extends the same logic to the knowledge substrate: even a well-validated SaMD produces bad outputs when operating on stale, polluted, or mis-scoped clinical knowledge.

---

*This is a domain mapping for the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*

*DRAFT status: items marked DRAFT in this document require domain expert review before operational use.*
