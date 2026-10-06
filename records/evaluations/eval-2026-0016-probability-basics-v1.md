# EVAL-2026-0016: Candidate evaluation — probability basics v1

**Candidate ID/version:** CAN-2026-0015, `probability-basics-v1.html`, SHA-256 `fa438356badf5b0e40d3929d7ac8317cbaa2e6b6ba4d270e4121cc307991c35d`, 145,525 bytes (1,411 lines)  
**Rubric version:** [evaluation-framework.md](../../docs/06-evaluation/evaluation-framework.md) (Stage 1 anchors, WF-007) against [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) and the [depth-calibration contract](../../docs/01-product/depth-calibration-contract.md)  
**Evaluator role/identity:** Repository maintainer (solo Stage 1 operator), generator of the same candidate  
**Evaluation mode:** automated checks + agent-performed specialist review + stub-DOM behavioral execution (no live browser)  
**Operating scope:** Stage 1 private pilot  
**Review independence:** non-independent  
**Reviewer relationship or limitation:** the evaluator generated the candidate in the same session; no second reviewer participated; all dimension scores are evidence-anchored and reproducible from the run ledger  
**Public-release eligibility:** ineligible  
**Confidence:** high  
**Recommendation:** private-pilot-complete  
**Iterations reviewed:** builds = 1 (`fa438356…`); revision cycles = 0 (3 in-generation corrections itemized in [RUN-20261006-0001](../runs/run-20261006-0001-probability-basics-v1.md); per [ADR-0006](../../docs/adr/0006-record-iteration-accounting.md))

## Scope and evidence inspected

The artifact at the hash above; `scripts/verify-candidate.py --strict` (0 failures; 9 canvases, 6 ladders, 3 gates, 19 formula blocks, 41 glossary entries, 10 per-element slider-track encapsulations, font floor ≥16px, option stacks, callout discipline, state-styling); an independent Python recomputation harness (60+ numeric values + MCQ/gate/mastery answer-key cross-check; 0 failures); `node --check`; a Node stub-DOM execution of all nine draw functions at defaults (0 exceptions); the assembled body read in order (U0 → glossary) for dependency order and cross-reference integrity; and the source notebook (61 cells) for the coverage matrix. Live rendered verification (Audit 6) was **not** performed — degraded mode.

## Coverage matrix (all 61 cells dispositioned)

| Source cells | Content | Disposition |
|---|---|---|
| 1–2 | Title; agenda (incl. core outcomes in cell 5) | Orientation U0 |
| 3–5 | Probability as uncertainty; LLM/fraud/recsys examples; outcomes | U1 (ML LINK) |
| 6–11 | Random variables; X:Ω→ℝ (opaque fig. cell 8); dice; rainfall | U1 (figure recovered) |
| 12–13 | Discrete vs continuous; P(X=x)=0; P(a≤X≤b) | U1 |
| 14–19 | Distributions; PMF; dice 1/6; PMF properties (opaque fig. cell 19) | U2 (figure recovered) |
| 20–21 | PDF; area = probability; f(x)≠P(X=x); uniform U(0,1) | U3 |
| 22–26 | CDF; F(x)=P(X≤x); U(0,1) F=x; properties (cell-26 typo) | U4 (typo corrected) |
| 27–33 | PDF↔CDF (opaque figs. 29/31); fundamental theorem; f=2x→F=x² | U5 (figures recovered) |
| 34–39 | Geometric reading; discrete CDF; dice F(3)=1/2; PMF recovery | U5 |
| 40–46 | Expectation; dice 3.5; E[X]=2/3; linearity/constant/sum; ML uses | U6 |
| 47–51 | Variance two ways; dice ≈2.92; σ; bias–variance | U7 |
| 52–55 | Covariance; interpretation; Cov=0 ≠ independence; Y=X²; correlation | U8 |
| 56–61 | PCA (opaque fig. 58); eigenvectors = principal components; Gaussian; multivariate | U9 (figure recovered) |

No silent drops. Corrections (all tagged in the artifact): cell-26 CDF upper limit 0→1; broken LaTeX splits re-emitted.

## Dimension scorecard

| Dimension | Score (0–4) | Evidence | Defects/severity | Recommended remedy | Confidence |
| --- | ---: | --- | --- | --- | --- |
| Educational quality (18%) | 4.0 | Nine units with ledes, intuition-first prose, worked numbers, and constructed-response checks; L1–L6 full 3-rung ladders; 3 gates; 11-item interleaved mastery (reasoning + transfer M9 + error-identification M10); 2 explain items with model answers; the CDF↔PDF arc seeded in U1–U4 and paid off in U5. | None | — | High |
| Factual/mathematical accuracy (18%) | 4.0 | Independent Python harness recomputed 60+ values and all keys (0 failures); source typo corrected and tagged; f(x)=2x, F=x², E[X]=2/3, Var≈2.92, Corr=6/(2·3)=1, eigenvalues 3,1 all verified; no unsupported claims. | None | — | High |
| Source grounding (10%) | 4.0 | Complete 61-cell coverage matrix; five opaque figures recovered as live/plain content; corrections tagged; provenance tags (source/constructed/supplemental) throughout. | None | — | High |
| Interactivity and agency (10%) | 4.0 | 9 goal-directed manipulable canvases (each slider-bounded, each with a same-numbers readout and legend); live computation only; gates hide the widget until commitment; storage-backed review list with reset and fallback. | None | — | High |
| Accessibility and inclusion (14%) | 3.5 | Semantic landmarks, heading order, aria-live readouts, keyboard-operable native controls, per-canvas text equivalents, colour never sole encoder, reduced-motion and print styles, 16px floor, no drag-only interaction. Two Minor items: a numeric readout substitutes for the W8/W9 cloud shape in non-visual use; a future human reviewer may move this ±0.5. | 2 Minor | Consider an aria-described summary of the cloud's tilt | Medium |
| Visual clarity (8%) | 2.5 | **Degraded-mode cap** (no live browser): encodings are accurate by construction (area = probability, running-total curve, two-panel area↔height, ellipse + axes) with legends and colour-plus-label; not confirmed on a rendered surface at 320/640/1024px. | Not rendered | Perform Audit 6 live | Low |
| User experience (8%) | 2.5 | **Degraded-mode cap** (no live browser): orientation loop, sticky nav with active state and completion dots, meta chips, visible reset, storage fallback messaging; not confirmed on a rendered surface. | Not rendered | Perform Audit 6 live | Low |
| Completeness (6%) | 4.0 | Every LP/XS element ships: 9 widgets, 3 gates, 6 ladders, 9 checks, 11 mastery items, 2 explain items, 19 formula blocks with symbol keys, 41-term glossary, 16-edge concept map, review list, colophon; spec conformance swept element-by-element. | None | — | High |
| Readability (4%) | 4.0 | One metaphor (budget of 1.0) throughout; jargon defined on first use and linked; misconception traps in prose; tables and formula keys aid scanning. | None | — | High |
| Technical feasibility/performance intent (4%) | 2.5 | **Degraded-mode cap** (no live browser): single file, zero external requests, offline-capable; 9 resize listeners = 9 canvases; bounded redraw workloads; `node --check` clean; stub-DOM draw execution 0 exceptions; but console/network/perf not captured live. | Not rendered | Perform Audit 6 live | Low |

## Weighted result and gate check

Weights sum to 100%; with the evaluator's scores the unrounded weighted result is:

`(0.18·4.0) + (0.18·4.0) + (0.10·4.0) + (0.10·4.0) + (0.14·3.5) + (0.08·2.5) + (0.08·2.5) + (0.06·4.0) + (0.04·4.0) + (0.04·2.5) = 3.63`

Gate check against the default learner-release conditions (used diagnostically for a private pilot): hard-gate dimensions ≥ 3.5 — educational quality 4.0, factual/mathematical accuracy 4.0, source grounding 4.0, accessibility 3.5 → **met**; weighted score ≥ 3.5 — met (3.63); no score of 0–1 — met; no unassessed dimension — met; no unresolved critical defect — met; source status approved — met; complete lineage — met. Three non-hard-gate dimensions (visual, UX, technical) sit at 2.5 **solely because of the degraded-mode cap** (no live browser), not from artifact defects; the other dimensions ≥ 3 condition is therefore not met on the rendered-evidence path. Independently, **independent review — NOT met** (non-independent). Because freedom-from-independent-review fails, a public `released` decision is unavailable regardless of the score; the candidate closes as `private-pilot-complete`.

## Disagreement or uncertainty

No reviewer disagreement (single reviewer). Uncertainty is concentrated in the degraded-mode caps: once Audit 6 runs live, the visual/UX/technical dimensions are expected to rise toward 4.0 (the construction is verified), moving the weighted result to roughly 3.83. The accessibility Minor items are judgment calls a human reviewer may move ±0.5.

## Non-negotiable blockers

None. (Public release remains blocked by the review-independence condition and the Stage 1 pilot scope; live rendered verification remains an open verification step, not an artifact defect.)

## Reviewer sign-off

Reviewed and closed by the repository maintainer as a non-independent Stage 1 private pilot; artifacts, audits, adversarial findings, and execution evidence are recorded in [RUN-20261006-0001](../runs/run-20261006-0001-probability-basics-v1.md). Public-release eligibility is `ineligible`, consistent with the non-independent review. Live rendered verification (ADR-0010) is recorded as deferred (degraded mode); when performed it will be appended as a dated re-verification note.
