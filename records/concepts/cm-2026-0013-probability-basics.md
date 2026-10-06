# CM-2026-0013: Probability basics for machine learning (concept model)

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 1 — original  
**Owner:** Repository maintainer  
**Source package:** [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md)  
**Domain review status:** Reviewed by the same operator; non-independent  
**Confidence:** high

**Intake:** source SHA-256 `837a1736e4286cf6b8b0d91792dd6611162dfb811332860a5dfca67fc60fd0ac`; all 61 cells re-read in order. Five cells are opaque base64 figures (8, 19, 29, 31, 58) and one cell carries a CDF upper-limit typo (26) — both dispositioned below.

**Cross-lesson continuity:** assumes AIML-4 Class 1 (functions, slope, summation Σ, the idea of an integral as accumulated area) and Class 2 (matrix vocabulary, eigenvectors — used only for the PCA one-liner, never re-derived). No prior probability assumed. This lesson is the first probability node in the module; its CM will be referenced by any later statistics/inference lesson.

## Scope and learning boundary

In scope: probability as uncertainty; random variables and their types; PMF, PDF, CDF; the CDF ↔ PDF (and CDF ↔ PMF) conversion; expectation and its properties; variance and standard deviation; covariance and correlation; and the ML connections the source names (LLM token distributions, fraud detection, recommendation, PCA, Gaussian models). Out of scope (do-not-add, standard §7): measure-theoretic foundations, proofs of the fundamental theorem, named continuous families beyond the uniform/Gaussian mention, Bayes' theorem and conditional-probability calculus, MLE/Bayesian inference, multivariate Gaussian density algebra, and estimator theory.

## Concepts and definitions

1. **Probability** — a number in [0,1] expressing how likely an outcome is; the language of uncertainty.
2. **Sample space Ω** — the set of all possible outcomes of a random process.
3. **Outcome / event** — a single result; a set of results whose probability we may ask about.
4. **Random variable (RV)** — a function mapping each outcome to a real number, X: Ω → ℝ.
5. **Discrete RV** — takes countable values; probabilities attach to exact values.
6. **Continuous RV** — takes infinitely many values in an interval; probability attaches to ranges.
7. **Probability distribution** — the rule describing how probability is spread over the values of an RV.
8. **Probability mass function (PMF)** — for a discrete RV, P(X=x), the probability of an exact value.
9. **Probability density function (PDF)** — for a continuous RV, f(x), a density whose integral over a range is probability.
10. **Cumulative distribution function (CDF)** — for any RV, F(x) = P(X ≤ x), the accumulated probability up to x.
11. **Density** — the height of a PDF; not a probability.
12. **Area under the curve** — the probability that a continuous RV falls in an interval.
13. **Support** — the set of x where the density/mass is nonzero (e.g. [0,1] for U(0,1)).
14. **Uniform distribution U(0,1)** — density f(x)=1 on [0,1]; CDF F(x)=x.
15. **Fundamental theorem (of probability conversion)** — CDF is the integral of the PDF; PDF is the derivative of the CDF.
16. **Integral** — accumulated area; turns a density into a cumulative probability.
17. **Derivative** — local rate of change; turns a cumulative probability back into a density.
18. **Left limit F(x⁻)** — the value the CDF approaches from below; used to recover a discrete PMF.
19. **Expectation E[X]** — the probability-weighted long-run average of an RV.
20. **Mean μ** — synonym for E[X].
21. **Linearity of expectation** — E[aX+b]=aE[X]+b; E[X+Y]=E[X]+E[Y].
22. **Variance Var(X)** — expected squared deviation from the mean; spread.
23. **Standard deviation σ** — the square root of the variance; spread in original units.
24. **Computational variance formula** — Var(X)=E[X²]−(E[X])².
25. **Bias–variance tradeoff** — high bias underfits, high variance overfits.
26. **Covariance Cov(X,Y)** — expected product of the two centered variables; joint movement.
27. **Correlation ρ** — covariance normalized by the two standard deviations; in [−1,1].
28. **Independence vs uncorrelated** — Cov(X,Y)=0 (uncorrelated) does not imply independence.
29. **PCA** — finds the directions of maximum variance from the covariance matrix; eigenvectors are the principal components.
30. **Covariance matrix** — the matrix of pairwise covariances; its diagonal holds variances.
31. **Eigenvector / principal component** — a direction the covariance matrix only scales.
32. **Gaussian (normal) distribution** — a distribution determined by mean and variance.
33. **Multivariate Gaussian** — a Gaussian over several variables; additionally uses the covariance matrix.
34. **Language model token distribution** — the probability distribution an LLM emits over the next token.
35. **Fraud-detection score** — P(Fraud | transaction features), a conditional probability used as a decision score.

## Atomic claims and evidence anchors

1. Probability is the mathematical language of uncertainty; AI systems make probabilistic, not certain, decisions (cell 3).
2. ML models answer likelihood questions: spam, fraud, next token, click (cells 3–5).
3. An LLM outputs a probability distribution over vocabulary tokens and samples/generates the highest-probability token; the source's table is world 0.41 > everyone 0.22 > people 0.18 (cell 5).
4. Fraud detection computes P(Fraud | Transaction Features); ≈0.02 → safe, ≈0.95 → highly suspicious (cell 5).
5. Recommendation systems estimate P(User Likes Item); ranking is probability ranking (cell 5).
6. A random variable maps outcomes of a random process to numerical values (cell 7).
7. Formally X: Ω → ℝ, where Ω is the sample space and ℝ the reals; every outcome gets a number (cells 8–9).
8. Dice: Ω={1,2,3,4,5,6}, X = number on the die, X ∈ {1..6} (cell 10).
9. Rainfall: X = rainfall in mm tomorrow, X ∈ [0,∞), continuous (cell 11).
10. A discrete RV takes countable (finite or countably infinite) values; probabilities attach to exact values; P(X=3) is meaningful (cell 13).
11. Discrete examples: dice roll, number of customers, emails, defective products (cell 13).
12. A continuous RV takes infinitely many values in an interval; examples height, weight, temperature, time, voltage (cell 13).
13. For a continuous RV, P(X=x)=0 at every single point; instead P(a ≤ X ≤ b) matters (cell 13).
14. A probability distribution describes how probability is distributed over an RV's values (cell 15).
15. The PMF is used for discrete RVs and gives the probability at exact values, P(X=x) (cell 17).
16. Dice PMF: P(X=x)=1/6 for x ∈ {1..6} (cell 17).
17. PMF properties: each mass in [0,1] and the masses sum to 1 (cell 19; figure recovered from standard properties).
18. The PDF is used for continuous RVs; probability is the area under the curve f(x) (cell 21).
19. For a continuous RV f(x) ≠ P(X=x); indeed P(X=x)=0 (cells 13, 21).
20. Uniform example: X ~ U(0,1) has f(x)=1 for 0 ≤ x ≤ 1 (cell 21).
21. The CDF works for both discrete and continuous variables; F(x)=P(X ≤ x) is the total accumulated probability up to x (cell 23).
22. Intuition: the CDF answers "how much probability has accumulated so far?" (cell 23).
23. U(0,1) example: F(x)=x on [0,1]; at x=0.2, 20% accumulated; at x=0.7, 70% (cell 24).
24. CDF properties: (i) non-decreasing — F(a) ≤ F(b) when a < b; (ii) range 0 ≤ F(x) ≤ 1; (iii) right-continuous; (iv) limits F(x)→0 as x→−∞ and F(x)→1 as x→+∞ (cell 26; the source's upper limit of 0 is a transcription error corrected to 1).
25. PDF = local probability density; CDF = total accumulated probability (cell 28).
26. Core relationship: the CDF is the area under the PDF; the PDF is the slope/derivative of the CDF (cell 29).
27. F(x) = ∫_{−∞}^{x} f(t) dt (cell 29 figure; recovered).
28. Reverse conversion: f(x) = dF(x)/dx (cell 31 figure; recovered).
29. Fundamental theorem: P(a ≤ X ≤ b) = F(b) − F(a) = ∫_a^b f(x) dx (cell 32).
30. Worked example: f(x)=2x on [0,1] → F(x)=x²; check F(1)=1; differentiating d/dx(x²)=2x recovers the PDF (cell 33).
31. Geometric reading: PDF height = density; area under the PDF = probability; the CDF is accumulated area (cell 35).
32. Discrete case: F(x)=P(X ≤ x) is obtained by summation (cell 36).
33. Dice CDF: F(3)=P(X≤3)=1/6+1/6+1/6=1/2 (cell 37).
34. Recovering a discrete PMF: P(X=x)=F(x)−F(x⁻), where F(x⁻) is the left limit (cell 39).
35. Expectation is the long-run average, equivalently the probability-weighted average (cell 41).
36. Dice expectation: E[X]=1·(1/6)+…+6·(1/6)=3.5; the expectation need not be an attainable outcome (cell 41).
37. Discrete expectation: E[X]=Σ_x x·P(X=x) (cell 43).
38. Continuous expectation: E[X]=∫_{−∞}^{∞} x·f(x) dx (cell 43).
39. Expectation example: f(x)=2x on [0,1] → E[X]=∫_0^1 2x² dx = 2/3 (cell 43).
40. Linearity: E[aX+b]=aE[X]+b (cell 45).
41. E[c]=c for a constant c (cell 45).
42. Sum rule: E[X+Y]=E[X]+E[Y], true even if X and Y are dependent (cell 45).
43. Expectation in ML represents mean prediction, average reward in RL, average loss, expected risk, expected return (cell 46).
44. Variance measures uncertainty/spread: how far values deviate from the mean (cell 48).
45. Var(X)=E[(X−μ)²] with μ=E[X] (cell 48).
46. Computational formula: Var(X)=E[X²]−(E[X])² (cell 48).
47. Dice variance: E[X²]=91/6, Var(X)=91/6−(3.5)²≈2.92 (cell 50).
48. Standard deviation σ=√Var(X), spread in the original units (cell 50).
49. High variance means unstable predictions, model sensitivity, more uncertainty (cell 51).
50. Bias–variance tradeoff: high bias → underfitting, high variance → overfitting (cell 51).
51. Covariance measures whether two variables move together: Cov(X,Y)=E[(X−E[X])(Y−E[Y])] (cell 53).
52. Covariance interpretation: positive → move together; negative → move oppositely; zero → no linear relation (cell 53).
53. Examples: more study hours → higher scores (positive covariance); more speed → less travel time (negative) (cell 53).
54. Key insight: Cov(X,Y)=0 does NOT imply independence (cell 53).
55. Example: Y=X² with a symmetric distribution around zero can have zero covariance while the variables are clearly dependent (cell 55).
56. Correlation normalizes covariance: Corr(X,Y)=Cov(X,Y)/(σ_X σ_Y), with range [−1,1] (cell 55).
57. PCA uses the covariance matrix; its goal is to find directions of maximum variance (cell 58).
58. The eigenvectors of the covariance matrix give the principal components (cell 59).
59. Gaussian distributions depend on mean and variance (cell 61).
60. A multivariate Gaussian additionally uses the covariance (cell 61).

## Prerequisites and relationships

Dependency graph (directed, multi-branch):

- OUTCOME → RANDOM_VARIABLE → {DISCRETE, CONTINUOUS}
- DISCRETE → PMF; CONTINUOUS → PDF
- {PMF, PDF} → DISTRIBUTION
- DISTRIBUTION → CDF
- CDF ↔ PDF (integral/derivative edges); PMF → discrete-CDF (summation edge); CDF → PMF recovery (left-limit edge)
- CDF → FUNDAMENTAL_THEOREM (P(a≤X≤b)=F(b)−F(a))
- RANDOM_VARIABLE → EXPECTATION → {VARIANCE, MEAN}
- VARIANCE → STANDARD_DEVIATION
- {EXPECTATION, VARIANCE} → COVARIANCE → CORRELATION
- COVARIANCE → COVARIANCE_MATRIX → {PCA, MULTIVARIATE_GAUSSIAN}
- {MEAN, VARIANCE} → GAUSSIAN
- PROBABILITY → {RANDOM_VARIABLE, EXPECTATION} (foundation edges)

**Source use-before-define repairs:** (a) the source's PMF-properties figure (cell 19) is opaque; the lesson states the properties (0 ≤ P ≤ 1, ΣP = 1) explicitly *before* first use. (b) The CDF-upper-limit typo (cell 26) is corrected to 1 with a correction tag. (c) The source introduces "area under the curve" (cell 21) before defining the integral; the lesson bridges "integral = accumulated area" as FOUNDATION before the conversion unit. (d) The source's covariance-matrix formula (cell 58) is opaque; the lesson states the 2×2 matrix explicitly. (e) The source uses "eigenvector" (cell 59) without re-deriving it; the lesson reuses Class 2's one-line meaning (a direction a matrix only scales) rather than assuming it.

## Examples, non-examples, and misconceptions

Examples (each anchored): dice RV (cell 10); rainfall RV (cell 11); dice PMF 1/6 (cell 17); uniform U(0,1) f=1 (cell 21); U(0,1) CDF F=x (cell 24); f(x)=2x → F=x² (cell 33); dice F(3)=1/2 (cell 37); dice E[X]=3.5 (cell 41); f=2x → E[X]=2/3 (cell 43); dice Var≈2.92 (cell 50); study-hours/speed covariance examples (cell 53); Y=X² zero-covariance example (cell 55).

Non-examples (each distinction the source draws): a discrete value's probability is not a density (P(X=3)=1/6 vs f(x) at a point); for a continuous RV a single point has probability 0 (P(X=x)=0), unlike the discrete case; a PDF value above 1 is legal (it is a density, not a probability) — contrast with a PMF mass, which never exceeds 1; "Cov(X,Y)=0" is not "independent" (cells 53/55).

Diagnosed misconceptions (each becomes an assessment distractor and/or alert callout):

1. **"For a continuous variable, f(x) is the probability that X = x."** Wrong: f(x) is a density; P(X=x)=0; only areas are probabilities (cells 13, 19–21).
2. **"A PDF value must be ≤ 1 because it is a probability."** Wrong: densities integrate to 1 but may exceed 1 pointwise (e.g. U(0,0.5) has f=2).
3. **"The CDF gives the probability that X equals x."** Wrong: F(x)=P(X ≤ x), the accumulated probability up to and including x (cell 23).
4. **"The CDF's upper limit is 0."** Wrong: as x→+∞, F(x)→1 (total probability); the source's cell-26 typo is corrected.
5. **"To go from PDF to CDF you differentiate; CDF to PDF you integrate."** Reversed. CDF = integral of PDF; PDF = derivative of CDF (cells 29–31).
6. **"Expectation must be an attainable value."** Wrong: E[X]=3.5 for a die is never rolled (cell 41).
7. **"Variance has the same units as X."** Wrong: variance is in squared units; the standard deviation returns to X's units (cell 50).
8. **"Cov(X,Y)=0 means X and Y are independent."** Wrong: uncorrelated ≠ independent; Y=X² around zero is the counterexample (cells 53, 55).
9. **"Correlation can be any size, like covariance."** Wrong: correlation is normalized to [−1,1] (cell 55).
10. **"The PDF is the derivative of the PMF."** Category error: PMFs and PDFs belong to different variable types; the derivative relationship is PDF ↔ CDF (cells 15–21, 29).
11. **"PCA maximizes covariance, so it maximizes variance in the units given."** Imprecise: PCA finds directions of maximum variance from the covariance matrix (cells 58–59).
12. **"A Gaussian is fully described by its mean."** Wrong: mean and variance together determine it; a multivariate Gaussian also needs the covariance (cell 61).
13. **"Discrete CDFs are smooth and continuous."** Wrong: discrete CDFs are step functions that jump by the PMF mass at each value (cell 36; contrast with the continuous F=x).
14. **"P(a ≤ X ≤ b) needs the PDF even if you have the CDF."** Wrong: the fundamental theorem gives P(a ≤ X ≤ b)=F(b)−F(a) directly (cell 32).
15. **"Summation and integration are unrelated."** Wrong: they are the discrete and continuous forms of the same accumulation (cells 36, 43).
16. **"An LLM picks the highest-probability token deterministically."** Oversimplified: it outputs a distribution and samples/generates the most probable token under the decoding scheme (cell 5).

## Ambiguities, gaps, and assumptions

- **Opaque figures (cells 8, 19, 29, 31, 58):** replaced by live or explicitly stated content in the lesson (the RV mapping, PMF properties, the two conversion formulas, and the covariance matrix), each labeled.
- **Cell-26 CDF upper-limit typo:** corrected to 1 with a `source (typo corrected)` tag.
- **Broken LaTeX splits (`x^\n2`, `F(x^\n−\n)`):** re-emitted correctly (x², F(x⁻)) with correction tags.
- **Missing derivations:** the source states the fundamental theorem and the expectation/variance results without derivations; the lesson supplies minimal FOUNDATION derivations (integrate/differentiate the toy example) so nothing is used before it is explained.
- **Assumption:** the learner completed AIML-4 Class 1 (summation, slope, accumulated-area intuition) and has the Class 2 eigenvector one-liner available; no prior probability.

## Review and acceptance criteria

All 61 cells dispositioned; every displayed number recomputed live in-page and independently in a harness (PMF 1/6, uniform f=1, CDF F=x, F(3)=1/2, E[X]=3.5, E[X²]=91/6, Var≈2.92, E[X]=2/3 for f=2x, P(0.2≤X≤0.7)=0.45 for F=x², correlation range); misconceptions shipped as distractors with per-miss feedback; at most one callout per unit; glossary covers every used term with 6 fields; the CDF↔PDF reveal arc (seeded in U1/U2, paid off in U5) closes; every forward reference names a payoff unit.

## Conformance checklist (depth-calibration contract)

- [x] ≥1 anchored atomic claim per concept (60 claims across 35 concepts)
- [x] Full dependency graph covering every prerequisite and flagging every source use-before-define case
- [x] ≥1 diagnosed misconception per major concept with wrong-answer definitions (16, distractor-ready)
- [x] Every source example anchored to cell
- [x] ≥1 non-example per conceptual distinction the source draws

