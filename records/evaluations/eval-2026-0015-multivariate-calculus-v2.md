# EVAL-2026-0015: Candidate evaluation — multivariate calculus v2

**Candidate ID/version:** CAN-2026-0014, `multivariate-calculus-v2.html`, evaluated build SHA-256 `f8160916b1e8adb5c2e559bdba1152e21bd18e129ebed79d97fa44314d96cc37`, 172,174 bytes; post-review revision 1 (remediated) SHA-256 `3c0bf64a797cae398f8ae66de933f0521b78d6f5f7b0780d33987d2eb80b78e9`, 172,763 bytes  
**Rubric version:** [evaluation-framework.md](../../docs/06-evaluation/evaluation-framework.md) (Stage 1 anchors, WF-007) against [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) and the [depth-calibration contract](../../docs/01-product/depth-calibration-contract.md)  
**Evaluator role/identity:** Repository maintainer (solo Stage 1 operator), generator of the same candidate  
**Evaluation mode:** automated checks + agent-performed specialist review + rendered browser execution  
**Operating scope:** Stage 1 private pilot  
**Review independence:** non-independent  
**Reviewer relationship or limitation:** the evaluator generated the candidate in the same session; no second reviewer participated; all dimension scores are evidence-anchored and reproducible from the run ledger  
**Public-release eligibility:** ineligible  
**Confidence:** high  
**Recommendation:** private-pilot-complete  
**Iterations reviewed:** builds = 3 in-session (superseded before evaluation: `f5465b1f…` → `1c9d3a5d…`), final evaluated build = `f8160916…`; revision cycles = 1 post-review (learner-reported interaction-state styling restoration, `f8160916…` → `3c0bf64a…`; 3 in-generation artifact corrections + 2 harness corrections; per [ADR-0006](../../docs/adr/0006-record-iteration-accounting.md), itemized in [RUN-20260929-0001](../runs/run-20260929-0001-multivariate-calculus-v2.md))

## Scope and evidence inspected

The final artifact at the hash above; `scripts/verify-candidate.py` strict run (0 failures; 7 canvases, 7 ladders, 15 formulas, ~44 glossary entries, per-element slider encapsulation, font floor, option stacks, callout discipline); the 118-check independent Python recomputation harness; `node --check` plus a 48-check stub-DOM behavioral harness; the assembled body read in order (U0 → glossary) for dependency order and cross-reference integrity; a live agent-browser (0.27.0/CDP) session exercising all 3 gates, 14 ladder keys (plus a boundary miss, hint toggle, explain reveal), 14 unit-check items, 9 mastery items with confidence routing, all 8 widgets at their extrema (including W6 flatten/flip/stretch/degenerate cases), reset, corrupted-storage recovery, 320/640/1024px widths, reduced-motion emulation, and print export — with 0 console messages and 0 page errors throughout; plus the source notebook (31 cells) for the coverage matrix.

## Post-review remediation

**Revision 1 (2026-09-29, learner-reported).** The learner reported that a wrong-answer Check left the feedback line unstyled while the adjacent Hint rendered as a styled notice box. Investigation confirmed five inherited gaps (the v1 assembly incident dropped a group of stylesheet-tail rules and v1's repair restored only two of the lost rules): missing `.feedback.ok`/`.feedback.no` state rules (all 42 feedback regions affected), a missing base `.callout` rule (all 6 callout blocks rendered as plain prose; the `.callout.good`/`.callout.info` overrides were inert without it), a missing `.gloss-list` rule, an unapplied `class="mastery"` wrapper (the mastery-card rule was dead), and a missing `@media print` neutralization line. Remediation restored the four rule/wrapper gaps with text verbatim from the module's sibling lessons, added an amber `.feedback.note` refusal state (Class 1's `.fb.note` precedent; red now means only "wrong answer") with the eight refusal sites relabelled `no` → `note`, and added `✓`/`✗` `::before` glyphs on graded states (lesson standard §10.1; WCAG 1.4.1 non-color cue). Re-verification on the remediated bytes (`3c0bf64a…`): strict candidate verification 0 failures — its new state-styling check was first proven to fail against the pre-fix bytes; Python harness 118/118 and Node behavioral harness 48/48; live browser audit 27/27 computed-style assertions (feedback ok/no/note backgrounds and borders, both callout variants, mastery card, glossary margin) with 0 page errors and 0 console messages, confident-miss routing and completion-dot regressions intact, 320/1024px no horizontal overflow at 16.5px body font, reduced-motion honored on a fresh load, print export ≈1.9 MB. No score change: presentation was restored to the intended design system; no assessed behavior, number, or key changed, so the weighted result stands. Process fixes (QA checklist Audit 5/Audit 6 items; `verify-candidate.py` state-styling check; MEM-2026-0005 amendment) are recorded in the run ledger. The three in-generation corrections (nav-dot unit list; `fmt` negative-zero display; "6 units" header chip) were made before evaluation, each followed by a full re-verification chain on the new hash; the two earlier in-session builds were superseded before evaluation.

## Dimension scorecard

| Dimension | Score (0–4) | Evidence | Defects/severity | Recommended remedy | Confidence |
| --- | ---: | --- | --- | --- | --- |
| Educational quality (18%) | 4.0 | The EVAL-2026-0014 density observation is closed by the U5/U6 split with full unit anatomy in both units; 7 computational skills each get a 3-rung faded ladder; 3 commitment gates with differentiated feedback; 2 explain items; 9-item interleaved mastery with reasoning, transfer, and error-identification items; every forward promise pays off (preview table, steepest-ascent, λᵏ). | None | — | High |
| Factual/mathematical accuracy (18%) | 4.0 | 118/118 independent recomputation checks pass, including the new L5r2=9, L5r3=0, c5n=6, m9=12 and the W6 determinant cases; the source's wrong chain-rule formula ships corrected with a tag; W6's source-matrix claim checked against cell 23; no hard-coded widget outcomes (live computation only). | None | — | High |
| Source grounding (10%) | 4.0 | Full 31-cell coverage matrix with dispositions unchanged; all constructed additions labeled and bounded; provenance tags on new claims; the split maps to the source's PART 6 / PART 7 boundary. | None | — | High |
| Interactivity and agency (10%) | 4.0 | 8 widgets with learner-manipulable variables and written goals; W6's four-entry transformation lab with equal-scale panels and clipped rendering; causal live readouts everywhere; bounded inputs; extrema verified live; recovery via reset and corrupted-storage fallback. | None | — | High |
| Accessibility and inclusion (14%, hard gate) | 3.5 | 16.5px font floor at all breakpoints; every canvas pairs a live text readout and `aria-describedby`; legends on multi-entity canvases; keyboard-operable native controls; reduced-motion honored; print fallback; measured AA contrast. | Minor (judgment): W6's numeric readout substitutes for the shape for non-visual users; the concept map scrolls internally at 320px rather than scaling. Revision 1 (post-review) added the `✓`/`✗` non-color cue to graded states per §10.1 / WCAG 1.4.1. | Future human reviewer may move this ±0.5; consider a tabular fallback for W6 in a later iteration. | Medium |

| Visual clarity (8%) | 4.0 | Two-panel W6 renders with equal x/y scale and per-panel clipping (divider-zoom verified); W1 aspect reduced 21% with data and optimum visible; hierarchy, legends, and color-not-sole-encoder verified at three widths. | None after remediation (revision 1: unstyled feedback states and the missing base callout rule, found by learner report post-evaluation; fixed and re-verified — see Post-review remediation) | — | High |
| User experience (8%) | 4.0 | Orientation loop, sticky nav with 7 completion dots and active state, meta chips updated to 7 units, visible reset, storage fallback messaging, spacing invitation; corrupted-storage reload recovers cleanly. | None | — | High |
| Completeness (6%) | 4.0 | Every LP/XS element ships: 8 widgets, 3 gates, 7 ladders, 7 unit checks, 9 mastery items, 2 explain items, 15 formula blocks with symbol keys, 44-term glossary, 16-edge concept map, review list, colophon; spec conformance sweep element-by-element. | None | — | High |
| Readability (4%) | 4.0 | The densest unit was split along the source's own boundary; U2 remains deliberately dense (evaluator accepted in EVAL-2026-0014); terminology linked; jargon sweep retains 41 resolving term links. | None | — | High |
| Technical feasibility/performance intent (4%) | 4.0 | Single file, zero external requests, offline-capable; 7 resize listeners ≥ 7 canvases; bounded per-redraw workloads; `node --check` clean; stub-DOM execution of every draw function with zero exceptions; 0 browser console errors after full interaction. | None | — | High |

## Weighted result and gate check

Weights sum to 100%; with the evaluator's scores the unrounded weighted result is:

`(0.18·4.0) + (0.18·4.0) + (0.10·4.0) + (0.10·4.0) + (0.14·3.5) + (0.08·4.0) + (0.08·4.0) + (0.06·4.0) + (0.04·4.0) + (0.04·4.0) = 3.93`

Gate check against the default learner-release conditions (used diagnostically for a private pilot): hard-gate dimensions ≥ 3.5 — educational quality 4.0, factual/mathematical accuracy 4.0, source grounding 4.0, accessibility 3.5 → **met**; all other dimensions ≥ 3 — met; weighted score ≥ 3.5 — met (3.93); no score of 0–1 — met; no unassessed dimension — met; no unresolved critical defect — met; source status approved — met; complete lineage — met; **independent review — NOT met** (non-independent). Because the freedom-from-independent-review condition fails, a public `released` decision is unavailable regardless of the score; the candidate closes as `private-pilot-complete`. Post-review revision 1 (see above) restores intended presentation only; no assessed behavior, number, or key changed, so the weighted result and the gate check stand unchanged.

## Disagreement or uncertainty

No reviewer disagreement (single reviewer). Uncertainty is concentrated in two judgment-based calls the evaluator flags rather than hides: (a) the accessibility score's two Minor items reflect a judgment about whether a numeric readout fully substitutes for the W6 shape in non-visual use — a future human reviewer may reasonably move this dimension by ±0.5; (b) the readability improvement to 4.0 reflects the structural split as sufficient evidence while acknowledging U2's retained density — defensible either way at ±0.5.

## Non-negotiable blockers

None. (Public release remains blocked by the review-independence condition and by the Stage 1 pilot scope, not by any artifact defect.)

## Reviewer sign-off

Reviewed and closed by the repository maintainer as a non-independent Stage 1 private pilot; artifacts, audits, adversarial findings, and rendered evidence are recorded in [RUN-20260929-0001](../runs/run-20260929-0001-multivariate-calculus-v2.md). Public-release eligibility is `ineligible`, consistent with the non-independent review. Revision 1 (learner-reported state-styling restoration) was re-verified on the remediated hash `3c0bf64a…` and is recorded in the run ledger; this sign-off stands for the remediated candidate.

