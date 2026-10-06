# EVAL-2026-0017: Candidate evaluation — probability basics v2

**Candidate ID/version:** CAN-2026-0016, `probability-basics-v2.html`, SHA-256 `c37befb55ae2703126b8c5e4c30f257e6816db9b444dc197a2326cc20f458b69`, 166,370 bytes (1,621 lines)
**Rubric version:** [evaluation-framework.md](../../docs/06-evaluation/evaluation-framework.md) (Stage 1 anchors, WF-007) against [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) and the [depth-calibration contract](../../docs/01-product/depth-calibration-contract.md)
**Evaluator role/identity:** Repository maintainer (solo Stage 1 operator), generator of the same candidate
**Evaluation mode:** automated checks + agent-performed specialist review + stub-DOM behavioral execution + live headless-browser rendering
**Operating scope:** Stage 1 private pilot
**Review independence:** non-independent
**Reviewer relationship or limitation:** the evaluator generated the candidate in the same session; no second reviewer participated; all dimension scores are evidence-anchored and reproducible from the run ledger
**Public-release eligibility:** ineligible
**Confidence:** high
**Recommendation:** private-pilot-complete
**Iterations reviewed:** builds = 1 (`c37befb5…`); revision cycles = 0 (3 in-generation corrections itemized in [RUN-20261006-0002](../runs/run-20261006-0002-probability-basics-v2.md); per [ADR-0006](../../docs/adr/0006-record-iteration-accounting.md))

## Scope and evidence inspected

The artifact at the hash above; `scripts/verify-candidate.py --strict` (0 failures; 12 canvases, 8 ladders, 3 gates, 19 formula blocks, 44 glossary entries, 15 per-element slider-track encapsulations, font floor ≥16px, option stacks, callout discipline, state-styling, canonical skeleton); an independent Python recomputation harness (all numeric values + MCQ/gate/mastery answer-key cross-check, including the new L7/L8/M12 keys; 0 failures); `node --check`; a Node stub-DOM execution of all twelve draw functions at defaults (0 exceptions); live headless-Google-Chrome rendering (0 page console errors; `r10`/`r11`/`r12` populated in the dumped DOM; screenshots at 320/640/1024px, with a clean full-layout render confirmed at 500px); the assembled body read in order (U0 → glossary) for dependency order and cross-reference integrity; and the source notebook (61 cells) for the coverage matrix.

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
| 27–33 | PDF↔CDF (opaque figs. 29/31); fundamental theorem; f=2x→F=x² | U5 (figures recovered; **two-point form now live via W10**) |
| 34–39 | Geometric reading; discrete CDF; dice F(3)=1/2; PMF recovery | U5 (**PMF recovery now live via W11**) |
| 40–46 | Expectation; dice 3.5; E[X]=2/3; linearity/constant/sum; ML uses | U6 (**continuous ladder L7 added**) |
| 47–51 | Variance two ways; dice ≈2.92; σ; bias–variance | U7 (**continuous ladder L8 + second-moment term added**) |
| 52–55 | Covariance; interpretation; Cov=0 ≠ independence; Y=X²; correlation | U8 |
| 56–61 | PCA (opaque fig. 58); eigenvectors = principal components; Gaussian; multivariate | U9 (figure recovered; **Gaussian shape now live via W12**) |

No silent drops. Corrections (all tagged in the artifact): cell-26 CDF upper limit 0→1; broken LaTeX splits re-emitted.

## Dimension scorecard

| Dimension | Weight | Score | Evidence | Defects/severity | Confidence |
|---|---:|---:|---|---|---|
| Educational quality | 18% | 4.0 | 9 units, full canonical anatomy; 8 faded ladders (added continuous L7/L8); 13-item confidence-tagged mastery (added M12 transfer, M13 reasoning); 2 explain-in-own-words items; per-unit ledes and named reveal arcs (LP-2026-0015). | none | high |
| Factual/mathematical accuracy | 18% | 4.0 | Independent recomputation of every value including new keys: L7 (0.667/0.5/0.75), L8 (0.083/0.083/0.0375), M12 (0.4015), W12 peak 1/(σ√(2π)); all formulas correct; cell-26 typo corrected and flagged. | none | high |
| Source grounding | 10% | 4.0 | All 61 cells dispositioned (matrix above); 41 CM claims anchored; three (v2) claims each mapped to a live element; provenance header traces CAN/RUN/SRC/CM/LP/XS. | none | high |
| Interactivity and agency | 10% | 4.0 | 12 live canvases (added W10 two-point, W11 staircase, W12 bell); 3 commitment gates; every readout computed live; slider/resize wiring verified in-browser. | none | high |
| Accessibility and inclusion | 14% | 3.5 | Semantic landmarks, native controls, aria-live readouts, 12 per-canvas text equivalents, inline legends, reduced-motion + print fallbacks, 16.5px floor; no drag-only interaction. | no screen-reader specialist pass; true 320px emulation not exercised (Minor) | medium |
| Visual clarity | 8% | 3.5 | Live-rendered at 500/640/1024px; standard tokens; color legends; correct encodings; canvases bounded by declared viewports. | W12 short-and-wide aspect (matches module convention; Minor) | medium |
| User experience | 8% | 3.0 | Clear nav with completion dots; functional per-option feedback; reset; graceful storage fallback; rendered at 500/640/1024px. | true 320px mobile breakpoint unverified in the headless harness (Minor) | medium |
| Completeness | 6% | 4.0 | All §1.1 elements present; 45-term glossary with 6 fields each; branched concept map; mastery = units + 4. | none | high |
| Readability | 4% | 4.0 | Audience-fit prose; jargon defined at first mention; per-symbol formula keys. | none | high |
| Technical feasibility/performance intent | 4% | 3.5 | Clean syntax; zero external requests; stub-DOM handlers pass; live render 0 console errors; responsive listeners present. | no automated 320px breakpoint assertion (Minor) | medium |

## Weighted result and gate check

`sum(score × weight)/100 = (18·4.0 + 18·4.0 + 10·4.0 + 10·4.0 + 14·3.5 + 8·3.5 + 8·3.0 + 6·4.0 + 4·4.0 + 4·3.5)/100 = (72 + 72 + 40 + 40 + 49 + 28 + 24 + 24 + 16 + 14)/100 = 379/100 = **3.79**`.

Gate check against the default learner-release conditions (used diagnostically for a private pilot): hard-gate dimensions ≥ 3.5 — educational quality 4.0, factual/mathematical accuracy 4.0, source grounding 4.0, accessibility 3.5 → **met**; weighted score ≥ 3.5 — met (3.79); no score of 0–1 — met; no unassessed dimension — met; no unresolved critical defect — met; source status approved — met; complete lineage — met. The other-dimensions ≥ 3 condition is met (interactivity 4.0, visual 3.5, UX 3.0, completeness 4.0, readability 4.0, technical 3.5). Independently, **independent review — NOT met** (non-independent). Because freedom-from-independent-review fails, a public `released` decision is unavailable regardless of the score; the candidate closes as `private-pilot-complete`. This is a **+0.16 improvement** over v1 (EVAL-2026-0016, 3.63): v1 was capped by degraded-mode Audit 6 (visual/UX/technical at 2.5), whereas v2 was rendered live (visual 3.5, technical 3.5, UX 3.0).

## Disagreement or uncertainty

No reviewer disagreement (single reviewer). Uncertainty is concentrated in two places: (1) the true 320px mobile breakpoint was not exercised (headless Chrome without device-metrics emulation enforced a minimum layout width; the 320px capture matched the v1 baseline exactly), so UX/technical sit at 3.0/3.5 rather than higher — a device-emulation pass is expected to lift them; (2) the accessibility Minor items are judgment calls a human reviewer may move ±0.5.

## Non-negotiable blockers

None. (Public release remains blocked by the review-independence condition and the Stage 1 pilot scope; the true 320px mobile-emulation check remains an open verification step, not an artifact defect.)

## Reviewer sign-off

Reviewed and closed by the repository maintainer as a non-independent Stage 1 private pilot; artifacts, audits, adversarial findings, and execution evidence are recorded in [RUN-20261006-0002](../runs/run-20261006-0002-probability-basics-v2.md). Public-release eligibility is `ineligible`, consistent with the non-independent review. Rendered verification (ADR-0010) was performed live at 500/640/1024px with 0 console errors; the true 320px mobile-emulation pass is recorded as deferred.
