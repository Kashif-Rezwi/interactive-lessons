# XS-2026-0015: Interactive lesson candidate probability basics v2

**Status:** Approved
**Approval scope:** Stage 1 governed generation
**Supersedes / iteration position:** Iteration 2 — deepens [XS-2026-0014](xs-2026-0014-probability-basics-v1.md) (adds W10–W12, L7–L8, M12–M13, and three glossary terms; W1–W9, G1–G3, and L1–L6 unchanged)
**Source concept model:** [CM-2026-0014](../concepts/cm-2026-0014-probability-basics.md)
**Learning plan:** [LP-2026-0015](../plans/lp-2026-0015-probability-basics.md)
**Target learner:** AIML-4 student, post-Classes 1–2
**Artifact family:** Single-file offline HTML
**Learning outcomes:** per LP-2026-0015 §Measurable learning outcomes (11 outcomes, each exercised by ≥1 assessment item)

## Learner problem and teaching strategy

The agenda-style notebook (61 Markdown cells; five opaque base64 figures; one CDF typo; no code) becomes an explain-before-use path: orientation unit, nine units in canonical anatomy (Learn → Predict → Explore → Practice → Check → Connect), synthesis with interleaved mastery, persistent review list, glossary. One metaphor throughout: probability is a budget of 1.0 shared over the values; the PMF/PDF says how, the CDF says how much is spent by x. All readouts computed live; nothing hard-codes what can be computed. The v2 deepening adds three labs (the two-point interval conversion, the discrete PMF-recovery staircase, and the Gaussian mean/width bell), two continuous-moment ladders, and two mastery items.

## Content and evidence map

U0 cells 1–2 (orientation); U1 cells 3–13; U2 cells 14–19 (cell 19's opaque properties figure stated in prose); U3 cells 20–21; U4 cells 22–26 (cell-26 typo corrected); **U5 cells 27–39** (cells 29/31 figures recovered as F=∫f and f=dF/dx; fundamental theorem cell 32 — **now shown at two points by W10**; worked example cell 33; discrete summation cell 36; dice F(3)=1/2 cell 37; **PMF recovery cell 39 — now shown live by W11**); U6 cells 40–46 (E[X]=2/3; **continuous ladder L7**); U7 cells 47–51 (dice ≈2.92; **continuous ladder L8**); U8 cells 52–55; U9 cells 56–61 (PCA cell 58 figure stated explicitly; **Gaussian mean+variance + 68–95 rule now shown live by W12**). No silent drops; full coverage matrix ships in EVAL-2026-0017.

## Learning sequence

U0 → U1 → U2 → U3 → U4 → U5 → U6 → U7 → U8 → U9 → Synthesis + mastery (M1–M13) → review list → glossary → colophon. Every forward reference is a promise with a named payoff unit (LP-2026-0015).

## Interaction and feedback specification

**W1 `rv-lab` (U1, canvas).** Manipulable: die sides n (slider 2–12, step 1, default 6). Draws n equal bars of height 1/n; readout shows each P=1/n and Σ=1. Viewport xMin=0, xMax=12, yMin=0, yMax=1.05.

**W2 `pmf-lab` (U2, canvas).** Manipulable: target k (slider 1–6, default 3). Draws the dice PMF bars with bars 1..k shaded; readout P(X=k)=1/6 and F(k)=k/6. Viewport xMin=0, xMax=7, yMin=0, yMax=1.05.

**W3 `pdf-lab` (U3, canvas, gated by G1).** Manipulables: a (0–1, default 0.2), b (0–1, default 0.7, clamped ≥ a). Draws f(x)=2x on [0,1] with [a,b] shaded; readout area = b²−a². Viewport xMin=−0.05, xMax=1.05, yMin=0, yMax=2.3.

**W4 `cdf-lab` (U4, canvas).** Manipulable: x (slider 0–1, default 0.5). Draws F(x)=x² with the point (x, F(x)) marked; readout F(x)=x². Viewport xMin=−0.05, xMax=1.05, yMin=0, yMax=1.05.

**W5 `convert-lab` (U5, canvas, gated by G2, signature).** Manipulable: x (slider 0–1, default 0.6). Two panels: top f(t)=2t with area [0,x] shaded; bottom F(x)=x² with the height at x marked. Viewport per panel xMin=−0.05, xMax=1.05; top yMin=0, yMax=2.3; bottom yMin=0, yMax=1.05.

**W10 `convert2-lab` (U5, canvas, v2 — two-point fundamental theorem).** Manipulables: lower bound a (slider 0–1, step 0.01, default 0.2) and upper bound b (slider 0–1, step 0.01, default 0.7, clamped ≥ a). Draws f(x)=2x on [0,1] with the region [a,b] shaded, plus a CDF inset showing the rise from F(a) to F(b). Readout gives the shaded area b²−a² and the CDF difference F(b)−F(a) as the same number. Degenerate-state guard: a==b → zero area, both readouts show 0. Viewport xMin=−0.05, xMax=1.05, yMin=0, yMax=2.3.

**W11 `pmfrecover-lab` (U5, canvas, v2 — discrete PMF recovery).** Manipulable: value x (slider 1–6, step 1, default 3). Draws the fair-die CDF staircase F(v)=⌊v⌋/6 with the step at x highlighted, marking F(x) and the left limit F(x⁻); readout gives P(X=x)=F(x)−F(x⁻)=1/6. Viewport xMin=0, xMax=7, yMin=0, yMax=1.05.

**W6 `expect-lab` (U6, canvas).** Manipulable: discrete sample size n (slider 1–10) for a uniform discrete variable on {1..n}, showing E[X]=(n+1)/2 as the balance point. Viewport xMin=0, xMax=11, yMin=0, yMax=1.05.

**W7 `variance-lab` (U7, canvas, gated by G3).** Manipulable: spread s (slider 0–3, step 0.1, default 1). Two masses at ±s (and 0) with the same mean 0 but growing variance; readout Var=E[X²] and σ. Viewport xMin=−3.5, xMax=3.5, yMin=0, yMax=1.05.

**W8 `covariance-lab` (U8, canvas).** Manipulable: correlation ρ (slider −1..1, step 0.05, default 0.6). Draws a deterministic seeded point cloud whose sample correlation tracks ρ; readout Cov and Corr. Viewport xMin=−4, xMax=4, yMin=−4, yMax=4.

**W9 `pca-lab` (U9, canvas).** Manipulable: correlation ρ (slider −1..1, step 0.05, default 0.7). Draws the cloud with the covariance ellipse and the two principal axes; readout shows the variance along each axis. Viewport xMin=−4, xMax=4, yMin=−4, yMax=4.

**W12 `gaussian-lab` (U9, canvas, v2 — Gaussian shape).** Manipulables: mean μ (slider −2..2, step 0.1, default 0) and standard deviation σ (slider 0.4..2.5, step 0.1, default 1). Draws the Gaussian density (height scaled to 1) with the μ ± σ band shaded; readout gives the peak density 1/(σ√(2π)) and the ≈68% band. Viewport xMin=−6, xMax=6, yMin=0, yMax=1.1.

## Formula manifest

The v2 artifact carries the same 19 `.formula` blocks as v1 (no new formal equation is introduced by the deepening — the two-point form is EQ-010, the second moment appears inside EQ-016, and the Gaussian density is EQ-022). The manifest is unchanged from [XS-2026-0014](xs-2026-0014-probability-basics-v1.md) §Formula manifest:

| Formula ID | Name / Purpose | Equation (display) | Target Unit |
|---|---|---|---|
| `EQ-001` | Random variable | X: Ω → ℝ | U1 |
| `EQ-002` | PMF | P(X=x) | U2 |
| `EQ-003` | PMF properties | 0 ≤ P(X=x) ≤ 1, Σₓ P(X=x) = 1 | U2 |
| `EQ-004` | PDF area = probability | P(a ≤ X ≤ b) = ∫ₐᵇ f(x) dx | U3 |
| `EQ-005` | Uniform density | f(x) = 1 on [0,1] | U3 |
| `EQ-006` | CDF definition | F(x) = P(X ≤ x) | U4 |
| `EQ-007` | CDF properties | 0 ≤ F(x) ≤ 1; F→0 (x→−∞), F→1 (x→+∞) | U4 |
| `EQ-008` | CDF as integral of PDF | F(x) = ∫_{−∞}^{x} f(t) dt | U5 |
| `EQ-009` | PDF as derivative of CDF | f(x) = dF(x)/dx | U5 |
| `EQ-010` | Fundamental / two-point theorem | P(a ≤ X ≤ b) = F(b) − F(a) | U5 |
| `EQ-011` | Discrete CDF (summation) | F(x) = Σ_{xᵢ ≤ x} P(X=xᵢ) | U5 |
| `EQ-012` | Recovering a PMF | P(X=x) = F(x) − F(x⁻) | U5 |
| `EQ-013` | Discrete expectation | E[X] = Σₓ x·P(X=x) | U6 |
| `EQ-014` | Continuous expectation | E[X] = ∫ x·f(x) dx | U6 |
| `EQ-015` | Linearity / constant / sum | E[aX+b]=aE[X]+b; E[c]=c; E[X+Y]=E[X]+E[Y] | U6 |
| `EQ-016` | Variance (definition) | Var(X) = E[(X − μ)²], μ = E[X] | U7 |
| `EQ-017` | Variance (computational) | Var(X) = E[X²] − (E[X])² | U7 |
| `EQ-018` | Standard deviation | σ = √Var(X) | U7 |
| `EQ-019` | Covariance | Cov(X,Y) = E[(X−E[X])(Y−E[Y])] | U8 |
| `EQ-020` | Correlation | Corr(X,Y) = Cov(X,Y)/(σ_X σ_Y) | U8 |
| `EQ-021` | Covariance matrix | Σ = [[Var(X), Cov(X,Y)], [Cov(X,Y), Var(Y)]] | U9 |
| `EQ-022` | Gaussian density | f(x) = (1/(σ√(2π)))·e^{−(x−μ)²/(2σ²)} | U9 |
| `EQ-023` | Second moment | E[X²] | U7 |

## Term definition registry

The v1 registry (42 terms) is inherited unchanged; the deepening adds three terms, each with a complete 6-field glossary entry:

| Term | First Appearance | Introductory Intuition / Definition | Glossary Status |
|---|---|---|---|
| second moment | Unit 7 | The average of the squared values, E[X²]; the bridge in Var = E[X²] − (E[X])² | Complete 6-field entry (`#g-secondmoment`) |
| 68–95 rule (empirical rule) | Unit 9 | For a Gaussian, ≈68% of probability lies within μ ± σ and ≈95% within μ ± 2σ | Complete 6-field entry (`#g-6895`) |
| two-point conversion | Unit 5 | P(a ≤ X ≤ b) = F(b) − F(a); the interval form of the fundamental theorem | Complete 6-field entry (`#g-twopoint`) |

## Assessment and misconception checks

Unit checks c1–c9 (unchanged): each a bounded numeric item plus a diagnostic MCQ with `.option-stack` option sets and per-option feedback. Ladders: L1–L6 (unchanged) plus **L7 (continuous expectation: f=2x → 2/3; uniform → 0.5; 3x² → 0.75)** and **L8 (continuous variance: f=2x → 1/18; uniform → 1/12; 3x² → 0.0375)**. Prediction gates G1–G3 (unchanged). Mastery: M1–M11 (unchanged) plus **M12 (transfer: P(0.3≤X≤0.8) for F=x⁴ → 0.4015)** and **M13 (reasoning: a Gaussian is fixed by mean and variance)**. Explain-in-own-words: E1 (U5), E2 (U7). No `<textarea>`; all inputs bounded numeric, MCQs, or reveal-style self-assessment.

## Accessibility and inclusion plan

12 canvas text equivalents (one per widget, updated for W10–W12); keyboard-operable native controls; `aria-live="polite"` readouts; inline legends for every multi-entity canvas; colour never the sole encoder; reduced-motion and print fallbacks; 16.5px body floor.

## Performance/responsiveness intent

Single file, zero external requests, offline-capable; 12 canvases each measure `clientWidth` at draw time and attach a `resize` listener (≥ 12 resize listeners). No build step.

## Acceptance criteria and evaluation dimensions

See LP-2026-0015 §Acceptance criteria and review boundary. All ten evaluation-framework dimensions assessed; rendered verification recorded as performed (500/640/1024px, 0 console errors) with the 320px true-mobile-emulation gap noted.

## Conformance checklist (depth-calibration contract)

Before approval, verify against [depth-calibration-contract.md](../../docs/01-product/depth-calibration-contract.md):
- [x] Every widget declares learner-manipulable variable(s) or explicit "static demo" justification
- [x] Every canvas widget declares input bounding (sliders, min/max) or autoscaling parameters
- [x] **Every canvas widget declares its mathematical viewport (`xMin`, `xMax`, `yMin`, `yMax`) for the P5 `makeView` conformance sweep ([ADR-0013](../../docs/adr/0013-canvas-engineering-standard-adoption.md) §2)**
- [x] Controls declare atomic `.slider-control` encapsulation and `.option-stack` layout
- [x] Complete **Formula manifest** provided; every formula is mapped to a unit `.formula` block
- [x] Complete **Term definition registry** provided; zero deferred jargon or unexplained terms
- [x] Assessment modality strictly avoids `<textarea>` / open text in favor of diagnostic MCQs and visual widgets
- [x] Exhaustive glossary term set listed from the CM (every term used will have 6 fields)
- [x] Concept map declares explicit dependency nodes and directed edges (multi-branch graph)
- [x] Every LP-planned ladder, prediction gate, and reveal arc has a specified element
- [x] Canvas text equivalents specified for every visual component
