# LP-2026-0015: Learning plan for probability basics for machine learning v2

**Status:** Reviewed
**Supersedes / iteration position:** Iteration 2 — deepens [LP-2026-0014](lp-2026-0014-probability-basics.md) (v2 superset: same nine units and source, plus two continuous-moment ladders L7/L8, three new labs W10–W12, and a 13-item mastery)
**Owner:** Repository maintainer
**Concept model:** [CM-2026-0014](../concepts/cm-2026-0014-probability-basics.md)
**Target learner and prerequisites:** AIML-4 learner post-Classes 1–2; comfortable with summation Σ, slope, the idea of accumulated area, and the Class 2 eigenvector one-liner; no prior probability.
**Source and claim links:** [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md); claims CM-2026-0014 #1–41

## Measurable learning outcomes

1. Explain why ML is probabilistic and name three concrete ML probability uses (LLM tokens, fraud, recommendation).
2. Define a random variable and classify a given variable as discrete or continuous.
3. State and use the PMF: compute P(X=x) for a discrete distribution and verify 0 ≤ P ≤ 1 and ΣP = 1.
4. State and use the PDF: read probability as area under the curve and explain why f(x) is not P(X=x) and P(X=x)=0.
5. State and use the CDF: compute F(x)=P(X ≤ x) and list its four properties.
6. Convert between PDF and CDF both ways (integrate and differentiate) and apply the fundamental theorem P(a ≤ X ≤ b)=F(b)−F(a) **at two points, not only from −∞**.
7. Recover a discrete PMF from its CDF as the jump F(x)−F(x⁻).
8. Compute expectation for discrete and continuous variables and apply linearity, E[c]=c, and the sum rule.
9. Compute variance two ways (E[(X−μ)²] and E[X²]−(E[X])²) for discrete **and continuous** variables, using the second moment, and interpret the standard deviation.
10. Compute covariance and correlation and explain why zero covariance does not imply independence.
11. Connect these to PCA (covariance matrix → eigenvectors) and Gaussian models (mean + variance; the 68–95 rule; multivariate adds covariance).

## Sequence and rationale

U0 Orientation → U1 Probability & random variables (cells 3–13) → U2 PMF (cells 14–19) → U3 PDF (cells 20–21) → U4 CDF (cells 22–26) → U5 CDF ↔ PDF conversion (cells 27–39, signature; deepened with the two-point and PMF-recovery labs) → U6 Expectation (cells 40–46; deepened with a continuous ladder) → U7 Variance (cells 47–51; deepened with a continuous ladder) → U8 Covariance & correlation (cells 52–55) → U9 ML connections (cells 56–61; deepened with the Gaussian lab) → synthesis + mastery (13 items) → review list → glossary.

Rationale: the source presents PMF → PDF → CDF → conversion, but explain-before-use requires the *distribution* concept and the *discrete/continuous* split to land first (U1), and the conversion unit (U5) to follow only after PMF, PDF, and CDF are taught, so the "CDF is the area under the PDF" reveal has all its pieces. The v2 deepening extends U5 with the two-point (interval) form and the discrete PMF-recovery staircase, adds continuous-expectation and continuous-variance ladders to U6/U7 (the source gives E[X]=2/3 for f=2x but no continuous variance), and adds the Gaussian shape lab to U9. The source's own ordering defects are repaired: the PMF-properties figure (cell 19) is stated in prose in U2, and the CDF upper-limit typo (cell 26) is corrected in U4.

## Teaching strategy and cognitive-load choices

One metaphor throughout: *probability is a budget of 1.0 that gets shared out over the possible values — the PMF/PDF says how it is shared, the CDF says how much has been spent by x.* Depth pass per unit:

| Unit | Lede | Signature visual (P-14) | Reveal arcs (P-15) | Misconception callout (≤1/unit) | Skills → ladders |
|---|---|---|---|---|---|
| U0 | Learn how the page teaches before the probability starts. | Branched concept map (SVG, 13 nodes / 16 edges) | — | — | — |
| U1 | Probability is the budget of 1.0; a random variable labels each outcome with a number. | `rv-lab` (W1): fair n-sided die PMF bars; slider n (2–12) | Seed the "distribution" idea → paid off in U2; seed discrete vs continuous → paid off in U3 | "A random variable is the outcome itself" | — |
| U2 | The PMF hands out the budget in lumps at exact values. | `pmf-lab` (W2): PMF bars with cumulative shading; slider k | PMF properties recovered from the cell-19 figure | "The masses don't have to sum to 1" | L1 (PMF arithmetic) |
| U3 | The PDF is a density; only its area is probability. | `pdf-lab` (W3): f(x)=2x with a shaded slice; sliders a, b (gated by G1) | Seed "area = probability" → paid off in U5 | "f(0.5)=2 means a 200% chance" | L2 (area under a PDF) |
| U4 | The CDF is a running total. | `cdf-lab` (W4): F(x)=x² with a marker at (x, F(x)); slider x | Seed "running total" → paid off in U5 | "F(x) is the probability that X equals x" | — |
| U5 | The CDF is the area; the PDF is the slope — at two points, not just from −∞. | `convert-lab` (W5, signature) + `convert2-lab` (W10, two-point) + `pmfrecover-lab` (W11, discrete staircase) | Closes the area↔height arc; pays off U3/U4 | "To get the PDF you integrate" (reversed) | L3 (PDF↔CDF conversion) |
| U6 | Expectation is the balance point of the budget. | `expect-lab` (W6): balance point of a uniform die; slider n | — | "3.5 is impossible on a die" | L4 (discrete expectation), **L7 (continuous expectation)** |
| U7 | Variance is the spread around the balance point. | `variance-lab` (W7): same mean, growing spread; slider s (gated by G3) | — | "Variance is the spread in X's units" | L5 (discrete variance), **L8 (continuous variance)** |
| U8 | Covariance asks whether two budgets move together. | `covariance-lab` (W8): tilting point cloud; slider ρ | Seed "linear dependence" → paid off in U9 | "Cov = 0 means independent" | L6 (covariance & correlation) |
| U9 | Where probability runs in real ML. | `pca-lab` (W9): covariance ellipse + principal axes; **`gaussian-lab` (W12): mean/width bell** | Closes the covariance→PCA arc and the mean/variance→Gaussian arc | "A Gaussian is just its mean" | (none new; connects) |

Prediction gates: G1 (U3 — "is f(x) the probability of x?"), G2 (U5 — "area vs height"), G3 (U7 — "does variance change units?"). Each hides its widget until commitment and gives option-specific feedback.

Explain-in-own-words items (≥2): **E1** (U5) "why is the CDF the integral of the PDF and the PDF its derivative?" and **E2** (U7) "what does variance measure, and why do we also want the standard deviation?" — both with model-answer reveals and honest self-evaluation, inside the unit Check blocks.

Additional-knowledge triage: **must-add bridges** — summation/integral as accumulation (Class 1), the eigenvector one-liner (Class 2), the uniform density f=1, and the toy pdf f(x)=2x. **should-add (v2)** — the two-point (interval) form of the fundamental theorem and the second-moment identity, both stated in the source and now given worked, live treatment. **could-add (v2)** — the 68–95 rule for the Gaussian (the source mentions 0.68/0.95). **do-not-add** — measure theory, Bayes, MLE, multivariate Gaussian algebra, named families beyond uniform/Gaussian.

Calibration: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) is the depth exemplar; implementation reference is the nearest governed sibling artifact `multivariate-calculus-v2.html` (CAN-2026-0014).

## Assessment and evidence of learning

Every unit check has ≥1 constructed-response numeric item plus ≥1 diagnostic MCQ with per-option feedback — checks c1–c9: random-variable type (c1), PMF sum/arithmetic (c2), area under a PDF (c3), CDF value and properties (c4), PDF↔CDF conversion (c5), expectation (c6), variance two ways (c7), covariance/correlation (c8), ML-connection reasoning (c9). Ladders L1–L8, three rungs each (worked → completion → independent), tiered never-auto-opening hints. Persistence: cleared checks fill nav dots; misses and confident mastery misses enter the `prob2-*` localStorage review list with a spacing invitation and visible reset; graceful fallback when storage is unavailable; corrupted-storage recovery.

Mastery: **13 items** (9 content units + 4), interleaved, 3-level confidence tags (`sure`/`think so`/`guessing`), confident misses routed to the review list. Includes reasoning, transfer (situations not seen in the lesson), and error-identification items; no worked numbers reused.

## Accessibility and inclusion intent

Semantic landmarks, logical heading order, native controls, keyboard operability, aria-live readouts, per-canvas text equivalents (all 12 canvases), colour never the sole encoder, reduced motion, print fallback, focus rings, a 16px body floor, and no drag-only interaction. Every canvas has an inline legend and a same-numbers readout.

## Acceptance criteria and review boundary

Strict mechanical verification (`verify-candidate.py`, 0 failures); independent Python recomputation (numbers, keys); Node behavioral harness (gates, ladders, checks, mastery, reset); dependency-order read-through; six audits + adversarial gate ([ADR-0009](../../docs/adr/0009-forced-adversarial-re-examination-gate.md)); rendered verification at 500/640/1024px with 0 console errors ([ADR-0010](../../docs/adr/0010-rendered-output-verification.md)) or a recorded limitation note; repository checker exit 0. Disposition `private-pilot-complete`; non-independent; release-ineligible.

## Conformance checklist (depth-calibration contract)

Before approval, verify against [depth-calibration-contract.md](../../docs/01-product/depth-calibration-contract.md):
- [x] Active benchmark ([BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md)) cited as calibration exemplar
- [x] Depth-pass table complete for every unit (lede, signature visual, reveal arcs with payoff units, misconception callouts, ladders)
- [x] One full 3-rung faded ladder for each computational skill (L1–L8)
- [x] ≥2 explain-in-own-words items with model-answer reveals allocated (U5, U7)
- [x] Every forward promise / reveal arc names its explicit payoff unit
