# CM-2026-0014: Probability basics for machine learning (concept model, v2 deepening)

**Status:** Reviewed
**Supersedes / iteration position:** Iteration 2 — deepens [CM-2026-0013](cm-2026-0013-probability-basics.md) (same 61-cell source, unchanged SHA-256; the v1 concept set is preserved and the deepening adds the second-moment, two-point-conversion, and 68–95-rule concepts plus a deepened Gaussian-shape claim)
**Owner:** Repository maintainer
**Source package:** [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md)
**Domain review status:** Reviewed by the same operator; non-independent
**Confidence:** high

**Intake:** source SHA-256 `837a1736e4286cf6b8b0d91792dd6611162dfb811332860a5dfca67fc60fd0ac`; all 61 Markdown cells re-read in order. Five cells are opaque base64 figures (8, 19, 29, 31, 58) and one cell carries a CDF upper-limit typo (26) — both dispositioned below. This CM is the v2 iteration of CM-2026-0013; it retains the v1 claims and adds the deepening claims marked **(v2)**.

**Cross-lesson continuity:** assumes AIML-4 Class 1 (functions, slope, summation Σ, the integral as accumulated area) and Class 2 (matrix vocabulary, the eigenvector one-liner — used only for the PCA link, never re-derived). No prior probability assumed. This lesson is the first probability node in the module.

## Scope and learning boundary

In scope: probability as uncertainty; random variables and their types; PMF, PDF, CDF; the CDF ↔ PDF (and CDF ↔ PMF) conversion including its two-point form; expectation and its properties; variance and standard deviation; covariance and correlation; the second moment; the Gaussian shape rule; and the ML connections the source names (LLM token distributions, fraud detection, recommendation, PCA, Gaussian models). Out of scope (do-not-add, standard §7): measure-theoretic foundations, proofs of the fundamental theorem, named continuous families beyond the uniform/Gaussian mention, Bayes' theorem and conditional-probability calculus, MLE/Bayesian inference, multivariate Gaussian density algebra, and estimator theory.

## Concepts and definitions

1. **Probability** — a number in [0,1] expressing how likely an outcome is; the language of uncertainty.
2. **Sample space Ω** — the set of all possible outcomes of a random process.
3. **Outcome / event** — a single result; a set of results whose probability we may ask about.
4. **Random variable (RV)** — a function mapping each outcome to a real number, X: Ω → ℝ.
5. **Discrete RV** — takes countable values; probabilities attach to exact values.
6. **Continuous RV** — takes infinitely many values in an interval; probability attaches to ranges.
7. **Probability distribution** — the rule describing how probability is spread over an RV's values.
8. **Probability mass function (PMF)** — for a discrete RV, P(X=x), the probability of an exact value.
9. **Probability density function (PDF)** — for a continuous RV, f(x), a density whose integral over a range is probability.
10. **Cumulative distribution function (CDF)** — for any RV, F(x) = P(X ≤ x), the accumulated probability up to x.
11. **Density** — the height of a PDF; not a probability.
12. **Area under the curve** — the probability that a continuous RV falls in an interval.
13. **Support** — the set of x where the density/mass is nonzero (e.g. [0,1] for U(0,1)).
14. **Uniform distribution U(0,1)** — density f(x)=1 on [0,1]; CDF F(x)=x.
15. **Fundamental theorem (of probability conversion)** — CDF is the integral of the PDF; PDF is the derivative of the CDF.
16. **Two-point conversion (v2)** — P(a ≤ X ≤ b) = F(b) − F(a), the interval form of the fundamental theorem; the two-point reading of the same slice.
17. **Integral** — accumulated area; turns a density into a cumulative probability.
18. **Derivative** — local rate of change; turns a cumulative probability back into a density.
19. **Left limit F(x⁻)** — the value the CDF approaches from below; used to recover a discrete PMF.
20. **Expectation E[X]** — the probability-weighted long-run average of an RV.
21. **Mean μ** — synonym for E[X].
22. **Second moment (v2)** — E[X²], the average of the squared values; the bridge in Var = E[X²] − (E[X])².
23. **Linearity of expectation** — E[aX+b]=aE[X]+b; E[X+Y]=E[X]+E[Y].
24. **Variance** — E[(X−μ)²] = E[X²] − (E[X])²; the expected squared spread.
25. **Standard deviation σ** — √Var(X); spread in the data's own units.
26. **Bias–variance tradeoff** — the error decomposition; high variance = overfitting.
27. **Covariance** — E[(X−E[X])(Y−E[Y])]; whether two variables move together.
28. **Correlation** — Cov/(σ_X σ_Y) ∈ [−1,1]; unit-free linear association.
29. **Independence** — P(X,Y)=P(X)P(Y); stronger than zero covariance.
30. **Uncorrelated** — Cov(X,Y)=0; no *linear* relation.
31. **Covariance matrix** — the table of variances (diagonal) and covariances (off-diagonal).
32. **Eigenvector / eigenvalue** — the directions a matrix only stretches and their stretch factors (Class 2, reused).
33. **Principal component** — an eigenvector of the covariance matrix; a direction of maximum variance.
34. **PCA** — the eigen-decomposition of the covariance matrix for compression/visualization.
35. **Gaussian (normal) distribution** — the bell; determined by mean μ and variance σ².
36. **68–95 rule (v2)** — for a Gaussian, ≈68% of probability lies within μ ± σ and ≈95% within μ ± 2σ.
37. **Multivariate Gaussian** — a Gaussian with a mean vector and a covariance matrix.

## Atomic claims and evidence anchors

| # | Claim | Source anchor |
|---|---|---|
| 1 | ML systems make probabilistic, not certain, predictions. | cell 3 |
| 2 | An LLM outputs a distribution over the next token; the top token is sampled. | cells 4–5 |
| 3 | Fraud detection estimates P(Fraud \| features); 0.02 ≈ safe, 0.95 ≈ suspicious. | cell 5 |
| 4 | Recommenders rank by P(User Likes Item). | cell 5 |
| 5 | A random variable maps outcomes to numbers, X: Ω → ℝ. | cells 6–8 |
| 6 | Ω is the sample space; ℝ is the real line. | cells 8–9 |
| 7 | Dice: Ω={1..6}, X ∈ {1..6}. | cell 10 |
| 8 | Rainfall: X ∈ [0,∞) is continuous. | cell 11 |
| 9 | Discrete RVs take countable values; P(X=3) is meaningful. | cells 12–13 |
| 10 | Continuous RVs take infinitely many values; P(X=x)=0; use P(a ≤ X ≤ b). | cell 13 |
| 11 | A PMF gives P(X=x) at exact values; fair die P=1/6. | cells 16–18 |
| 12 | PMF properties: 0 ≤ P(X=x) ≤ 1 and Σ P(X=x) = 1. | cell 19 (figure recovered) |
| 13 | A PDF's probability is the area under the curve; f(x) ≠ P(X=x). | cells 20–21 |
| 14 | Uniform U(0,1) has f(x)=1 on [0,1]. | cell 21 |
| 15 | CDF works for both types; F(x)=P(X ≤ x) is accumulated probability. | cells 22–24 |
| 16 | U(0,1) has F(x)=x; F(0.2)=20%, F(0.7)=70%. | cells 24–25 |
| 17 | CDF is non-decreasing, in [0,1], right-continuous, →0 left and →1 right. | cell 26 (upper limit corrected 0→1) |
| 18 | PDF is local density; CDF is total accumulated probability. | cell 28 |
| 19 | CDF = ∫f (area); PDF = dF/dx (slope). | cells 29, 31 (figures recovered) |
| 20 | P(a ≤ X ≤ b) = F(b) − F(a) = ∫ₐᵇ f. | cell 32 |
| 21 | Worked example f(x)=2x on [0,1] → F(x)=x²; F(1)=1; d/dx(x²)=2x. | cell 33 |
| 22 | Discrete CDF is a summation; dice F(3)=1/2. | cells 36–37 |
| 23 | Recover a PMF from its CDF: P(X=x)=F(x)−F(x⁻). | cell 39 |
| 24 | Expectation is the long-run / probability-weighted average; dice E[X]=3.5. | cells 40–42 |
| 25 | 3.5 is never rolled — expectation need not be attainable. | cell 42 |
| 26 | E[X]=Σ x P(X=x) (discrete); E[X]=∫ x f(x) dx (continuous). | cell 43 |
| 27 | For f(x)=2x on [0,1], E[X]=2/3. | cells 44–45 |
| 28 | E[aX+b]=aE[X]+b; E[c]=c; E[X+Y]=E[X]+E[Y] (even if dependent). | cell 46 |
| 29 | Var(X)=E[(X−μ)²] with μ=E[X]. | cells 48–49 |
| 30 | Var(X)=E[X²]−(E[X])² (computational form). | cell 50 |
| 31 | Dice: E[X²]=91/6, Var ≈ 2.92. | cell 51 |
| 32 | σ=√Var is spread in original units. | cell 51 |
| 33 | High variance = unstable/sensitive models; bias–variance tradeoff. | cell 51 |
| 34 | Cov(X,Y)=E[(X−E[X])(Y−E[Y])]; positive/negative/zero meanings. | cells 53–54 |
| 35 | Cov=0 does not imply independence (Y=X² symmetric example). | cell 55 |
| 36 | Corr(X,Y)=Cov/(σ_X σ_Y) ∈ [−1,1]. | cell 55 |
| 37 | PCA uses the covariance matrix; eigenvectors are the principal components. | cells 57–58 (figure recovered) |
| 38 | Gaussian models depend on mean and variance; multivariate adds covariance. | cell 61 |
| 39 **(v2)** | The fundamental theorem holds at two points, not only from −∞; the interval probability is the CDF's rise. | cell 32 (deepened) |
| 40 **(v2)** | E[X²] is the second moment; variance = second moment − square of the first. | cells 50–51 (deepened) |
| 41 **(v2)** | For a Gaussian, ≈68% of probability lies within μ ± σ and ≈95% within μ ± 2σ. | cell 61 (deepened) |

## Prerequisites and relationships

Dependency chain (each node taught before first use): outcome/sample space → random variable → discrete/continuous → distribution → PMF (discrete) and PDF (continuous) → CDF (both) → CDF↔PDF conversion (needs PDF **and** CDF **and** the integral) → two-point conversion (needs the CDF and the interval idea) → expectation (needs the distribution) → second moment → variance (needs E[X] **and** E[X²]) → standard deviation → covariance (needs two RVs and their means) → correlation (needs two standard deviations) → covariance matrix → eigenvectors (Class 2) → PCA and Gaussian. Source use-before-define cases repaired: the PMF-properties figure (cell 19) is stated in prose in U2; the CDF upper-limit typo (cell 26) is corrected in U4.

## Examples, non-examples, and misconceptions

Examples (all anchored): fair die (cells 10, 18, 37, 42, 51); rainfall (cell 11); uniform U(0,1) (cell 21); toy density f(x)=2x (cells 33, 45); loaded die (derived); study-hours/scores and speed/time (cell 54); Y=X² (cell 55); covariance matrix [[2,1],[1,2]] (cells 58–59); the "world 0.41 / everyone 0.22" token table (cells 4–5).

Non-examples: a discrete value treated as continuous (P(X=3) for rainfall is 0); a density read as a probability; covariance read as dependence.

Misconceptions (each becomes a distractor or alert): (1) "a random variable *is* the outcome" (U1); (2) "the masses must be equal" (U2); (3) "f(0.5)=2 is a 200% chance" (U3); (4) "F(x) is P(X=x)" (U4); (5) "to get the PDF you integrate" (U5, reversed); (6) "3.5 is impossible, so the mean is wrong" (U6); (7) "variance 2.92 means ±2.92 in the data's units" (U7); (8) "Cov=0 means independent" (U8); (9) "a Gaussian is just its mean" (U9); (10) "the CDF upper limit is 0" (cell-26 typo, corrected).

## Ambiguities, gaps, and assumptions

The source is agenda-style with no derivations; the lesson supplies worked examples the source only states. Five figures are opaque; their content is recoverable from surrounding prose and is emitted live. No code outputs exist to recompute. Assumption: the learner has seen Σ and the integral-as-area in Class 1.

## Review and acceptance criteria

Downstream artifacts must (a) cover all 41 claims or record a disposition, (b) teach in the dependency order above, (c) surface each misconception, and (d) emit the three **(v2)** claims live (the two-point lab, the second-moment identity, and the Gaussian shape rule).

## Conformance checklist (depth-calibration contract)

Before approval, verify against [depth-calibration-contract.md](../../docs/01-product/depth-calibration-contract.md):
- [x] $\ge 1$ anchored atomic claim per concept (41 claims across 37 concepts)
- [x] Full dependency graph covering every prerequisite and flagging every source use-before-define case
- [x] $\ge 1$ diagnosed misconception per major concept with clear wrong-answer definitions
- [x] Every source example anchored to a cell
- [x] $\ge 1$ non-example per conceptual distinction the source draws
