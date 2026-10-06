# LP-2026-0014: Learning plan for probability basics for machine learning v1

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 1 — original  
**Owner:** Repository maintainer  
**Concept model:** [CM-2026-0013](../concepts/cm-2026-0013-probability-basics.md)  
**Target learner and prerequisites:** AIML-4 learner post-Classes 1–2; comfortable with summation Σ, slope, the idea of accumulated area, and the Class 2 eigenvector one-liner; no prior probability.  
**Source and claim links:** [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md); claims CM-2026-0013 #1–60

## Measurable learning outcomes

1. Explain why ML is probabilistic and name three concrete ML probability uses (LLM tokens, fraud, recommendation).
2. Define a random variable and classify a given variable as discrete or continuous.
3. State and use the PMF: compute P(X=x) for a discrete distribution and verify 0 ≤ P ≤ 1 and ΣP = 1.
4. State and use the PDF: read probability as area under the curve and explain why f(x) is not P(X=x) and P(X=x)=0.
5. State and use the CDF: compute F(x)=P(X ≤ x) and list its four properties.
6. Convert between PDF and CDF both ways (integrate and differentiate) and apply the fundamental theorem P(a ≤ X ≤ b)=F(b)−F(a).
7. Compute expectation for discrete and continuous variables and apply linearity, E[c]=c, and the sum rule.
8. Compute variance two ways (E[(X−μ)²] and E[X²]−(E[X])²) and interpret the standard deviation.
9. Compute covariance and correlation and explain why zero covariance does not imply independence.
10. Connect these to PCA (covariance matrix → eigenvectors) and Gaussian models (mean + variance, plus covariance when multivariate).

## Sequence and rationale

U0 Orientation → U1 Probability & random variables (cells 3–13) → U2 PMF (cells 14–19) → U3 PDF (cells 20–21) → U4 CDF (cells 22–26) → U5 CDF ↔ PDF conversion (cells 27–39, signature) → U6 Expectation (cells 40–46) → U7 Variance (cells 47–51) → U8 Covariance & correlation (cells 52–55) → U9 ML connections (cells 56–61) → synthesis + mastery (11 items) → review list → glossary.

Rationale: the source presents PMF → PDF → CDF → conversion, but explain-before-use requires the *distribution* concept and the *discrete/continuous* split to land first (U1), and the conversion unit (U5) to follow only after both PMF and PDF and CDF are taught, so the "CDF is the area under the PDF" reveal has all its pieces. Expectation (U6) precedes variance (U7) because the variance formula is written in terms of E[X]; covariance (U8) precedes PCA (U9) because the covariance matrix is PCA's input. The source's agenda order is otherwise preserved. The source's own ordering defects are repaired: the PMF-properties figure (cell 19) is stated in prose in U2, and the CDF upper-limit typo (cell 26) is corrected in U4.

## Teaching strategy and cognitive-load choices

One metaphor throughout: *probability is a budget of 1.0 that gets shared out over the possible values — the PMF/PDF says how it is shared, the CDF says how much has been spent by x.* Depth pass per unit:

| Unit | Lede | Signature visual (P-14) | Reveal arcs (P-15) | Misconception callout (≤1/unit) | Skills → ladders |
|---|---|---|---|---|---|
| U0 | Learn how the page teaches before the probability starts. | Branched concept map (SVG, 13 nodes / 16 edges) | — | — | — |
| U1 | Probability is the budget of 1.0; a random variable labels each outcome with a number. | `rv-lab` (W1): fair n-sided die PMF bars; slider n (2–12) | Seed the "distribution" idea → paid off in U2 (PMF); seed discrete vs continuous → paid off in U3 (PDF) | "A random variable is the outcome itself" | — |
| U2 | The PMF hands out the budget in lumps at exact values. | `pmf-lab` (W2): PMF bars with cumulative shading; slider k | PMF masses sum to 1 → paid off as the area/integral in U3/U5 | "The masses don't have to sum to 1" | L1 PMF arithmetic |
| U3 | The PDF is a density: only its area is probability, never its height. | `pdf-lab` (W3): f(x)=2x with shaded [a,b]; sliders a,b | "area = probability" → paid off in U5 (CDF is area) | "f(x) is the probability of x" | L2 area under a PDF |
| U4 | The CDF is a running total: how much budget is spent by x. | `cdf-lab` (W4): F(x)=x² curve; slider x | Running total → paid off in U5 (F is the integral) | "F(x) is the probability that X=x" | (shares L2 with U3) |
| U5 | The CDF is the integral of the PDF, and the PDF is the derivative of the CDF. | `convert-lab` (W5): two-panel PDF/CDF, slider x, area = height | U1–U4 seeds all paid off here; the signature "area = height" reveal | "Integrate one way, differentiate the other — reversed" | L3 PDF↔CDF conversion |
| U6 | Expectation is the balance point of the probability budget. | `expect-lab` (W6): f(x)=2x with the mean at 2/3 marked; slider shift | Balance-point image → paid off in U7 (spread around the mean) | "Expectation must be attainable" | L4 expectation |
| U7 | Variance is how spread out the budget is around its balance point. | `variance-lab` (W7): two distributions, same mean, spread slider | Spread-around-mean → paid off in U8 (covariance) | "Variance is in the same units as X" | L5 variance |
| U8 | Covariance asks whether two budgets move together. | `covariance-lab` (W8): point cloud with correlation slider; live Cov/ρ | Joint-movement → paid off in U9 (covariance matrix / PCA) | "Cov = 0 means independent" | L6 covariance & correlation |
| U9 | PCA reads the covariance matrix; Gaussians are mean + variance (+ covariance). | `pca-lab` (W9): point cloud with covariance ellipse and principal axes; slider ρ | Closes the covariance→PCA arc | "A Gaussian is just its mean" | (none new; connects) |

Prediction gates: G1 (U3 — "is f(x) the probability of x?"), G2 (U5 — "area vs height"), G3 (U7 — "does variance change units?"). Each hides its widget until commitment and gives option-specific feedback.

Explain-in-own-words items (≥2): **E1** (U5) "why is the CDF the integral of the PDF and the PDF its derivative?" and **E2** (U7) "what does variance measure, and why do we also want the standard deviation?" — both with model-answer reveals and honest self-evaluation, inside the unit Check blocks.

Additional-knowledge triage: **must-add bridges** — summation/integral as accumulation (Class 1), the eigenvector one-liner (Class 2), the uniform density f=1, and the toy pdf f(x)=2x. **should-add** — one line on why continuous point-probability is 0 (area of a line). **could-add** — the Gaussian density shape (one line). **do-not-add** — measure theory, Bayes, MLE, multivariate Gaussian algebra, named families beyond uniform/Gaussian.

Calibration: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) is the depth exemplar; implementation reference is the nearest governed sibling artifact `multivariate-calculus-v2.html` (CAN-2026-0014).

## Assessment and evidence of learning

Every unit check has ≥1 constructed-response numeric item plus ≥1 diagnostic MCQ with per-option feedback — checks c1–c9: random-variable type (c1), PMF sum/arithmetic (c2), area under a PDF (c3), CDF value and properties (c4), PDF↔CDF conversion (c5), expectation (c6), variance two ways (c7), covariance/correlation (c8), ML-connection reasoning (c9). Ladders L1–L6, three rungs each (worked → completion → independent), tiered never-auto-opening hints. Persistence: cleared checks fill nav dots; misses and confident mastery misses enter the `prob1-*` localStorage review list with a spacing invitation and visible reset; graceful fallback when storage is unavailable; corrupted-storage recovery.

Mastery: **11 items** (9 content units + 2), interleaved, 3-level confidence tags (`sure`/`think so`/`guessing`), confident misses routed to the review list. Includes reasoning, transfer (a situation not seen in the lesson), and error-identification items; no worked numbers reused.

## Accessibility and inclusion intent

Semantic landmarks, logical heading order, native controls, keyboard operability, aria-live readouts, per-canvas text equivalents, colour never the sole encoder, reduced motion, print fallback, focus rings, a 16px body floor, and no drag-only interaction. Every canvas has an inline legend and a same-numbers readout.

## Acceptance criteria and review boundary

Strict mechanical verification (`verify-candidate.py`, 0 failures); independent Python recomputation (numbers, keys); Node behavioral harness (gates, ladders, checks, mastery, reset); dependency-order read-through; six audits + adversarial gate ([ADR-0009](../../docs/adr/0009-forced-adversarial-re-examination-gate.md)); live rendered verification at 320/640/1024px with 0 console errors ([ADR-0010](../../docs/adr/0010-rendered-output-verification.md)) or a recorded degraded-mode note; repository checker exit 0. Disposition `private-pilot-complete`; non-independent; release-ineligible.

## Conformance checklist (depth-calibration contract)

- [x] Active benchmark BMK-2026-0001 cited as calibration exemplar
- [x] Depth-pass table complete for every unit (lede, signature visual, reveal arcs with payoff units, misconception callouts, ladders)
- [x] One full 3-rung faded ladder for each computational skill (L1–L6)
- [x] ≥2 explain-in-own-words items with model-answer reveals allocated (U5, U7)
- [x] Every forward promise / reveal arc names its explicit payoff unit
