# Intelligence Governance in the Public Sector

**Domain mapping for the Intelligence Governance Manifesto**

This document maps the manifesto's twelve principles and four integrity preconditions to the regulatory and operational context of public-sector and government use of AI. It identifies where each principle connects to existing regulatory requirements and where it addresses gaps that current frameworks leave open.

Intelligence governance does not claim to satisfy these regulations. It provides an architectural framework designed to support the knowledge-substrate requirements that these regulations increasingly imply but do not specify how to implement. Compliance determinations require domain-specific legal, constitutional, and regulatory analysis.

> **DRAFT — public-law / administrative-law SME review needed.** This mapping was drafted from public regulatory text and inter-governmental guidance. Items marked DRAFT below should be reviewed by qualified public-law counsel and a public-sector AI governance officer before operational use.

---

## Regulatory context

Public-sector intelligence governance operates under overlapping legal and inter-governmental obligations:

| Regulation | Scope | Intelligence governance relevance |
|---|---|---|
| **EU AI Act** — high-risk Annex III categories (public services) | AI used for access to essential public services and benefits, law enforcement, migration / asylum / border control, administration of justice and democratic processes | Risk management, technical documentation, human oversight, data governance, transparency, post-market monitoring. Intelligence governance is designed to support the substrate architecture these requirements imply. |
| **EU AI Act — Fundamental Rights Impact Assessment (FRIA)** (Article 27 for deployers including public bodies) | Public bodies and certain operators of high-risk systems must perform an FRIA before deployment | FRIA requires structural evidence about the system's foreseeable impact on fundamental rights. Intelligence governance produces the substrate-level evidence the FRIA requires. |
| **Council of Europe Framework Convention on AI and Human Rights, Democracy and the Rule of Law (2024)** | First binding international AI treaty; obligations on public authorities and (with declarations) private actors | Article 11 (effective remedies) requires accessible and effective remedies for adverse impacts on rights — the substrate must support remedy paths, not block them. |
| **OECD AI Principles** | Inter-governmental principles for trustworthy AI | Inclusive growth, human-centred values, transparency, robustness, accountability. Intelligence governance is one operationalisation route. |
| **National administrative-law obligations** | Reasoned decisions, right to be heard, access to file, judicial review | Public-sector decisions touching individuals must be reasoned and reviewable. Intelligence governance supports claim-level reasoning reconstruction. |
| **Supreme audit institution mandates** | National audit offices, Court of Auditors equivalents | Audit obligations to demonstrate lawful, regular, and effective use of public funds and public power. Intelligence governance produces the substrate-level evidence such audits require. |
| **GDPR / national equivalents** | Personal data processing by public authorities | Specific public-sector lawful bases, Article 6(1)(c) and (e); strict purpose limitation. See `personal-data-and-data-act.md` domain mapping. |
| **DORA / NIS2 (EU)** | Operational and cyber resilience for entities including parts of the public sector | Operational resilience obligations attach to substrate as infrastructure, not just ICT systems. |

DRAFT — public-law SME review needed: National-level constitutional and administrative law obligations (e.g. duty to give reasons, equal-treatment doctrine, proportionality, legitimate expectations) materially differ across member states; this mapping is at the European-level baseline.

---

## Principle-by-principle mapping

### Principle 1: The claim is the unit

**Public-sector application.** Statutes, regulations, ministerial guidance, and administrative-court precedents are currently governed at the document level — the agency "has" the latest text of the statute on a shared drive. Intelligence governance moves this to claim level: "Article X of Statute Y, as amended by Decree Z (date D), requires that benefit applicants demonstrate residence for at least 12 months" is a governed claim with provenance, scope (which subset of applicants), temporal validity (since amendment D), and epistemic tier (Foundational — primary statutory text in current consolidated form, structurally integrated).

**Regulatory connection.** Administrative-law duty to give reasons requires that decisions reference specific provisions, not entire statutes. The claim model operationalises this at the knowledge level: each cited rule is a governed claim with metadata sufficient to reconstruct why it applied to this case at this time.

**Worked example.** A benefits-eligibility agent applying a residency threshold must reason over the specific claim about the threshold, with its temporal validity. Document-level governance cannot tell the agent that an amendment last month changed the threshold for one applicant cohort while leaving another unchanged.

**Gap addressed.** Current public-sector knowledge management tracks legal documents and ministerial circulars. When an agent acts on a claim extracted from such a document, there is no governance at the claim level — no way to know whether the specific provision is current, scoped to the applicant's cohort, or contradicted by a recent court decision.

### Principle 2: Provenance is non-negotiable

**Public-sector application.** Every claim used in a public-sector decision must trace to its source — the statute, the regulation, the policy guidance, the case file, the inter-agency data sharing agreement — with the legal basis that authorised its use. When agents participate in benefit determinations, regulatory enforcement, or service triage, the provenance chain from action to claim to source must be reconstructable to the standard of judicial review and supreme audit examination.

**Regulatory connection.** EU AI Act Article 13 (transparency) and Article 12 (record-keeping) for high-risk systems; Council of Europe Framework Convention obligations on documentation; national administrative-law duty to give reasons; supreme audit institution mandates. Article 11 of the CoE Convention (effective remedies) presupposes reconstructable reasoning.

**Worked example.** An applicant seeking judicial review of a benefit denial is entitled (under most administrative-law systems and Article 11 of the CoE Convention) to know the basis of the decision. An AI agent that contributed to the determination must produce, on review, the specific claims it consumed, their statutory or policy provenance, and the temporal validity of each at the moment of the decision.

**Gap addressed.** Current AI audit trails for public-sector systems typically record model inputs and outputs. They do not record the legal provenance of the knowledge those inputs were drawn from. A claim with broken provenance cannot satisfy duty-to-give-reasons standards or remedy-pathway requirements.

### Principle 3: Epistemic tier is earned, not assigned

**Public-sector application.** A consolidated statutory text from the official gazette carries a different epistemic tier than a ministerial FAQ; a binding judicial precedent carries a different tier than a single first-instance decision. The four tiers (Provisional → Emerging → Validated → Foundational) gate what actions agents may take. Provisional- or Emerging-tier claims (e.g. extracted from an unannotated draft circular) cannot drive an enforceable benefit determination.

**Regulatory connection.** EU AI Act Article 10 (data governance for high-risk systems) and Article 9 (risk management) presuppose that the system can distinguish primary-source legal authority from less-supported inputs. Intelligence governance operationalises this through tiers (and, in colloquial / decision-time framing, through the corresponding *epistemic quality* summary surfaced to the human reviewer).

**Worked example.** An agent considering whether a particular activity is regulated must distinguish a Foundational-tier claim from a current statute, a Validated-tier claim from a published implementing regulation, and an Emerging-tier claim from a leaked draft circular. The first two may inform an enforceable position; the third cannot.

**Gap addressed.** Current public-sector knowledge bases treat all entries as roughly equivalent once curated. AI extraction from policy guidance and direct statutory citation carry similar weight in retrieval. Tiering prevents agents from acting on weakly supported public-law claims with the authority of statutory text.

### Principle 4: Contradictions are information

**Public-sector application.** Public law is full of legitimate contradictions: regulatory ambiguity where two provisions plausibly apply, judicial divergence between first-instance courts, divergent ministerial guidance from successive governments, federal/state or supranational/national tensions. Auto-resolution destroys signal that is constitutionally important — including the very ambiguity that triggers proportionality analysis or remedy pathways.

**Regulatory connection.** Council of Europe Convention Article 11 (effective remedies) and proportionality doctrine in EU and national administrative law assume the institution can identify and present competing legitimate interpretations. Untyped contradictions in the substrate destroy the basis for proportionality reasoning.

**Worked example.** A claim from national statute and a claim from a directly effective EU regulation may diverge on a procedural requirement. This is a jurisdictional / hierarchical contradiction, not a data quality defect. A system that silently picks one applies the wrong rule for some applicants and exposes the agency to judicial review.

DRAFT — public-law SME review needed: The specific hierarchy and direct-effect rules vary by member state and subject matter; this is illustrative, not authoritative.

**Gap addressed.** Current public-sector decision-support forces resolution. Intelligence governance types contradictions (jurisdictional, judicial divergence, temporal supersession, regulatory ambiguity, scope, extraction) and preserves them. An agent reasoning over typed contradictions can present the proportionality space rather than imposing a silent arbitration.

### Principle 5: Intelligence decays. Govern the decay.

**Public-sector application.** Decay rates in the public sector vary by claim type:

| Claim type | Decay rate | Trigger |
|---|---|---|
| Constitutional principles | Decades | Constitutional reform |
| Primary statutes | Years | Legislative amendment |
| Secondary regulations / decrees | Months to years | Ministerial action, regulatory cycle |
| Policy guidance and circulars | Months | Ministerial change, evolving practice |
| Judicial precedent (top-court binding) | Months to years | New top-court decision |
| Lower-court decisions | Weeks to months | Appellate decision |
| Operational case-handling guidance | Weeks | Internal directive, supervisor decision |

**Regulatory connection.** EU AI Act Article 17 (quality management for high-risk providers) and Article 72 (post-market monitoring for deployers) presuppose continuous evidence about evolving regulatory environment. Supreme audit institutions look for evidence that public bodies have systematic processes for currency of legal knowledge.

**Worked example.** A claim about the threshold for an environmental-permit category is overridden by a new EU regulation effective on a specific date. An agent processing applications must not surface the prior threshold after the effective date. Decay monitoring with linkage to the official gazette feed makes this enforceable rather than dependent on a quarterly legal update memo.

**Gap addressed.** Current public-sector knowledge management has manual update cycles tied to legal-affairs review meetings. In an agentic environment, stale claims produce automated determinations on expired law — exactly the failure mode that drives judicial review and audit findings.

### Principle 6: Four authorities govern the graph

**Public-sector application.** The four governance authorities map to existing public-sector roles:

| Authority | Public-sector mapping | Responsibility |
|---|---|---|
| **Semantic authority** | IT governance / data architecture in conjunction with legal-affairs taxonomy | Vocabulary and ontology — what legal categories exist, how policy concepts relate, when to decompose hub concepts (e.g. "applicant") |
| **Assertion authority** | Legal counsel / legal-affairs office (for legal-rule claims); policy office / programme owner (for policy-intent and operational guidance claims); programme staff (for operational practice claims) | Whether specific claims are accurate within their declared scope |
| **Inference authority** | Algorithm-governance / AI-governance committee / responsible-AI office | Whether reasoning chains across claims are valid (e.g. eligibility composition, risk-tier composition); whether tier propagation is correct |
| **Revision authority** | Information-governance committee, including legal counsel and DPO; with escalation to the responsible minister or accountable officer for politically consequential changes | When claims should be superseded, demoted, sealed, or disposed; freedom-of-information disposition; rights-pathway propagation |

**Regulatory connection.** EU AI Act Article 26 (deployer obligations for high-risk systems) requires governance arrangements with named accountable persons. The four-authority model gives this an explicit, claim-level locus. CoE Framework Convention obligations on accountability presuppose identifiable accountability lines.

**Worked example.** When a court ruling supersedes a prior administrative interpretation, the revision authority is the institutional locus that processes the supersession, propagates it to derived claims, and produces the audit trail for supreme-audit-institution review.

**Gap addressed.** Current public-sector knowledge management has policy owners and legal-affairs heads but rarely claim-level accountability. The four-authority model makes governance accountability explicit at the claim level — particularly important when decisions can be challenged by judicial review.

### Principle 7: Acquisition has modes

**Public-sector application.** Four acquisition modes operate in the public sector:

- **Harvest:** Structured extraction from official gazettes, regulatory portals, judicial publication channels, inter-governmental sources. High-volume, automatable, requires synthetic-origin labelling when AI performs extraction.
- **Extract:** Semi-structured capture from policy memoranda, inspector reports, audit findings, parliamentary committee outputs. Requires expert review of extraction quality.
- **Capture:** Expert sessions with policy officers, programme staff, legal counsel — institutional interpretation, operational workaround knowledge, casework patterns. Voluntary, disclosed, structured as claims.
- **Emerge:** New claims generated through graph operation — gaps surfaced, cross-domain links discovered, hypotheses raised. Marked as system-generated; never enters operational use without validation.

**Regulatory connection.** EU AI Act Article 10 (data governance) and Article 13 (transparency) require that the provenance and intended use of training and operational data be documented. Acquisition mode is a structural input.

### Principle 8: Expert knowledge is a point of view, not ground truth

**Public-sector application.** A senior caseworker knows things no manual captures. A policy officer knows the negotiating history that shaped a regulation. That knowledge is governable — but a single expert's claim about legal interpretation cannot reach Validated tier (let alone Foundational) without independent corroboration *and* a recorded validation event (Principle 13). The system governs the *epistemic tier with which it acts on that claim* based on evidentiary standing, not seniority.

**Regulatory connection.** Equal-treatment and reasoned-decision doctrine resist opaque expert-driven decisions. Intelligence governance requires that any expert claim used to inform an agent action be exposed and tier-bound.

### Principle 9: The graph must support structured inquiry

**Public-sector application.** Structured inquiry in the public sector means answering questions that span domains: "For applicant cohort C under programme P, which rules currently apply, what are their interactions with cohort-C-specific exemptions, where do recent court rulings or ministerial circulars create ambiguity, and what equality-of-treatment concerns arise across this cohort and adjacent cohorts?" This requires cross-domain linking, gap analysis, and conflict surfacing.

**Regulatory connection.** EU AI Act Article 27 (FRIA) requires structural analysis of foreseeable impacts on fundamental rights. Structured inquiry over a governed graph supports FRIA preparation and update. Supreme-audit-institution mandates assume the public body can answer cross-domain queries.

### Principle 10: Every engagement feeds the graph

**Public-sector application.** Every casework decision, every appeal, every parliamentary question response, every supreme-audit-institution observation generates feedback that should feed the substrate. Three structured capture points: at intake (what does the graph get wrong about this cohort, this case type, this regulatory boundary?), during processing (what has the team learned?), at close-out (what would the next caseworker need to know?). Without these loops, the substrate fossilises around the day it was built.

**Regulatory connection.** EU AI Act Article 72 (deployer post-market monitoring) and CoE Framework Convention obligations on iterative improvement assume substrate-level feedback, not just performance-metric feedback.

### Principle 11: Traceability is the response to acceleration

**Public-sector application.** When an agent contributes to a citizen-facing determination — benefit eligibility, regulatory enforcement, service allocation, risk classification — the reasoning chain must be traceable from action through reasoning through claims through provenance to source, including statutory and policy provenance. The traceability must support the **remedy paths** under CoE Convention Article 11: a citizen who challenges a decision must be able to obtain (through the institution or a court) a structured account of the basis for the decision.

**Regulatory connection.** EU AI Act Article 14 (human oversight for high-risk systems) and Article 27 (FRIA) presuppose traceability. CoE Framework Convention Article 11 (effective remedies) requires that remedy mechanisms be **accessible and effective**, which in turn requires reconstructable reasoning. National duty-to-give-reasons doctrine is the long-standing form of the same requirement.

**Governance relocation in public-sector contexts.** In low-substrate deployments, governance is external: every agent recommendation in a citizen-facing path gates on synchronous human approval. As the substrate deepens — validated statutory claims, scoped policy claims, current judicial precedent, jurisdiction-aware contradiction map — the consequence structure that governance was encoding becomes structurally represented in the graph. *This relocation is bounded:* decisions producing legal or similarly significant effects on individuals, decisions in fundamental-rights-sensitive domains (asylum, criminal justice, child protection), and any decisions where Article 22 GDPR or equivalent applies remain synchronously human-gated regardless of substrate maturity. DRAFT — public-law SME review needed for the specific decision classes that remain mandatory-gated.

### Principle 12: No unfunded mandates

**Public-sector application.** Intelligence governance in the public sector requires legal-affairs curation time, policy-office curation time, IT-governance capacity, and dedicated FRIA / post-market monitoring capacity. Public-sector budget cycles are particularly vulnerable to "unfunded mandates" — obligations imposed without resources. EU AI Act Article 26 (deployer obligations) and Article 27 (FRIA) presuppose resourced operations, not policy declarations.

**Regulatory connection.** EU AI Act Article 17 (quality management) and Article 72 (post-market monitoring) require resourced ongoing operations. CoE Framework Convention Article 4 (general obligations) requires that signatory parties take measures including organisational measures — i.e. resourced capacity, not statements.

---

## Cross-references

- See [`governance/authority-accountability-matrix.md`](../governance/authority-accountability-matrix.md) for the named-role mapping of the four authorities plus the substrate-security owner across a public-sector org chart, with escalation paths to the responsible minister or accountable officer. *(Planned by A11.)*
- See [`governance/foundation-model-third-party-register.md`](../governance/foundation-model-third-party-register.md) for the register of foundation models and third-party intelligence sources whose claims enter a public-sector substrate, including the procurement and lawful-basis posture for each. *(Planned by A11.)*

---

## Epistemic operational risk in the public sector

The manifesto introduces epistemic operational risk as the risk of institutional harm from acting on defective knowledge. In the public sector, this surfaces in specific ways:

**Adverse-decision risk.** An agent contributing to a benefit denial, regulatory enforcement, or service refusal based on a stale or mis-scoped legal claim produces decisions that are individually plausible and structurally ultra vires. The harm to the citizen is often irreversible by the time review catches it.

**Equal-treatment risk.** An agent that applies different versions of the substrate to functionally equivalent cohorts (because decay was uneven) produces unequal treatment that violates equal-treatment doctrine.

**Remedy-pathway failure.** A claim that cannot be traced from the agent's action back to a verifiable source breaks the remedy pathway under CoE Convention Article 11. The citizen has a right of effective remedy, and the institution cannot satisfy it without substrate-level traceability.

**Audit and accountability failure.** Supreme audit institutions and parliamentary oversight bodies look for evidence that public bodies systematically govern the knowledge their automated systems act on. Absence of substrate-level evidence is itself an audit finding under modern AI-audit methodologies.

**Fundamental-rights amplification.** A FRIA produced before deployment is a snapshot. Without substrate-level feedback that updates the fundamental-rights view as use evolves, the FRIA becomes a one-time compliance artefact rather than a living risk control.

---

*This is a domain mapping for the Intelligence Governance Manifesto (Reichhart and Gelas, 2026). Licensed under CC BY-SA 4.0.*

*DRAFT status: items marked DRAFT in this document require domain expert review before operational use.*
