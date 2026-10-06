# SRC-2026-0005: Probability basics (with CDF ↔ PDF conversion)

**Status:** Recorded  
**Owner:** Repository maintainer  
**Content package:** [AIML-4 Module 2](../../content/aiml-4/module-02-math-statistics-for-ml/README.md)  
**Version:** 1.0

## Source identity

**Source file:** [Probability_Basics_(with_CDF_↔_PDF_Conversion).ipynb](../../content/aiml-4/module-02-math-statistics-for-ml/sources/Probability_Basics_%28with_CDF_↔_PDF_Conversion%29.ipynb)  
**SHA-256:** `837a1736e4286cf6b8b0d91792dd6611162dfb811332860a5dfca67fc60fd0ac`  
**Language and scope:** English; AIML-4 Module 2 (Class 5) probability basics — probability as the language of uncertainty with real ML examples (LLM next-token, fraud detection, recommendation), random variables (discrete vs continuous), PMF, PDF, and CDF, the CDF ↔ PDF conversion (fundamental theorem, geometric understanding), expectation, variance, covariance, and ML connections (PCA, Gaussian models).  
**Sensitive-content flags:** None known.

## Citation anchors

The notebook is `nbformat` 4 with 61 cells (all Markdown; zero code cells, so no recorded executions exist). Claims are anchored by one-based cell ordinal and visible heading:

- Cells 1–2: title and agenda (Probability Basics + real ML examples; Random Variables + types; PMF/PDF/CDF; CDF ↔ PDF conversion; Expectation; Variance; Covariance; ML connections — PCA, Gaussian models). Core learning outcomes listed in cell 5.
- Cell 3: probability is the mathematical language of uncertainty; ML makes probabilistic predictions; the four motivating questions (spam, fraud, next token, click).
- Cells 4–5: real ML examples — LLM next-token distribution with a small token/probability table (world 0.41, everyone 0.22, people 0.18), fraud detection P(Fraud|features) with example scores 0.02 / 0.95, recommendation systems P(User Likes Item); core learning outcomes.
- Cells 6–11: random variables — mapping outcomes to numbers; formal definition X: Ω → ℝ as an opaque inline base64 PNG (cell 8) with the surrounding prose naming Ω (sample space) and ℝ; dice-roll example (Ω = {1..6}); rainfall example (X ∈ [0, ∞), continuous).
- Cells 12–13: types of random variables — discrete (countable; dice, customers, emails, defects; P(X=3) meaningful) vs continuous (infinitely many values; height, weight, temperature, time, voltage; P(X=x)=0; instead P(a ≤ X ≤ b) matters).
- Cells 14–15: PMF/PDF/CDF framing — distributions describe how probability is distributed.
- Cells 16–19: PMF — used for discrete variables; P(X=x); dice P(X=x)=1/6 for x ∈ {1..6}; PMF properties shown only as an opaque base64 PNG (cell 19).
- Cells 20–21: PDF — used for continuous variables; f(x); probability is area under the curve; f(x) ≠ P(X=x); uniform U(0,1) has f(x)=1 on [0,1].
- Cells 22–26: CDF — works for both discrete and continuous; F(x)=P(X≤x); accumulated probability; U(0,1) example F(x)=x (x=0.2 → 20%, x=0.7 → 70%); properties: increasing F(a)≤F(b) for a<b; range 0≤F(x)≤1; right-continuous; limits (cell 26 states the upper limit as lim_{x→+∞} F(x)=0, a transcription error — the correct value is 1, dispositioned in the CM).
- Cells 27–33: CDF ↔ PDF conversion — PDF is local density, CDF is accumulated probability; CDF is the area under the PDF and PDF is the slope/derivative of the CDF (F(x)=∫_{−∞}^{x} f; reverse f = dF/dx, shown as base64 images in cells 29 and 31); fundamental theorem P(a ≤ X ≤ b) = F(b) − F(a) = ∫_a^b f(x) dx; worked example f(x)=2x on [0,1] → F(x)=x², F(1)=1 verified, d/dx(x²)=2x recovers the PDF.
- Cells 34–39: geometric understanding (PDF height = density, area = probability, CDF = accumulated area); discrete case F(x)=P(X≤x) by summation; dice F(3)=1/2; recovering the PMF P(X=x)=F(x)−F(x⁻) via the left limit.
- Cells 40–46: expectation — long-run average / probability-weighted average; dice E[X]=3.5 (not an attainable outcome); discrete E[X]=Σ x P(X=x) and continuous E[X]=∫ x f(x) dx; example f(x)=2x → E[X]=2/3; properties: linearity E[aX+b]=aE[X]+b, E[c]=c, sum rule E[X+Y]=E[X]+E[Y] (true even if dependent); ML interpretation (mean prediction, average reward, average loss, expected risk/return).
- Cells 47–51: variance — spread/uncertainty; Var(X)=E[(X−μ)²] with μ=E[X]; computational formula Var(X)=E[X²]−(E[X])²; dice E[X²]=91/6 → Var ≈ 2.92; standard deviation σ=√Var in original units; ML interpretation (instability, sensitivity) and the bias–variance tradeoff (high bias → underfitting, high variance → overfitting).
- Cells 52–55: covariance — Cov(X,Y)=E[(X−E[X])(Y−E[Y])]; interpretation table (positive / negative / zero); study-hours–scores and speed–travel-time examples; the key insight Cov(X,Y)=0 does not imply independence (Y=X² symmetric example); correlation Corr(X,Y)=Cov(X,Y)/(σ_X σ_Y) with range [−1,1].
- Cells 56–61: ML connections — PCA uses the covariance matrix to find directions of maximum variance, with the covariance-matrix formula shown as an opaque base64 image (cell 58) and eigenvectors giving the principal components; Gaussian models depend on mean and variance, and a multivariate Gaussian additionally uses the covariance.

**Transcription artifacts:** cells 8, 19, 29, 31, and 58 are opaque inline base64 PNG figures (a random-variable mapping diagram, PMF properties, the CDF-as-integral and PDF-as-derivative formulas, and the covariance-matrix formula respectively); the intended content is recoverable from surrounding prose and is emitted live/correctly in the lesson. Several LaTeX fragments carry broken line splits (e.g. `x^\n2`, `F(x^\n−\n)`); the intended formulas are recoverable and are emitted correctly with correction tags. Cell 26's CDF upper-limit typo is corrected to 1. No code outputs exist to recompute.
