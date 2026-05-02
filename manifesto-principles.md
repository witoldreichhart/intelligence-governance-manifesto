# Sixteen Principles of Intelligence Governance

*Each principle includes a minimum bar — the absolute floor of implementation. Principles without minimum bars are aspirations, not governance.*

*Governance intensity should be proportionate to risk. Claims that gate agent action in regulated workflows require full governance. Claims used for informational support may warrant lighter treatment. The principles below define the ceiling, not a uniform floor.*

These sixteen principles govern the substrate from which organizational intelligence emerges. Knowledge — structured claims with provenance, confidence, and scope — is what the system holds. Organizational intelligence — the institutional capacity to perceive relevant patterns, infer consequences, and select action opportunities aligned with purpose — is what the system enables. The principles maintain the substrate. What emerges on top depends on how well the substrate is built and maintained.

> **Terminology note (v1.3).** The IGM tier system previously called "confidence" is renamed **epistemic tier** to free the word *confidence* for its AEM verification meaning ("did the change pass the gates we agreed on") and to make the IGM tier collision with AEM/AEnt-M usage explicit. The tier names (Provisional, Candidate, Confirmed, High Confidence, Authoritative) and their semantics are unchanged; only the umbrella term is renamed. References to "confidence" in earlier revisions of this manifesto and its companion documents read as "epistemic tier" unless the surrounding text refers to AEM-style verification confidence. See the unified glossary's term-collision appendix for the full mapping.

When these principles operate together over time — when confidence is continuously earned, decay is actively governed, contradictions are preserved, and every engagement feeds back — something structural changes: the enforcement locus of governance migrates from synchronous pre-action gating to the substrate's own causal architecture. This is governance relocation. It is not a separate principle. It is the emergent consequence of the twelve principles working in concert on a deepening substrate.

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

**Decay triage — normative four-priority model.** At enterprise scale, the graph may contain tens or hundreds of thousands of claims. Revalidating all of them on schedule is not realistic without triage. The following four-priority model is normative; implementations may vary the percentage thresholds but must publish them.

| Priority | Definition | Typical share | Revalidation cadence |
|---|---|---|---|
| **P1 — Critical-path** | On the active reasoning path of agent workflows currently in production. | 5–15% of graph | Shortest decay window; revalidated first |
| **P2 — High-dependency** | Many downstream dependents (per IGQ-17/IGQ-18). Stale = systemic risk. | 10–20% of graph | Prioritised by blast radius |
| **P3 — Active-domain** | In domains with running or recently completed engagements. | 20–30% of graph | Maintained at high freshness |
| **P4 — Dormant** | No current engagements, no active agent workflows. | balance | Quarterly or semi-annual; "revalidation pending" flag retained; promoted to P3 on engagement reactivation |

Auto-revalidation handles the unambiguous cases (regulatory source unchanged since last validation → decay clock resets). Human review is reserved for ambiguous signals and high-impact claims; in practice auto-revalidation handles 40–60% of revalidation volume.

**Minimum bar:** Every claim has an expected validity window and a decay class. Claims past their window trigger review alerts. Staleness metrics are tracked per domain. Critical-path (P1) claims are revalidated before any P3 or P4 claim in the same window. Curate events on claims that affect any agent product's composite state follow the class-based precedence in [`/integration/composite-state-vs-curate-precedence.md`](../../integration/composite-state-vs-curate-precedence.md), which specifies the AEnt-M P9 acceptance pathway per class (Class 1 routine revalidations within decay-window bounds — pre-accepted; Class 2 consequential demotions on High/Critical critical-path claims — 4-hour SLO with named Accountable Authority; Class 3 emergency retirements on integrity grounds — bypass with 24h post-hoc review). The Revision authority is responsible for class assignment at decision time and the assignment is part of the audit trail.

---

## Part II — Principles of Intelligence Operations

*How the organisation must run it.*

### Principle 6: Four authorities govern the graph.

**Semantic authority** — who defines the vocabulary, ontology, and allowed relation types. Semantic authority includes ontology evolution — adding, refining, or restructuring the vocabulary as domains change and new concepts emerge. **Assertion authority** — who creates, validates, promotes, supersedes, or retires claims. **Inference authority** — who defines the rules by which claims support, contradict, or entail each other. **Revision authority** — who handles challenge, contradiction, confidence downgrade, and decay.

Every claim-affecting action maps to exactly one authority. Ungoverned authorities produce ungoverned graphs.

These are functional authorities, not job titles. In practice, one role may exercise multiple authorities. In a small implementation, a single domain lead may hold assertion and revision authority. What matters is that every governance action is traceable to the authority that sanctioned it.

**Authority escalation — normative deadlines.** The four authorities will conflict. The escalation rules below are normative, not advisory:

- **Within-scope conflicts** (two authorities disagree about a claim within one domain) are resolved by the assertion authority for factual disputes and the semantic authority for structural disputes. If they disagree with each other, the revision authority adjudicates.
- **Cross-scope conflicts** (a decision in one domain affects governance in another) are escalated to the knowledge governance committee — or the institutional body holding cross-domain authority.
- **10-business-day deadline.** A conflict that remains unresolved for **more than 10 business days must be escalated** to the next level (within-scope → cross-scope; cross-scope → committee).
- **30-business-day deadline.** A conflict that remains unresolved for **more than 30 business days triggers a temporary governance hold** on affected claims — they remain in the graph but are flagged as governance-pending, which lowers their effective epistemic tier for agent-action thresholds.
- **Two-authority requirement.** No authority may unilaterally promote a claim to Authoritative or unilaterally retire a claim with active downstream dependencies. Both actions require two-authority agreement.

**Minimum bar:** All four authorities are explicitly assigned to named roles or functions. Authority boundaries are documented. No claim is created, promoted, or retired without the responsible authority's involvement. The 10-/30-business-day escalation deadlines are tracked as operational SLOs and are reportable to second-line oversight.

Retirement workflows (for agents and for claims) follow [`/integration/decommissioning.md`](../../integration/decommissioning.md), which specifies the five-phase workflow (trigger → impact analysis → disposition decisions → 30-day grace period → execution → post-retirement audit), the disposition matrix for claims maintained primarily for a retiring agent (preserve / preserve-for-regulator / demote-to-archive / retire), and the named-authority chain (Revision + Assertion + APLC product manager + system steward + AEnt-M P8 authorities for affected action classes). The Revision authority is the IGM-side accountable party for terminal claim retirement decisions and for class assignment under `/integration/composite-state-vs-curate-precedence.md`.

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

**The L1 / L2 / L3 memory layer model — normative.** Intelligence in a governed system operates at three layers; each carries different governance obligations. The model below is promoted from companion-guide into the principles because it is load-bearing for every Apply-stage query.

| Layer | What it holds | Governance concern | Primary controls |
|---|---|---|---|
| **L1 — Working memory** | Claims and practitioners' situated knowledge loaded in active context at the moment of action; a governed window into L2 and L3 filtered by task scope, authorisation, and recency. | What gets loaded into L1 determines decision quality. Stale, low-tier, or out-of-scope claims contaminate the decision regardless of reasoning quality. | Scope-match enforcement; freshness gates; epistemic-tier floors; contradiction surfacing. |
| **L2 — Institutional memory** | The curated, validated, connected domain graph the institution has accumulated. | Where epistemic debt accumulates. L2 is the system's immune-function target. | The full intelligence lifecycle (Ingest → Consolidate → Curate → Expand → Apply) operates on L2. |
| **L3 — Foundational intelligence** | Stable, deeply connected structural knowledge: regulatory architectures, domain mechanics, institutional patterns. | L3 changes are rare but high-impact; cascading effects touch every L2 claim that depends on it. | Change detection with cascade analysis; L3 revalidation is always human-reviewed — automated revalidation is not appropriate. |

L3 provides the structural foundation. L2 builds institutional knowledge on that foundation. L1 selects from L2 (and references L3) what is relevant to the current decision. If any layer is defective — stale L3, polluted L2, mis-scoped L1 — the defect propagates.

For the relationship between this internal layer model and the external Knowledge / Organizational Intelligence / Governed Intelligence three-level hierarchy in `manifesto.md`, see the "Which layer are you governing?" section in the manifesto.

**Minimum bar:** Cross-domain link detection is automated. Gap analysis (claims the graph suggests should exist but doesn't have) runs continuously. Every Apply-stage query returns not just matching claims but adjacent conflicts and epistemic-tier warnings. L1 working memory is scope-checked, freshness-gated, and tier-floored. L3 changes trigger cascade analysis with human-reviewed revalidation.

---

### Principle 10: Every engagement feeds the domain graph.

No engagement is purely a consumer of intelligence. Every delivery, every deployment, every agent interaction generates observations that feed back into the domain graph — the shared institutional substrate that no single engagement owns but every engagement enriches. Intelligence that doesn't compound through use is a cost centre. Intelligence that compounds is infrastructure.

The domain graph sits between foundation model capability and application context. It is the accumulated, governed, reusable domain substrate: how settlement workflows interact with penalty regimes, how regulatory requirements cascade through product hierarchies, how operational workarounds interact with control frameworks. Each engagement that operates on the domain graph enriches it — gaps identified, claims validated against operational reality, cross-domain edges discovered. This is fertility: the rate at which existing knowledge generates new knowledge through operation.

**Minimum bar:** Every engagement has a defined feedback pathway from delivery observations to Ingest. Feedback rate (observations returned per engagement) is a tracked metric. The domain graph — not engagement-specific knowledge stores — is the primary destination for feedback.

**Production-incident feedback path.** Production operation is itself an engagement on the substrate, and production incidents are the highest-signal observations that engagement produces. For systems governed under the Agentic SDLC (ASDLC) whose actions are informed by claims in the domain graph, the ASDLC's Layer 4 incident and steward-review process (see ASDLC `asdlc.md` Feedback Paths, *L4 → Intelligence Lifecycle*) must produce a structured feedback artefact identifying which claims informed the failed action, whether those claims were stale, contradicted, or misapplied, the IGM revision/assertion/semantic authorities responsible for the affected claims, and a re-verification timeline not exceeding 30 calendar days from incident closure. The Ingest authority is responsible for accepting the feedback into the domain graph and routing the re-verification work to the appropriate authority. An incident-feedback artefact that does not reach Ingest within the post-incident SLO window is a Principle 10 compliance gap, not an operational backlog item.

---

### Principle 11: Traceability is the response to acceleration.

When AI agents accelerate delivery, human oversight models break. The answer is not to slow down. It is to make every decision traceable to the intelligence that informed it. An agent acting on an epistemic-tier-scored, provenance-tracked claim is auditable. An agent acting on a document retrieved by similarity search is not.

Traceability is necessary for accountability but does not by itself prevent harm. It must operate alongside epistemic-tier thresholds that gate agent action, human oversight at defined decision points, and containment mechanisms for when the intelligence base is compromised or incomplete.

**Epistemic circuit breaker — normative specification.** When the epistemic-tier of claims required for an action falls below the threshold for that action's consequence class, the system **must halt the action** and produce a structured escalation. The agent does not silently degrade to best-effort.

| Consequence class | Example (FS) | Circuit-breaker behaviour |
|---|---|---|
| **Low** | Internal research query, non-client-facing | Log epistemic-quality warning. Agent proceeds. |
| **Medium** | Client recommendation, internal report | Agent pauses. Human reviewer sees epistemic-quality summary. Human decides. |
| **High** | Trade execution, regulatory filing, compliance determination | Agent halts. Named accountable human reviews full reasoning chain with epistemic tiers, provenance, and contradiction flags. |
| **Critical** | Cross-border regulatory submission, systemic risk assessment | Agent halts. Two-person review with escalation to governance authority. |

A circuit-breaker activation produces a structured escalation: which claims triggered the breaker, their epistemic tiers, the specific defect (staleness, contradiction, scope mismatch, broken provenance), and what action is blocked pending resolution. SLAs for resolution are set per workflow (settlement-related breakers in active trading windows: hours; compliance-interpretation breakers outside reporting season: days), not per breaker type.

**Activation rate is an inverse indicator of governance relocation.** Rising activation rates with stable substrate depth indicate insufficient relocation; declining activation rates with stable or improving decision quality indicate relocation is working. Circuit-breaker frequency is therefore a measurement, not only a halt mechanism, and is reported alongside relocation metrics in second-line oversight.

**Minimum bar:** Every agent action in a regulated workflow is traceable to the specific claims that informed it, including their epistemic tier and provenance chain at the time of action. Epistemic circuit breakers are configured per consequence class as above, halt action when the tier threshold is not met, produce a structured escalation, and report activation rates as a system-health metric.

---

### Principle 12: No unfunded mandates.

Intelligence governance that depends on volunteer effort dies. Curation time must be budgeted, priced into engagements, and protected from delivery pressure. If it isn't in the commercial model, it won't survive first contact with a quarterly target.

**Minimum bar:** Intelligence curation is a line item in engagement pricing. Curation capacity is allocated, tracked, and protected from reallocation to delivery tasks.

---

## Part III — Principles of Substrate Integrity

*What protects the substrate from epistemic, adversarial, architectural, and emergent failure.*

The first twelve principles describe the architecture of governed intelligence and how the organisation must run it. Principles 13–16 address what protects that substrate when it is treated as load-bearing infrastructure for AI agents: the difference between agreement and reality, the substrate as an attack surface, the architectural assumptions the IGM relies on but does not provide, and the emergent behaviour produced by multi-agent systems reading and writing the same graph. These principles wire IGM into the AEM principles it depends on (AEM P3 architecture, AEM P8 evaluations, AEM P10 emergence and containment) without restating them.

---

### Principle 13: Claims must be validatable, not only corroborated.

Corroboration — multiple independent sources agreeing — is necessary but not sufficient. Two sources agreeing on a falsehood produce a high-tier wrong claim. Promotion to Confirmed or higher requires at least one **validation event**: a check against an observable reality that was not itself used as a corroborating source. Regulatory claims validate against regulatory text in primary form. Operational claims validate against system behaviour, transaction data, or reproducible operational evidence. Procedural claims validate against the recorded execution of the procedure.

A validation event is recorded as a first-class object with method (what was checked), evidence (what was observed), date, and the named role that performed the check. The validation source must be independent of the corroborating sources used to support the claim — re-reading the same documents that produced the claim is not validation. Validation events have their own decay: a claim validated against transaction data from two years ago is not, today, a validated claim.

This is the IGM counterpart to AEM Principle 8 (*Evaluations are the contract*). Where AEM P8 demands evaluation portfolios that test agent behaviour against observable reality, IGM P13 demands the same of the claims agents reason over. Claim corroboration tells you sources agree; claim validation tells you sources agree with reality. Promotion above Supported requires both.

The failure mode this principle prevents is **confidence laundering** — accumulating high epistemic tier by stacking weak corroboration. A claim with five citations to documents that all derive from one upstream source has one corroboration, not five, and zero validation events. The system must detect and reject such stacking.

**Minimum bar:** Every claim above Supported epistemic tier carries at least one recorded validation event with method, evidence, date, and named validator. Validation sources are demonstrably independent of corroborating sources. Validation events themselves carry decay windows. Promotions that fail the validation requirement are rejected, not silently approved.

---

### Principle 14: Claims are attack surfaces.

The domain graph is a high-value asset and must be threat-modelled as such. The substrate's attack surface includes:

- **Claim poisoning** — adversarial insertion of false claims through Ingest, Extract, or Capture paths.
- **Provenance spoofing** — forging or altering source attributions so that claims appear to originate from authoritative sources.
- **Tier manipulation** — adversarial promotion of claims by stacking corroborating sources or compromising assertion authority credentials.
- **Indirect prompt injection** in Ingest — adversarial content embedded in harvested or extracted material that targets downstream agent reasoning rather than human readers (Slack-AI 2024 class).
- **Contradiction injection** — adversarial insertion of contradictions designed to trigger denial-of-service through curation backlog or to force premature resolution in the attacker's favour (CSA 2026 class).
- **Insider tampering by authority-holders** — abuse of legitimate Semantic, Assertion, Inference, or Revision authority credentials to corrupt the substrate from within.

IGM Principle 2 requires provenance integrity to be verifiable, not just recorded. This principle specifies the verification mechanisms and extends them to the substrate as a whole.

This principle is the IGM counterpart to AEM Principle 10 (*Assume emergence; engineer containment*) for adversarial rather than emergent failure. The two interact: an adversary who poisons a claim that subsequently feeds multi-agent reasoning produces emergent harm whose root cause is in the substrate, not in any single agent. The detection and response paths from P14 (substrate integrity) and P16 (substrate-driven emergence) must be wired together.

**Minimum bar:** Cryptographic provenance signatures on all claims at intake; signature verification on every Apply-stage retrieval. Write-path access controls separated from read-path — the credentials that allow an agent to read the graph cannot, by themselves, write or promote claims. Continuous integrity monitoring with tamper alerts on claim content, provenance metadata, and epistemic-tier transitions. Indirect-prompt-injection scanning is part of Ingest, not optional. Quarterly red-team of the graph itself (not just of agents that consume it), exercising at least the six attack classes named above. A named **owner of substrate security**, distinct from the four governance authorities and reporting through an independent line, accountable for the integrity programme.

> **DRAFT — author review needed.** The "owner of substrate security" is positioned as a fifth named role distinct from the Semantic, Assertion, Inference, and Revision authorities. Authors should confirm whether this should be a fifth functional authority or a separate security function reporting to an external CISO line.

---

### Principle 15: Architectural enforcement is assumed, not provided.

The IGM governs the knowledge layer — what claims exist, what they support, what agents may do with them. It does not provide the architectural defense-in-depth on which the substrate's integrity depends: machine-enforced policies, repository gates, type contracts, lint rules, domain ownership maps, CI checks, runtime sandboxes, and the rest of the architectural envelope. Those are the responsibility of the consuming system's engineering layer, governed by AEM Principle 3 (*Architecture is the first line of defense; treat it as production code*).

A perfectly governed knowledge base on an architecturally unprotected system is a liability, not an asset. Validated, high-tier claims served to agents through an unguarded API, a permissive runtime, or an unmonitored write path produce *higher* operational risk than no claims at all — because the agent and its reviewers trust them. IGM-governed intelligence amplifies whatever architecture it sits on. Without AEM P3 controls, that amplification is in the wrong direction.

This principle is therefore deliberately a **stub**. It declares the dependency and refuses to restate AEM P3. Implementations must demonstrate AEM P3 compliance for the consuming system before claiming an IGM substrate is operational; reviewers and auditors must look for that evidence and reject IGM deployment claims that lack it.

**Minimum bar:** Deployment of an IGM substrate requires evidence that AEM Principle 3 is implemented for the consuming system — including, at minimum, machine-enforced policies on agent action, repository and CI gates on substrate writes, domain ownership maps that the substrate's authorities map onto, and runtime sandboxing of agents that consume claims. Absence of this evidence is a P0 finding for IGM operational readiness, not a documentation gap.

---

### Principle 16: Containment is required for substrate-driven emergence.

Multi-agent systems reading and writing the same substrate exhibit emergent behaviour that no single agent's design accounts for: feedback loops where agent A's output becomes a corroborating source for agent B's claim that agent A then re-ingests; cascading promotions where a routine epistemic-tier change triggers re-evaluation across dependent claims and produces graph-wide tier inflation; **self-corroborating false claims**, where claim A is supported by B which is supported by A through a path the system did not detect; contradiction churn, where claims are repeatedly demoted and re-promoted by competing agents without convergence.

These behaviours are not pathologies of any individual agent. They are properties of the agent-substrate system, observable only when multiple agents interact through the shared graph at scale. Without containment, they degrade the substrate silently — high epistemic-tier metrics rise while operational reliability falls.

This principle is the IGM counterpart to AEM Principle 10 (*Assume emergence; engineer containment*) for the substrate itself. Where AEM P10 contains emergence in agent execution, IGM P16 contains emergence in the knowledge layer those agents share.

**Minimum bar:** Rate limits on epistemic-tier promotions per source per window — no single source, automated or human, may drive more than a defined number of promotions per unit time. Detection of self-corroboration cycles — the system must surface, not silently accept, support paths where claim A is corroborated by B which is itself corroborated (transitively) by A. Circuit breakers on cascading retirements — when a single retirement triggers more than a threshold number of dependent retirements within a window, the cascade is paused for human review. Audit trail showing which agents touched which claims, retained for a period at least as long as the slowest decay class.

> **DRAFT — author review needed.** Specific rate-limit thresholds, cycle-detection depth, and cascade thresholds are intentionally left unspecified at the principle level; authors should decide whether to fix them in implementation guidance or to leave them per-deployment.

---

## Revision Log

> **Abbreviation system used in the *Driven by* column.** Codes refer to internal review streams that produced each finding. The current canonical mapping is:
>
> | Code | Stream | Description |
> |---|---|---|
> | **SW-n** | Stakeholder Workshop finding *n* | Findings raised in stakeholder workshops with practitioners, regulators, or domain SMEs reviewing the IGM. |
> | **IC-n** | Internal Critique finding *n* | Findings from the internal critique cycle (epistemologist, technical architect, regulatory reviewer). |
> | **PC** | Peer-Critique rewrite | Section-level rewrites driven by peer critique (typically from a named external reviewer; e.g. *PC: epistemologist rewrite*). |
> | **PD** | Peer-Driven rewrite | Section-level rewrites driven by an external practitioner reviewer (e.g. *PD: tech architect rewrite*). |
> | **EC-n** | External Critique finding *n* | Findings from external critics (academic, industry, regulatory) outside the standing review pool. |
> | **Coherence review** | Cross-manifesto coherence review of 2026-05-02 | Findings carrying B-numbers (Critical Twelve blockers) or W-numbers (waves of remediation) trace to the IGM↔AEnt-M coherence review at repo root. |
>
> *DRAFT — author review needed: confirm that SW/IC/PC/PD/EC mappings above match the authors' intended meaning. If a code below is missing from this table or mapped wrongly, update the legend rather than retro-naming individual entries.*

| Version | Principle | Change | Driven by |
|---|---|---|---|
| v1.1 | Preamble | Added proportionality statement — governance intensity varies by risk | SW-4: governance scaling critique |
| v1.1 | P1 | Added claim definition, scope requirement, lineage acknowledgment, tacit knowledge boundary | SW-2: claim undefined; SW-3: tacit knowledge; IC-3: epistemologist critique |
| v1.1 | P2 | Added social provenance and integrity verification | SW-5: security gap; PC: epistemologist rewrite |
| v1.1 | P3 | Added epistemic dependence concept, confidence ≠ truth caveat, expert-dependent status | SW-7: false precision; IC: Hardwig's epistemic dependence |
| v1.1 | P4 | Added contradiction taxonomy (5 types), relabeled CREST/CSDR example as jurisdictional divergence | IC-3: contradiction terminology; P4/P8 critiques |
| v1.1 | P6 | Added ontology evolution to semantic authority; clarified these are functional, not org chart | IC-1: bureaucratic bottleneck; IC-4: semantic brittleness |
| v1.1 | P7 | Strengthened Emerge guardrails — hypotheses not claims, uncontrolled Emerge is failure mode | IC-2: Emerge danger |
| v1.1 | P9 | Reframed as "structured inquiry" — honest about what's technically deliverable | IC-7: reasoning oversold; PD: tech architect rewrite |
| v1.1 | P11 | Added traceability ≠ safety caveat — operates alongside thresholds, oversight, containment | EC-2: traceability fallacy |
| v1.2 | Preamble | Added organizational intelligence framing — principles govern substrate from which intelligence emerges. Added governance relocation as emergent consequence of principles operating together. | Manifesto v1.2: organizational intelligence hierarchy, governance relocation mechanism |
| v1.2 | P10 | Renamed to "Every engagement feeds the domain graph." Added domain graph as shared institutional substrate, fertility concept, clarified feedback destination. | Manifesto v1.2: domain graph as enterprise substrate |
| v1.3 | Preamble | Renamed IGM "confidence" → "epistemic tier" with explicit terminology note; tier names and semantics unchanged. | IGM↔AEnt-M coherence review T1 (vocabulary collision) |
| v1.3 | P13 (new) | Added "Claims must be validatable, not only corroborated." Wires IGM to AEM P8 evaluation portfolios; defines validation event as a first-class object distinct from corroboration; names confidence laundering as the prevented failure mode. | Coherence review B2 / W1.2 |
| v1.3 | P14 (new) | Added "Claims are attack surfaces." Threat-models the substrate (claim poisoning, provenance spoofing, tier manipulation, indirect prompt injection in Ingest, contradiction injection, insider tampering); requires cryptographic provenance, write/read path separation, integrity monitoring, quarterly graph red-team, and a named substrate-security owner distinct from the four authorities. Wires IGM to AEM P10 for adversarial failure. | Coherence review B3 / W1.3 |
| v1.3 | P15 (new) | Added "Architectural enforcement is assumed, not provided" as a stub principle declaring delegation to AEM P3 for architectural defense-in-depth. Makes the dependency on AEM P3 explicit and a precondition for IGM operational readiness. | Coherence review T2 / W2.2 |
| v1.3 | P16 (new) | Added "Containment is required for substrate-driven emergence." Names feedback loops, cascading promotions, self-corroboration cycles, and contradiction churn as emergent failure modes of multi-agent systems on a shared substrate; requires rate limits, cycle detection, cascade circuit breakers, and an agent-touch audit trail. Wires IGM to AEM P10 for emergent failure. | Coherence review T2 / W2.5 |
| v1.3 | Revision Log | Added abbreviation legend (SW/IC/PC/PD/EC) so the *Driven by* column is intelligible to first-time readers. | Coherence review W3.3 / IGM internal audit (45 findings) |
| v1.3 | P5 | Promoted decay-triage four-priority model (P1 critical-path → P4 dormant) from implementation-guide to principles as normative; added decay class to minimum bar; specified P1 revalidates before P3/P4. | Coherence review W3.4 (load-bearing operational detail) |
| v1.3 | P6 | Promoted authority-escalation rules (10-/30-business-day deadlines, two-authority requirement for Authoritative promotion / dependency retirement) from companion-guide to principles as normative; added SLO reporting to second-line in minimum bar. | Coherence review W3.4 (load-bearing operational detail) |
| v1.3 | P9 | Promoted L1/L2/L3 memory-layer model from companion-guide-only to principles as normative; added scope-check, freshness-gate, tier-floor, and L3 cascade-with-human-review to minimum bar. | Coherence review W3.4 / W3.5 (memory-layer reconciliation) |
| v1.3 | P11 | Promoted epistemic-circuit-breaker specification from implementation-guide to principles as normative; added consequence-class table; reframed activation rate as inverse indicator of governance relocation rather than only a halt mechanism. | Coherence review W3.4 / W3.5 (tense/inversion fix on circuit-breaker framing) |
