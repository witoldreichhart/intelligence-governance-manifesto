# Twelve Principles of Intelligence Governance

*Each principle includes a minimum bar — the absolute floor of implementation. Principles without minimum bars are aspirations, not governance.*

*Governance intensity should be proportionate to risk. Claims that gate agent action in regulated workflows require full governance. Claims used for informational support may warrant lighter treatment. The principles below define the ceiling, not a uniform floor.*

---

## Part I — Principles of the Intelligence Architecture

*What the system must look like.*

### Principle 1: The claim is the unit.

Every piece of intelligence is decomposed to claim level — a single, testable, governable assertion. Claims have types (regulatory rule, operational workaround, cross-domain dependency, vendor configuration), provenance, confidence, and lifecycle state.

A claim is a governed assertion scoped to a defined context — not a free-floating fact. It carries its boundaries: jurisdiction, business unit, operational state, temporal validity. Claims inherit a lineage from structured content engineering, semantic assertions, and knowledge management primitives. The difference is operational: these claims are governed for machine consumption under regulatory constraint, with confidence tiers that gate what agents may do with them.

Not all institutional knowledge can be expressed as claims. Tacit judgment, situated expertise, and embodied know-how resist clean decomposition. The claim layer governs what can be made explicit. Where decomposition would destroy operational meaning, the system must preserve larger structured objects — cases, scenarios, decision records — or route to human judgment.

**Minimum bar:** No intelligence enters the graph as an unstructured document. Every claim has a type, at least one source attribution, and a defined scope before it is stored.

---

### Principle 2: Provenance is non-negotiable.

Every claim traces to its source — document, expert interview, operational observation, or graph inference. Provenance is not metadata. It is the basis for trust. When an auditor asks "why did the agent make this recommendation?", the chain from action to claim to source must be traversable in seconds.

Provenance includes source type, date of acquisition, acquisition mode, and — where material — the social process of challenge and acceptance that turned an assertion into something the organisation treats as reliable. Provenance chains must be verifiable for integrity, not just recorded.

**Minimum bar:** No claim exists without source attribution. Provenance includes source type, date of acquisition, and acquisition mode. Provenance integrity is verifiable.

---

### Principle 3: Confidence is earned, not assigned.

Confidence reflects provenance strength, corroboration depth, time since last challenge, and source class. A single-source expert claim starts at "Supported," not "Validated." Promotion requires corroboration — from independent sources, documentary evidence, or operational verification.

Confidence marks the level of institutional support for a claim under defined conditions. It does not certify truth. It does not remove the need for scope judgment. It does not authorise action by itself. In specialist domains where independent verification is impractical — where the institution depends on expert testimony because no alternative evidence exists — the system must accept structured epistemic dependence as a valid state, not demand infinite corroboration. Claims resting on expert testimony carry explicit "expert-dependent" status and defined usage constraints.

**Minimum bar:** Every claim carries a visible confidence tier. Promotion from one tier to the next requires documented evidence of corroboration. Claims resting on uncorroborated expert testimony are explicitly marked and carry defined usage constraints.

---

### Principle 4: Contradictions are information.

When two claims conflict, both are preserved. The contradiction itself is a first-class object — with its own provenance, scope, and resolution status. Auto-resolution destroys the most important signal in the system.

Conflicts must be typed: logical contradiction, jurisdictional divergence, temporal supersession, scope variation, or extraction error. Each type carries different operational implications. A jurisdictional divergence (UK CREST vs EU CSDR penalty calculations) means both positions are valid within their scope. A logical contradiction within a single jurisdiction means at least one claim is wrong. A temporal supersession means one claim has replaced another. The system must distinguish these — untyped conflict is noise, not signal.

*Example: ESMA's CSDR specifies T+2 settlement with a penalty calculation methodology. UK CREST, post-Brexit, implements a divergent penalty regime. This is a jurisdictional divergence. Both claims are valid within their jurisdiction. A system that "resolves" this by choosing one has destroyed the information that a cross-border settlement programme must handle both regimes simultaneously.*

**Minimum bar:** Contradiction detection is automated. Contradiction resolution is human-gated. Every material conflict is typed. No contradiction is silently overwritten.

---

### Principle 5: Intelligence decays. Govern the decay.

Every claim has a temporal dimension. Regulatory claims decay on amendment cycles. Operational claims decay faster — a workaround valid last quarter may not survive a system upgrade. A claim about a vendor's configuration decays with every product release. Decay monitoring is the difference between an intelligence system and a legacy document store.

**Minimum bar:** Every claim has an expected validity window. Claims past their window trigger review alerts. Staleness metrics are tracked per domain.

---

## Part II — Principles of Intelligence Operations

*How the organisation must run it.*

### Principle 6: Four authorities govern the graph.

**Semantic authority** — who defines the vocabulary, ontology, and allowed relation types. Semantic authority includes ontology evolution — adding, refining, or restructuring the vocabulary as domains change and new concepts emerge. **Assertion authority** — who creates, validates, promotes, supersedes, or retires claims. **Inference authority** — who defines the rules by which claims support, contradict, or entail each other. **Revision authority** — who handles challenge, contradiction, confidence downgrade, and decay.

Every claim-affecting action maps to exactly one authority. Ungoverned authorities produce ungoverned graphs.

These are functional authorities, not job titles. In practice, one role may exercise multiple authorities. In a small implementation, a single domain lead may hold assertion and revision authority. What matters is that every governance action is traceable to the authority that sanctioned it.

**Minimum bar:** All four authorities are explicitly assigned to named roles or functions. Authority boundaries are documented. No claim is created, promoted, or retired without the responsible authority's involvement.

---

### Principle 7: Acquisition has modes. Match the mode to the source.

**Harvest** — automated, public sources, lowest cost, highest volume. **Extract** — tool-assisted, credentialed access to project archives, vendor portals, defect logs. **Capture** — human-led structured interviews, most expensive, captures operational knowledge from people's heads. **Emerge** — graph self-extension, connections and gaps the system surfaces without human prompting.

Each mode has different cost, reliability, and governance requirements.

Emerge produces acquisition hypotheses and gap candidates — never operational claims. Every emerged suggestion enters the standard validation pipeline and becomes a claim only after human validation and promotion through the standard gate. Uncontrolled Emerge — where machine-generated suggestions bypass validation — is a failure mode, not a feature.

**Minimum bar:** Acquisition mode is recorded for every claim. Confidence tier at intake is calibrated to source mode — Harvest claims do not enter at the same confidence as Capture claims. Emerge outputs are clearly labelled as hypotheses requiring validation.

---

### Principle 8: Expert knowledge is a point of view, not ground truth.

An expert interview produces claims at a specific confidence tier. Experts are subjective, role-dependent, and reconstructive. We are collecting points of view. Out of this noise, you extract signal. The curation process — corroboration across sources, documentary evidence, operational verification — is the signal extraction mechanism.

**Minimum bar:** Single-source expert claims cannot reach "Validated" status without independent corroboration. Source class (document, single SME, multiple SMEs, operational verification) is a first-order input to confidence scoring.

---

### Principle 9: The graph must support structured inquiry, not just retrieval.

Retrieval returns documents. Intelligence supports structured inquiry — connecting claims across domains, surfacing conflicts, detecting gaps, flagging what the specification doesn't cover. L2 remembers sources. L3 remembers assertions. That boundary is where retrieval ends and intelligence begins.

Cross-domain link detection, gap analysis, and conflict surfacing are implementable and required. Full automated reasoning — entailment chains, causal inference, open-ended deduction — is aspirational at enterprise scale with current technology. The principle demands that queries return structured context (claims, conflicts, confidence, gaps), not just matching text.

**Minimum bar:** Cross-domain link detection is automated. Gap analysis (claims the graph suggests should exist but doesn't have) runs continuously. Every Apply-stage query returns not just matching claims but adjacent conflicts and confidence warnings.

---

### Principle 10: Every engagement feeds the graph.

No engagement is purely a consumer of intelligence. Every delivery, every deployment, every agent interaction generates observations that feed back. Intelligence that doesn't compound through use is a cost centre. Intelligence that compounds is infrastructure. The graph improves the more it is used.

**Minimum bar:** Every engagement has a defined feedback pathway from delivery observations to Ingest. Feedback rate (observations returned per engagement) is a tracked metric.

---

### Principle 11: Traceability is the response to acceleration.

When AI agents accelerate delivery, human oversight models break. The answer is not to slow down. It is to make every decision traceable to the intelligence that informed it. An agent acting on a confidence-scored, provenance-tracked claim is auditable. An agent acting on a document retrieved by similarity search is not.

Traceability is necessary for accountability but does not by itself prevent harm. It must operate alongside confidence thresholds that gate agent action, human oversight at defined decision points, and containment mechanisms for when the intelligence base is compromised or incomplete.

**Minimum bar:** Every agent action in a regulated workflow is traceable to the specific claims that informed it, including their confidence tier and provenance chain at the time of action.

---

### Principle 12: No unfunded mandates.

Intelligence governance that depends on volunteer effort dies. Curation time must be budgeted, priced into engagements, and protected from delivery pressure. If it isn't in the commercial model, it won't survive first contact with a quarterly target.

**Minimum bar:** Intelligence curation is a line item in engagement pricing. Curation capacity is allocated, tracked, and protected from reallocation to delivery tasks.

---

## Revision Log (v1.0 → v1.1)

| Principle | Change | Driven by |
|---|---|---|
| Preamble | Added proportionality statement — governance intensity varies by risk | SW-4: governance scaling critique |
| P1 | Added claim definition, scope requirement, lineage acknowledgment, tacit knowledge boundary | SW-2: claim undefined; SW-3: tacit knowledge; IC-3: epistemologist critique |
| P2 | Added social provenance and integrity verification | SW-5: security gap; PC: epistemologist rewrite |
| P3 | Added epistemic dependence concept, confidence ≠ truth caveat, expert-dependent status | SW-7: false precision; IC: Hardwig's epistemic dependence |
| P4 | Added contradiction taxonomy (5 types), relabeled CREST/CSDR example as jurisdictional divergence | IC-3: contradiction terminology; P4/P8 critiques |
| P6 | Added ontology evolution to semantic authority; clarified these are functional, not org chart | IC-1: bureaucratic bottleneck; IC-4: semantic brittleness |
| P7 | Strengthened Emerge guardrails — hypotheses not claims, uncontrolled Emerge is failure mode | IC-2: Emerge danger |
| P9 | Reframed as "structured inquiry" — honest about what's technically deliverable | IC-7: reasoning oversold; PD: tech architect rewrite |
| P11 | Added traceability ≠ safety caveat — operates alongside thresholds, oversight, containment | EC-2: traceability fallacy |
