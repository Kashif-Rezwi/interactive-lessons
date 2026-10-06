# XS-2026-0014: Interactive lesson candidate probability basics v1

**Status:** Approved  
**Approval scope:** Stage 1 governed generation  
**Supersedes / iteration position:** Iteration 1 — original  
**Source concept model:** [CM-2026-0013](../concepts/cm-2026-0013-probability-basics.md)  
**Learning plan:** [LP-2026-0014](../plans/lp-2026-0014-probability-basics.md)  
**Target learner:** AIML-4 student, post-Classes 1–2  
**Artifact family:** Single-file offline HTML  
**Learning outcomes:** per LP-2026-0014 §Measurable learning outcomes (10 outcomes, each exercised by ≥1 assessment item)

## Learner problem and teaching strategy

The agenda-style notebook (61 Markdown cells; five opaque base64 figures; one CDF typo; no code) becomes an explain-before-use path: orientation unit, nine units in canonical anatomy (Learn → Predict → Explore → Practice → Check → Connect), synthesis with interleaved mastery, persistent review list, glossary. One metaphor throughout: probability is a budget of 1.0 shared over the values; the PMF/PDF says how, the CDF says how much is spent by x. All readouts computed live; nothing hard-codes what can be computed.

## Content and evidence map

U0 cells 1–2 (orientation); U1 cells 3–13 (why probability; random variables; discrete vs continuous; the opaque RV figure cell 8 replaced by a labeled live W1 lab); U2 cells 14–19 (PMF; dice 1/6; cell 19's opaque properties figure stated in prose); U3 cells 20–21 (PDF; area = probability; uniform U(0,1); toy f(x)=2x); U4 cells 22–26 (CDF; U(0,1) F=x; four properties; cell-26 typo corrected); **U5 cells 27–39** (PDF/CDF relationship — cells 29 and 31 figures recovered as F=∫f and f=dF/dx; fundamental theorem cell 32; worked example cell 33; geometric reading cell 35; discrete summation cell 36; dice F(3)=1/2 cell 37; PMF recovery cell 39); U6 cells 40–46 (expectation; dice 3.5; E[X]=2/3; linearity, constant, sum rule; ML uses); U7 cells 47–51 (variance two ways; dice ≈2.92; standard deviation; bias–variance); U8 cells 52–55 (covariance; interpretation; Cov=0 ≠ independence; Y=X²; correlation [−1,1]); U9 cells 56–61 (PCA covariance matrix — cell 58 figure stated explicitly; eigenvectors = principal components; Gaussian mean+variance; multivariate uses covariance). No silent drops; full coverage matrix ships in EVAL-2026-0016.

## Learning sequence

U0 → U1 → U2 → U3 → U4 → U5 → U6 → U7 → U8 → U9 → Synthesis + mastery (M1–M11) → review list → glossary → colophon. Every forward reference is a promise with a named payoff unit (LP-2026-0014).

## Interaction and feedback specification

**W1 `rv-lab` (U1, canvas).** Manipulable: die sides n (slider 2–12, step 1, default 6). Goal: see how a discrete distribution shares the budget. Draws n equal bars of height 1/n; readout shows each P=1/n and Σ=1. Viewport xMin=0, xMax=12, yMin=0, yMax=1.05.

**W2 `pmf-lab` (U2, canvas).** Manipulable: target k (slider 1–6, default 3). Draws the dice PMF bars with bars 1..k shaded as the cumulative mass; readout P(X=k)=1/6 and F(k)=k/6. Viewport xMin=0, xMax=7, yMin=0, yMax=1.05.

**W3 `pdf-lab` (U3, canvas, gated by G1).** Manipulables: lower bound a (slider 0–1, default 0.2), upper bound b (slider 0–1, default 0.7, clamped ≥ a). Draws f(x)=2x on [0,1] with the region [a,b] shaded; readout area = b²−a². Viewport xMin=−0.05, xMax=1.05, yMin=0, yMax=2.3.

**W4 `cdf-lab` (U4, canvas).** Manipulable: x (slider 0–1, default 0.5). Draws F(x)=x² with the point (x, F(x)) marked; readout F(x)=x². Viewport xMin=−0.05, xMax=1.05, yMin=0, yMax=1.05.

**W5 `convert-lab` (U5, canvas, gated by G2, signature).** Manipulable: x (slider 0–1, default 0.6). Two panels: top = f(t)=2t on [0,1] with area [0,x] shaded; bottom = F(x)=x² with the height at x marked. Readout links "area = x²" and "F(x) = x²". Viewport per panel xMin=−0.05, xMax=1.05; top yMin=0, yMax=2.3; bottom yMin=0, yMax=1.05.

**W6 `expect-lab` (U6, canvas).** Manipulable: a horizontal shift c applied to the density f(x)=2(x−c) kept normalized on [c, c+1] is out of scope; instead the manipulable is the discrete sample size n (slider 1–10) for a uniform discrete variable on {1..n}, showing E[X]=(n+1)/2 as the balance point, alongside the continuous 2/3 marker. Viewport xMin=0, xMax=11, yMin=0, yMax=1.05.

**W7 `variance-lab` (U7, canvas, gated by G3).** Manipulable: spread s (slider 0–3, step 0.1, default 1). Two discrete distributions on {−s, 0, +s}-style symmetric mass with the same mean 0 but growing variance; readout Var=E[X²] (mean 0) and σ. Viewport xMin=−3.5, xMax=3.5, yMin=0, yMax=1.05.

**W8 `covariance-lab` (U8, canvas).** Manipulable: correlation ρ (slider −1..1, step 0.05, default 0.6). Draws a deterministic seeded point cloud whose sample correlation tracks ρ; readout Cov and Corr. Viewport xMin=−4, xMax=4, yMin=−4, yMax=4.

**W9 `pca-lab` (U9, canvas).** Manipulable: correlation ρ (slider −1..1, step 0.05, default 0.7). Draws the same cloud with the covariance ellipse and the two principal axes (eigenvectors); readout shows the variance along each axis. Viewport xMin=−4, xMax=4, yMin=−4, yMax=4.

## Formula manifest

| Formula ID | Name / Purpose | Equation (display) | Symbol Key Breakdown | Target Unit |
|---|---|---|---|---|
| `EQ-001` | Random variable | X: Ω → ℝ | X: the mapping; Ω: sample space; ℝ: reals | U1 |
| `EQ-002` | PMF | P(X=x) | X: discrete RV; x: an exact value | U2 |
| `EQ-003` | PMF properties | 0 ≤ P(X=x) ≤ 1, Σₓ P(X=x) = 1 | Σ: sum over all values; 1: total budget | U2 |
| `EQ-004` | PDF area = probability | P(a ≤ X ≤ b) = ∫ₐᵇ f(x) dx | f: density; ∫: accumulated area | U3 |
| `EQ-005` | Uniform density | f(x) = 1 on [0,1] | support [0,1]; height 1 | U3 |
| `EQ-006` | CDF definition | F(x) = P(X ≤ x) | F: running total; ≤: up to x | U4 |
| `EQ-007` | CDF properties | 0 ≤ F(x) ≤ 1; F(x)→0 (x→−∞), F(x)→1 (x→+∞) | limits; range | U4 |
| `EQ-008` | CDF as integral of PDF | F(x) = ∫_{−∞}^{x} f(t) dt | t: dummy variable; x: upper limit | U5 |
| `EQ-009` | PDF as derivative of CDF | f(x) = dF(x)/dx | d/dx: local rate of change | U5 |
| `EQ-010` | Fundamental theorem | P(a ≤ X ≤ b) = F(b) − F(a) | F(b)−F(a): accumulated difference | U5 |
| `EQ-011` | Discrete CDF (summation) | F(x) = Σ_{xᵢ ≤ x} P(X=xᵢ) | Σ: sum of masses up to x | U5 |
| `EQ-012` | Recovering a PMF | P(X=x) = F(x) − F(x⁻) | F(x⁻): left limit | U5 |
| `EQ-013` | Discrete expectation | E[X] = Σₓ x·P(X=x) | E[X]: weighted average | U6 |
| `EQ-014` | Continuous expectation | E[X] = ∫_{−∞}^{∞} x·f(x) dx | ∫ x f: density-weighted mean | U6 |
| `EQ-015` | Linearity | E[aX+b] = aE[X] + b; E[c] = c | a,b,c: constants | U6 |
| `EQ-016` | Sum rule | E[X+Y] = E[X] + E[Y] | holds even if dependent | U6 |
| `EQ-017` | Variance definition | Var(X) = E[(X−μ)²], μ=E[X] | μ: mean; (·)²: squared deviation | U7 |
| `EQ-018` | Computational variance | Var(X) = E[X²] − (E[X])² | E[X²]: second moment | U7 |
| `EQ-019` | Standard deviation | σ = √Var(X) | √: back to X's units | U7 |
| `EQ-020` | Covariance | Cov(X,Y) = E[(X−E[X])(Y−E[Y])] | centered product | U8 |
| `EQ-021` | Correlation | Corr(X,Y) = Cov(X,Y)/(σ_X σ_Y) | normalized to [−1,1] | U8 |
| `EQ-022` | Covariance matrix (2×2) | Σ = [[Var(X), Cov(X,Y)], [Cov(X,Y), Var(Y)]] | diagonal: variances; off-diagonal: covariance | U9 |
| `EQ-023` | Gaussian density | f(x) = (1/(σ√(2π)))·e^{−(x−μ)²/(2σ²)} | μ: mean; σ: spread | U9 |

## Term definition registry

Terms (each defined at first mention and linked to a 6-field glossary entry; zero deferred jargon): probability; uncertainty; random variable; sample space; outcome; discrete random variable; continuous random variable; probability distribution; probability mass function (PMF); probability density function (PDF); cumulative distribution function (CDF); density; area under the curve; support; uniform distribution; fundamental theorem; integral; derivative; left limit; expectation; expected value; mean; linearity of expectation; variance; standard deviation; spread; computational formula; bias–variance tradeoff; covariance; correlation; independence; uncorrelated; PCA; covariance matrix; eigenvector; principal component; Gaussian distribution; multivariate Gaussian; language model; token distribution; fraud detection; recommendation system.

## Visual/representation rationale

Each unit's idea is given a representation where it is literally visible: a bar chart where the budget is shared out (W1/W2), a curve whose shaded area is the probability (W3), a running-total curve (W4), a two-panel area↔height correspondence (W5), a balance point (W6), a spread change (W7), a joint cloud whose tilt is the covariance (W8), and the same cloud with its covariance ellipse and principal axes (W9). Colour is never the sole encoder: every shaded region and marker also carries a label and a numeric readout.

## Assessment and misconception checks

Checks c1–c9 each pair one bounded numeric item with one diagnostic MCQ; MCQ distractors are the CM's diagnosed misconceptions with option-specific feedback and the governing rule. Mastery M1–M11 (interleaved; reasoning, transfer, and error-identification items). No `<textarea>`; option sets use `.option-stack`/`.option-item`; numeric items auto-grade with tolerance.

## Accessibility and inclusion plan

Semantic landmarks, logical heading order, aria-live readouts, keyboard-operable native controls, per-canvas text equivalents (aria-label + same-numbers readout), colour never sole encoder, reduced motion, print fallback, focus rings, 16px floor, no drag-only interaction. Each canvas ships an inline legend; each slider a descriptive aria-label.

## Performance/responsiveness intent

Single file; zero external requests; nine canvases each responsive via `makeView` (clientWidth at draw time, DPR scaling, aspect-ratio height) with 9 resize listeners = canvas count; bounded per-redraw workloads; all widget math closed-form; nav single-line horizontal scroll; concept map internally scrollable at narrow widths.

## Acceptance criteria and evaluation dimensions

`verify-candidate.py` strict pass (0 failures); every formula-manifest equation present with a symbol key; every registry term defined and linked; every widget matches this specification element-for-element (including the declared viewports); six audits + adversarial gate pass; live rendered verification at 320/640/1024px with 0 console errors (or degraded-mode note); repository checker exit 0; disposition `private-pilot-complete`, non-independent, release-ineligible.

## Concept map (dependency nodes and directed edges)

Nodes (13): probability; random variable; discrete; continuous; PMF; PDF; CDF; conversion; expectation; variance; covariance; PCA; Gaussian. Directed edges (16): probability→random variable; random variable→discrete; random variable→continuous; discrete→PMF; continuous→PDF; PMF→CDF; PDF→CDF; CDF→conversion (integral); conversion→PDF (derivative); random variable→expectation; expectation→variance; variance→covariance; expectation→covariance; covariance→PCA; variance→Gaussian; covariance→Gaussian.

## Conformance checklist (depth-calibration contract)

- [x] Every widget declares learner-manipulable variable(s) (all nine canvases slider-driven)
- [x] Every canvas widget declares input bounding (sliders, min/max)
- [x] Every canvas widget declares its mathematical viewport
- [x] Controls declare atomic `.slider-control` encapsulation and `.option-stack` layout
- [x] Complete Formula manifest (EQ-001–EQ-023) mapped to unit `.formula` blocks
- [x] Complete Term definition registry (42 terms); zero deferred jargon
- [x] Assessment modality strictly MCQ / bounded auto-graded numeric; no `<textarea>`
- [x] Exhaustive glossary term set listed from the CM (every term used has 6 fields)
- [x] Concept map declares explicit dependency nodes and directed edges (multi-branch; 16 edges)
- [x] Every LP-planned ladder (L1–L6), prediction gate (G1–G3), and reveal arc has a specified element
- [x] Canvas text equivalents specified for every visual component
