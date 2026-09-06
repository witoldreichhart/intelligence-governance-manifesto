# Errata

Dated corrections to previously published content in this repository. Each entry
records what was wrong, what was done about it, and when.

## 2026-09-06

- **No entry to make: this repository was enumerated for the annex-attribution
  defect corrected in the other three and has none.** The defect is an annex
  citation whose line names no instrument, which an attribution pass then files
  under whatever instrument the surrounding prose happens to name. Enumerated
  with `command grep` over `git ls-files -- '*.md'` plus
  `git ls-files --others --exclude-standard -- '*.md'`, **14 files scanned**,
  both line-scoped and wrap-safe, and again over whole-file text with dashes
  mapped to spaces: every annex-and-numeral citation in this repository was
  taken one by one, and **each is attributed to the instrument that states it,
  and none is split across a line break**. No total is recorded, deliberately:
  this file quotes annex citations when it explains them, so a repository count
  would be counting these notes alongside the content, and would move again the
  next time an entry is added here without a single content file changing. No
  file in this repository was edited by this pass, and `manifesto.md` and its
  tracked twin at
  `papers/Manifesto_IGM_Intelligence_Governance.md` are unchanged and identical.
  This file is untracked in git, so `git grep` does not see it; the enumeration
  above does.

- **Article 72 was cited as a deployer duty. It is a provider duty; the
  provision the file was reaching for is Article 26(5).**
  `domains/public-sector.md:90` said "Article 72 (post-market monitoring for
  deployers)" and `:140` said "Article 72 (deployer post-market monitoring)".
  Read in full at the hashed primary (Regulation (EU) 2024/1689,
  `inputs/20260902-arnaud/sources/OJ_L_202401689_AIAct.html.gz`, sha256 prefix
  `a0f437e89667`), Article 72 is headed "Post-market monitoring by providers
  and post-market monitoring plan for high-risk AI systems", has four
  paragraphs, and 72(1) reads "Providers shall establish and document a
  post-market monitoring system". A deployer appears in Article 72 exactly
  once, in 72(2), as one possible *source* of the data the provider's system
  collects — never as a duty-holder. The deployer's counterpart is Article
  26(5): deployers monitor the operation of the high-risk system on the basis
  of the instructions for use and, where relevant, "inform providers in
  accordance with Article 72". So Article 72 is where a deployer's information
  goes, not an obligation it bears. Both sites re-attributed; nothing deleted.
  A third site, `:154`, paired Articles 17 and 72 with no duty-holder named at
  all in a document whose subject is a public-sector *deployer* — the same
  fault in a weaker form, and corrected the same way. This is the same defect
  fixed at `aplc/agent/agent-retirement.md:213` on 2026-09-06.

- **A missing duty, not a miscited one: the deployer's serious-incident
  obligation was cited nowhere in this repository.** Enumerated before the
  pass: `Art. 26(5)`/`Article 26(5)` — **0 occurrences**; `Art. 73`/`Article
  73` — **0**; `serious incident` (case-insensitive) — **0 lines in 0 files**.
  Unlike the Article 72 sites, this was not a wrong attribution to be
  corrected but an absent obligation to be stated, and the two close
  differently: a misattribution is repaired by naming the right holder, a gap
  by adding the duty. Article 26(5) now appears at `domains/public-sector.md`
  with all three of its limbs in-sentence — monitor on the basis of the
  instructions for use and inform the provider under Article 72 where
  relevant; on reason to consider a risk within the meaning of Article 79(1),
  inform the provider or distributor and the market surveillance authority
  without undue delay "and shall suspend the use of that system"; and, "Where
  deployers have identified a serious incident, they shall also immediately
  inform first the provider, and then the importer or distributor and the
  relevant market surveillance authorities of that incident", with Article 73
  applying *mutatis mutandis* only where the deployer cannot reach the
  provider. No after-count is recorded: this entry cites Article 26(5) several
  times itself, so any repository figure would be a count of this note as much
  as of the duty it describes.

- **The Article 27 FRIA was attributed to "operators". Article 3(8) makes that
  six roles; Article 27(1) binds a scoped subset of one of them.**
  `domains/public-sector.md:20` said "Public bodies and certain operators of
  high-risk systems must perform an FRIA before deployment". At the primary,
  "'operator' means a provider, product manufacturer, deployer, authorised
  representative, importer or distributor" — five of those six owe no FRIA.
  Article 27(1) binds "deployers that are bodies governed by public law, or
  are private entities providing public services", and deployers of Annex III
  point 5 (b) and (c) systems (creditworthiness scoring; risk assessment and
  pricing for life and health insurance). The row also omitted the carve-out
  that limits it: the duty applies to Article 6(2) high-risk systems "with the
  exception of high-risk AI systems intended to be used in the area listed in
  point 2 of Annex III" — critical infrastructure — so a public body deploying
  an Annex III point 2 safety component owes no Article 27 FRIA at all. That
  omission is the same one the `aplc/` pass found. Article 27(2)'s first-use
  and update rule and Article 27(3)'s notification to the market surveillance
  authority were also absent and are now stated. This is the fifth site of the
  corpus-wide *operator* pattern.

- **Method note, and the shape of the enumeration.** Every verdict above was
  re-derived at the hashed primary rather than inherited from the routing
  brief: Articles 26, 27 and 72 were read end to end, and 42 byte-comparisons
  were run through the checker's own `normalizeForMatch` with a prefix-safe
  negative twin for every positive control (numerals swapped only within digit
  width — 72→74, 73→79, 79→75, point 2→point 8, points 5→points 7, six→nine
  months — and word swaps chosen so neither string prefixes the other:
  providers→deployers, deployers→operators, distributor→contractor,
  suspend→continue, system→model, first→second). Zero unexpected results. The
  `operator` enumeration was run from *inside* this repository —
  `command grep -rniE '\boperators?\b' --include='*.md' .` — because a
  root-level grep is blind to a nested repository. It reached three content
  lines and the fault was at one of them, `domains/public-sector.md:20`. The
  totals that command prints are not recorded here: this file uses the word
  freely, so the command returns more today than when it was run, and the
  difference is this file, not the repository it was measuring.
  The other two, `domains/personal-data-and-data-act.md:29` and `:150`, use
  *operator* in ordinary English about DPA enforcement against AI-system and
  foundation-model operators, make no EU AI Act duty claim, and were left
  alone. The routing brief named one site and the enumeration found exactly
  that one — but it was run rather than assumed.
- **Re-enumerated for the remaining annex-attribution defect: still none.**
  The 2026-09-06 entry above recorded no site of this class here. It was
  re-derived, not inherited, because re-measurement grew the class elsewhere:
  the checker's refusal list was read in full, `--dump-triples` was filtered to
  annex citations, and wrap-safe and whole-file normalised scans were run over
  **14 files** in this repository. No annex citation here is attributed to any
  instrument other than the one that states it, and no refusal names this
  repository. This file is untracked in git; `manifesto.md` was not edited, so
  its tracked twin is unchanged.
- **Annex citations hidden by a line break: none here, re-derived.** The
  adjacent class — annex citations split across a line break, invisible to the
  line-scoped extractor rather than mis-filed — was enumerated with a wrap-safe
  scan and a whole-file normalised scan (blockquote and list markers stripped
  before joining, dashes mapped to spaces, **no filter by instrument**) over
  `git ls-files` plus `git ls-files --others --exclude-standard`: **14 files**
  here, **210** in the corpus. **Zero sites in this repository**, against a
  positive control on the identical command and file set and a fresh long
  negative control returning zero. Sixteen were found elsewhere and all sixteen
  are closed. This file is untracked in git; `manifesto.md` was not edited, so
  its tracked twin is unchanged.
- **A corpus claim in this file was measuring this file: absence-and-count
  claims about this repository, corrected without substituting a new number.**
  The class is a claim about *this corpus* that its own file falsifies — a note
  recording that something is absent, or that it stands at so many lines,
  published into a file that is itself inside the search space, so that the
  sentence moves the number it reports. It is distinct from a claim about the
  text of an external instrument: the notes here recording that a phrase is
  absent from a hashed primary are unaffected by this file quoting the phrase,
  and every one of them was left exactly as it stood. Three sites here were of
  the corpus-scoped kind and all three are corrected.
  · **Two of the three were already wrong when they were written, not merely
  overtaken.** The method note above printed a search command and its line total
  for a role word; the entry immediately above it in this same dated section uses
  that word repeatedly, so the total was short before the ink dried, and the
  command as printed now returns a much larger number of which most is this file.
  The serious-incident entry gave an after-the-pass occurrence figure for the
  deployer's provision while citing that provision several times in the same
  paragraph. The third had drifted rather than started wrong: the
  annex-attribution entry gave a repository total that was correct when written
  and was moved by two later entries in the same dated section, with no content
  file changing.
  · **The form of the correction is the same at every site, and it is not a
  smaller number.** A figure written "excluding this note" goes stale at the next
  entry with no word changing, which is the same trap one order out. Each
  sentence now makes a claim about named lines — what is at them, and what is
  attributed there — which nothing written elsewhere can move. Where a figure was
  dropped the sentence says why, so a reader does not read the absence as an
  oversight rather than as a choice.
  · **Controls.** A fresh two-word negative control was chosen only after
  confirming it was absent from every Markdown and HTML file in the corpus, and
  was then run with the identical command and file set as a positive control that
  hit a large share of them. Its result is deliberately not written here as a
  figure, and the string itself is not reproduced: recording a control in a
  published file is what burns it, and earlier controls in this corpus are
  already unusable for exactly that reason, some of them recorded in this file.
  That is the same effect this entry describes, one level up. **The cost of this
  form is real and is stated rather than hidden: a reader cannot re-run a control
  they cannot see.** The positive control carries the weight instead — it is
  supposed to be present, so publishing it cannot burn it, and a run in which it
  fails to hit is a broken search rather than a demonstrated absence.
  · This file is untracked under `D-57`, so a `git diff` run in this repository
  does not show this entry. It was written anyway, and this line says so.
  `manifesto.md` was not edited, so its tracked twin is unchanged.


---

## 2026-09-05

- **Every numeric threshold in this repository now carries its register in the
  same sentence as the number.** Three registers are used: *measured* (with the
  measurement named), *policy-set* (a chosen default, said so), and
  *illustrative* (a worked hypothetical). Where neither measurement nor
  authorial choice could be established from the corpus, the figure is marked
  *origin not established* rather than assigned a register on a guess. No
  figure was changed and none was deleted; the decay-class windows, the
  critical-path and triage share bands, the auto-revalidation share, the
  maturity and rollout timelines, the leading- and lagging-indicator targets,
  the Epistemic Tier Waiver cap and portfolio limits, the Revision-authority
  domain limit, the escalation deadlines and the staleness reference points are
  all now marked in place. The caveat is deliberately in-sentence rather than
  in a footnote: a footnoted qualifier is stripped the first time a figure is
  lifted into a slide, and a sentence is harder to strip than a footnote
  (`D-42`, `D-43`). Files: `glossary.md`, `implementation-guide.md`,
  `manifesto-principles.md`, `companion-guide.md`, `governance/queries.md`,
  `domains/personal-data-and-data-act.md`.

- **Fabricated DORA quotation withdrawn.** `domains/financial-services.md`
  quoted DORA Article 11 as requiring "sufficient and appropriate records."
  That phrase occurs zero times in the Regulation. The quotation marks and
  the attribution were withdrawn; the underlying point — that DORA Article
  11 imposes some records obligation on ICT systems — was kept, unquoted,
  since the scope of that duty has not itself been signed off. No
  replacement quotation is asserted.

- **DORA Article 11 records duty re-cited to the paragraph that carries it.**
  After the fabricated "sufficient and appropriate records" quotation was
  withdrawn (entry above), `domains/financial-services.md:40` was left saying
  that DORA Article 11 "imposes a records obligation on ICT systems". The
  instrument is right and the scope is wrong. Article 11 is *Response and
  recovery*, and its record duty is paragraph 8: financial entities shall keep
  readily accessible records of activities before and during disruption events
  when their ICT business continuity plans and ICT response and recovery plans
  are activated — a duty about activities during disruption, not a duty about
  ICT systems. The sentence now states the Article 11(8) duty, unquoted, and the
  in-sentence bracket records the correction. Read at primary against
  `inputs/20260905-arnaud/prep/asdlc-standards/sources/dora_fulltext.txt`
  (sha256 prefix `25328c7e39c4`); no replacement quotation is asserted. The note
  follows the form of the Article 11 note it replaces at `:40` and of the
  Article 5(2)(g) note below, so a reader can see the three were found by one
  process.

- **Second fabricated DORA quotation withdrawn, and the obligation re-attached
  to the party that bears it.** `domains/financial-services.md` quoted DORA
  Article 5 as requiring that ICT risk management frameworks be "adequately
  resourced." A whole-text search of Regulation (EU) 2022/2554 returns
  "resourced" zero times, so the phrase is not a quotation of the instrument.
  Two things were wrong, not one: the quotation marks, and the subject. Article
  5(2)(g) binds the *management body* to allocate and periodically review the
  appropriate budget to fulfil the financial entity's digital operational
  resilience needs in respect of all types of resources — a duty on a body to
  set a budget, not a duty on a framework to be resourced. The sentence now
  states the Article 5(2)(g) duty unquoted and against the management body; no
  replacement quotation is asserted. The withdrawal note follows the form of
  the Article 11 note at `:40` in the same file, so a reader can see the two
  were found by one process.

---

[← Back to README](README.md)
