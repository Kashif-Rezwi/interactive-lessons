# EVAL-2026-0014: Candidate evaluation — multivariate calculus v1

**Candidate ID/version:** CAN-2026-0013, `multivariate-calculus-v1.html`, SHA-256 `5363d7d535bba16ea7401a035b0d8b7666833a2600515fe1cc0286416e449f81`, 157,620 bytes  
**Rubric version:** [evaluation-framework.md](../../docs/06-evaluation/evaluation-framework.md) (Stage 1 anchors, WF-007) against [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) and the [depth-calibration contract](../../docs/01-product/depth-calibration-contract.md)  
**Evaluator role/identity:** Repository maintainer (solo Stage 1 operator), generator of the same candidate  
**Evaluation mode:** automated checks + agent-performed specialist review + rendered browser execution  
**Operating scope:** Stage 1 private pilot  
**Review independence:** non-independent  
**Reviewer relationship or limitation:** the evaluator generated the candidate in the same session; no second reviewer participated; all dimension scores are nevertheless evidence-anchored and reproducible from the run ledger  
**Public-release eligibility:** ineligible  
**Confidence:** high  
**Recommendation:** private-pilot-complete  
**Iterations reviewed:** builds = 1 (CAN-2026-0013, `5363d7d5…`); revision cycles = 0 (per [ADR-0006](../../docs/adr/0006-record-iteration-accounting.md); 16 in-generation corrections enumerated in [RUN-20260924-0001](../runs/run-20260924-0001-multivariate-calculus-v1.md) §Revision history)

## Scope and evidence inspected

The final artifact at the hash above; `scripts/verify-candidate.py` strict run; the 47-check independent Python recomputation harness; `node --check` and Node execution of the page's extracted script; the assembled body read in order (U0 → glossary); a live agent-browser (0.27.0/CDP) session exercising all 3 gates, 12 ladder rungs, 6 unit checks, 8 mastery items, 2 explain items, 6 widgets at their extrema, reset, corrupted-storage recovery, four viewport widths, reduced-motion emulation, and print export; plus the source notebook (31 cells) for coverage.

## Dimension scorecard

| Dimension | Score (0–4) | Evidence | Defects/severity | Recommended remedy | Confidence |
| --- | ---: | --- | --- | --- | --- |
| Educational quality (18%) | 4.0 | Six units in full canonical anatomy; six 3-rung faded ladders; three commitment gates with differentiated feedback; two explain-in-own-words items with model answers; 8-item interleaved mastery (6+2) with reasoning, transfer (3-D directional derivative, R⁴→R⁷ Jacobian shape), and one error-identification item, plus 3-level confidence and review routing (traced live). Reveal arcs verified realized: cell-12 steepest-ascent promise proven in U3 via the cos φ bound; flat perpendicular → U6 plateaus; U1 hand-tuning payoff → U2 descent lab and the live optimum MSE = 0.22. | None | — | High |
| Factual/mathematical accuracy (18%) | 4.0 | 47/47 independent recomputations pass (prose numbers, 12 ladder keys, 6 check keys, 3 numeric mastery keys, 11 MCQ/gate letters, tolerance cross-checks); every displayed value computed live in the page (verified in-browser at defaults and extrema); the source's wrong chain-rule formula corrected and tagged; source imprecisions (Hessian direction-dependence, Newton invertibility) stated as transparency additions rather than silent quieting. | None | — | High |
| Source grounding (10%) | 4.0 | All 31 cells dispositioned (coverage matrix in RUN-20260924-0001); three corrections tagged (`source (formula corrected)`, `source (direction-dependence tightened)`, `source (guard added, supplemental)`); two opaque base64 figures replaced by live labeled visuals and recorded as replacements, not copies; every FOUNDATION bridge labeled; the source's PART 9/10 numbering inconsistency recorded. | None | — | High |
| Interactivity and agency (10%) | 4.0 | Six goal-strip widgets, all values live; canvases bounded and extrema-forced with no off-canvas or thrown states; gates hide the manipulable until commitment and stay locked on refusal; hints are learner-opened; reset clears state; corrupted localStorage recovers gracefully; every interaction has a text readout carrying the same numbers. | None | — | High |
| Accessibility and inclusion (14%) | 3.5 | Semantic landmarks, logical headings, `aria-live` readouts, native keyboard-operable controls, canvas text equivalents, `.legend-inline` legends with labels (colour never the sole encoder), `prefers-reduced-motion` honored (`scroll-behavior: auto`), print stylesheet hides controls and exposes content, 16.5px body font at all four tested widths, no horizontal overflow at 320px. | Minor: the nav is a horizontally scrollable one-line strip on narrow screens (sanctioned by the standard, but a mild friction); canvas *shapes* are conveyed numerically by readouts rather than by a non-visual structural description. | Consider a stacked nav variant below ~420px in a future iteration; optionally add a short structural sentence to each canvas's accessible description. | High |
| Visual clarity (8%) | 3.5 | Consistent design tokens, per-widget viewports, legends matching drawn colours after the legend-colour correction, error-squares visual on the loss explorer, contour/arrow/projection-bar grammar shared across U2–U4, two-panel cross-sections in U5. | Minor: the U5 cross-section panels draw normalised amplitudes (a schematic bend picture) while the exact curvatures live in the readout; the schematic nature is implicit rather than stated on the canvas. | Add a one-line "amplitude is schematic; values in the readout" note to the U5 canvas description in a future iteration. | High |
| User experience (8%) | 4.0 | Orientation unit with loop table and label legend; sticky nav with completion dots and active state; meta chips; every unit ends in Connect; review list with spacing invitation; visible reset; storage-fallback message; no page-level horizontal scroll at any tested width; print and reduced-motion paths behave. | Minor observation: the U1 canvas is tall (~813px at 1280px width), adding scroll before the ladder. | Optionally reduce the W1 y-window in a future iteration. | High |
| Completeness (6%) | 4.0 | Every LP/XS-declared element ships: 7 widgets (5 canvases + 1 numeric lab with stated reason + 1 loss explorer), 15 formula blocks with per-symbol keys, 44-term registry with 44 glossary entries shipped, 3 gates, 6 ladders, 2 explain items, 8 mastery items, concept map, review list, colophon. The XS was re-pinned to the shipped artifact after the two boundary-level refinements. | None | — | High |
| Readability (4%) | 3.5 | Consistent voice, plain-language symbol keys, terms linked to a six-field glossary, a jargon sweep removed five undefined usages, layered badges (`CLASS CORE`/`FOUNDATION`/`DEEP DIVE`/`ML LINK`/`EXTENSION`) and provenance tags. | Minor: density is high in U2 and U5, and the full run takes 60–80 minutes. | Consider splitting U5's Jacobian and Hessian into two shorter units in a future major iteration. | High |
| Technical feasibility/performance intent (4%) | 4.0 | Single file, zero external requests, offline-capable; all widget math closed-form with bounded workloads (14 descent steps; 4 level curves; ≤60-point curves); `makeView` clientWidth/DPR pattern with 6 resize listeners = 6 canvases; storage guarded with try/catch and reset; `node --check` clean; 0 browser errors after full interaction. | None | — | High |

## Weighted result and gate check

Weights sum to 100%; with the evaluator's scores the unrounded weighted result is:

`(0.18·4.0) + (0.18·4.0) + (0.10·4.0) + (0.10·4.0) + (0.14·3.5) + (0.08·3.5) + (0.08·4.0) + (0.06·4.0) + (0.04·3.5) + (0.04·4.0) = 3.87`

Gate check against the default learner-release conditions (used diagnostically for a private pilot): hard-gate dimensions ≥ 3.5 — educational quality 4.0, factual/mathematical accuracy 4.0, source grounding 4.0, accessibility 3.5 → **met**; all other dimensions ≥ 3 — met; weighted score ≥ 3.5 — met (3.87); no score of 0–1 — met; no unassessed dimension — met; no unresolved critical defect — met; source status approved — met; complete lineage — met; **independent review — NOT met** (non-independent). Because the freedom-from-independent-review condition fails, a public `released` decision is unavailable regardless of the score; the candidate closes as `private-pilot-complete`.

## Disagreement or uncertainty

No reviewer disagreement (single reviewer). Uncertainty is concentrated in two judgment-based judgments the evaluator flags rather than hides: (a) the accessibility score's two Minor items reflect a *judgment* about whether a numeric readout fully substitutes for a shape in non-visual use — a future human reviewer may reasonably move this dimension by ±0.5; (b) the readability score reflects a judgment that density in U2/U5 is acceptable at this learner level, where the standard's depth bar argues for keeping the gradient and gradient-descent material adjacent.

## Non-negotiable blockers

None. (Public release remains blocked by the review-independence condition and by the Stage 1 pilot scope, not by any artifact defect.)

## Reviewer sign-off

Reviewed and closed by the repository maintainer as a non-independent Stage 1 private pilot; artifacts, audits, adversarial findings, and rendered evidence are recorded in [RUN-20260924-0001](../runs/run-20260924-0001-multivariate-calculus-v1.md). Public-release eligibility is `ineligible`, consistent with the non-independent review.
