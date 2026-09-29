# LP-2026-0013: Learning plan for multivariate calculus for machine learning v2

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 2 — v2 regeneration (iteration of LP-2026-0012; preserved for the v1 lineage)  
**Owner:** Repository maintainer  
**Concept model:** [CM-2026-0012](../concepts/cm-2026-0012-multivariate-calculus.md)  
**Target learner and prerequisites:** unchanged from LP-2026-0012 (AIML-4 learner post-Classes 1–3; comfortable algebra; no prior multivariable calculus)  
**Source and claim links:** [SRC-2026-0004](../sources/src-2026-0004-multivariate-calculus.md); claims CM-2026-0012 #1–48 (unchanged from CM-2026-0011, re-verified at intake)

## Measurable learning outcomes

Unchanged outcomes 1–7 from LP-2026-0012; outcome 6 is now exercised by its own unit and assessments (Jacobian: read the matrix and its (outputs × inputs) shape, compute entries, connect to backprop), with Hessian/definiteness/Newton remaining in U6.

## Sequence and rationale

U0 Orientation → U1 Why calculus in ML (cells 3–6) → U2 Partials & the gradient, incl. gradient descent (cells 7–14) → U3 Directional derivatives (cells 15–16) → U4 Chain rule & backpropagation (cells 17–20) → **U5 The Jacobian** (cells 21–23) → **U6 Hessian & curvature** (cells 24–29) → U7 The deep-learning view (cells 30–31) → synthesis + mastery (9 items) → review list → glossary. Rationale for the v2 change: [EVAL-2026-0014](../evaluations/eval-2026-0014-multivariate-calculus-v1.md) recorded the merged Jacobian+Hessian unit as the lesson's densest and named the split as the suggested future iteration; the split also mirrors the source's own PART 6 / PART 7 boundary and gives the Jacobian its own signature visual, ladder, unit check, and mastery item. Unchanged arcs: the preview table (U1) is paid off in U2/U6; the steepest-ascent promise is asserted in U2 and proven in U3; λᵏ is seeded in U4 and paid off in U7; every forward reference names a payoff unit.

## Teaching strategy and cognitive-load choices

One visual metaphor throughout: *training is walking downhill on a surface the model can feel but cannot see*. Depth pass per unit:

| Unit | Lede | Signature visual (P-14) | Reveal arcs (P-15) | Misconception callout (≤1/unit) | Skills → ladders |
|---|---|---|---|---|---|
| U0 | Learn how the page teaches before the math starts. | Branched concept map (SVG, 16 edges) | — | — | — |
| U1 | Every model is a machine with dials; the loss is how wrong it is. | `loss-eval` canvas (W1): scatter + line + error squares, MSE live | Hand-tuning setup → payoff: calculus finds the best dials (U2); preview table → definitions in U2/U6 | "Optimization means collecting more data / bigger models" | L1 loss/MSE arithmetic |
| U2 | A partial is the slope of one dial, all others frozen. | `partial-lab` (W2) contours + gradient arrow; `descent-lab` (W3) stepped path | Steepest-ascent promise (asserted here) → proven in U3; hand-tuning payoff: descent-lab lands the U1 optimum | "The gradient is a number — the biggest partial" | L2 partials (freeze-and-differentiate) |
| U3 | The gradient's component along any direction is that direction's climb rate. | `direction-lab` (W4): gradient + dial + projection bar | U2 promise paid off (max D_u f = ‖∇f‖ via cos φ); flat-perpendicular → plateaus (U7) | "Unnormalized u = (3,4) gives 25, the max" | L3 directional-derivative arithmetic |
| U4 | Deep nets are nested functions; gradients flow backward by multiplying local derivatives. | `graph-lab` (W5): computational graph, forward values + backward derivatives | Cell-18 "gradients must flow backward" → live backward pass; λᵏ seeded for U7 | "Backprop is a new algorithm unrelated to calculus" | L4 chain-rule products |
| U5 | One row per output: the derivative of a many-output function is a matrix. | `jacobian-lab` (W6, new): live 2×2 linear map of the unit grid; columns are basis images; determinant = area scale | Preview-table Jacobian row → real definition here; JAC→BP arc connects to U4/U7 | "The Jacobian's shape is (inputs × outputs)" | L5 Jacobian entries |
| U6 | Second order says shape: curvature decides floor, ceiling, or pass. | `curv-lab` (W7): two live parabola cross-sections + definiteness classifier | Preview-table Hessian row → real definition here; Newton one-step landing for quadratics | "∇f = 0 means we found a minimum" | L6 Hessian entries & classification |
| U7 | Repeat the chain rule 100 times and small factors compound. | `chain-depth` (W8, numeric by stated reason): λᵏ live with vanish/explode thresholds | λᵏ (U4 seed) → vanishing/exploding paid off; flat-perpendicular (U3) → plateaus; adaptive optimizers as the response | "Vanishing gradients come from subtraction" | L7 exponential factors λᵏ |

Prediction gates (3, unchanged in design; G3 retargeted after the split): G1 in U2 (which nudge raises f fastest — correct: the gradient direction), G2 in U3 (max D_u f for ∇f=[3,4] — correct: 5 along (3,4)/5), G3 in **U6** (Hessian eigenvalues +4/−2 — correct: saddle; unlocks the curvature lab W7). Gates hide the manipulable until commitment; per-option feedback differentiated; governing rule stated in every feedback.

Explain-in-own-words items (≥2, unchanged): U2 "why the negative gradient points fastest downhill" and U4 "why backpropagation is just the chain rule", both with model-answer reveals and honest self-evaluation, inside the unit Check blocks.

Mastery: **9 items** (7 content units + 2), interleaved, 3-level confidence tags, confident misses routed to the review list. M1–M8 carry over from LP-2026-0012 (M6's reference updated to U6); **M9** (new): a Jacobian entry J₁₂ of (xy², x²y) at (2,3) → 12. Includes reasoning, transfer, and error-identification items; no worked numbers reused.

Additional-knowledge triage: unchanged (must-add bridges MSE, dot-product projection, eigenvalue one-liner, second-order approximation, λᵏ; should-add one-line adaptive-optimizer mechanism and stochastic-gradient statement; EXTENSION-collapsed automatic-diff internals, momentum, non-convexity proofs; do-not-add KKT, convergence proofs, transformer internals, numerical H⁻¹). The W6 lab is a constructed supplement to claims 32–35 (tagged constructed; defaults reproduce the source's matrix).

Calibration: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) remains the depth exemplar; the implementation reference is now the Class 4 v1 artifact (CAN-2026-0013, `multivariate-calculus-v1.html`) as the nearest governed component-contract reference.

## Assessment and evidence of learning

Every unit check has ≥1 constructed-response numeric item plus ≥1 diagnostic MCQ with per-option feedback — checks c1–c7: MSE, partials, directional derivative, chain rule, **Jacobian (new c5: J₂₁ = 6; indexing MCQ)**, Hessian (renumbered c6), exponential factors (renumbered c7). Ladders L1–L7, three rungs each (worked → completion → independent), tiered never-auto-opening hints (**L5 new**: J₁₂ = 9; J₂₁ = 0). Persistence unchanged: cleared checks fill nav dots; misses and confident mastery misses enter the `mvc2-*` localStorage review list with a spacing invitation and visible reset; graceful fallback when storage is unavailable; corrupted-storage recovery verified.

## Accessibility and inclusion intent

Unchanged from LP-2026-0012 (native controls, keyboard operability, per-canvas text equivalents, legends, reduced motion, print fallback, measured AA contrast, 16px floor). v2 additions: the Jacobian lab ships a two-panel canvas text equivalent, four labeled sliders, an inline legend, and a same-numbers readout; the W1 canvas viewport is tightened to y ∈ [−1, 10] (aspect ratio 1.167 → 0.917, ≈21% shorter) per the EVAL-2026-0014 observation, keeping every data point and the least-squares optimum visible.

## Acceptance criteria and review boundary

Strict mechanical verification (`verify-candidate.py`, 0 failures); independent Python recomputation (118 checks, 0 failures); Node behavioral harness (48 checks, 0 failures); dependency-order read-through; six audits + adversarial gate ([ADR-0009](../../docs/adr/0009-forced-adversarial-re-examination-gate.md)); live rendered verification at 320/640/1024px with 0 console errors ([ADR-0010](../../docs/adr/0010-rendered-output-verification.md)); repository checker exit 0. Disposition `private-pilot-complete`; non-independent; release-ineligible.

## Conformance checklist (depth-calibration contract)

- [x] Active benchmark BMK-2026-0001 cited as calibration exemplar
- [x] Depth-pass table complete for every unit (lede, signature visual, reveal arcs with payoff units, misconception callouts, ladders)
- [x] One full 3-rung faded ladder for each of the 7 computational skills (L1–L7)
- [x] ≥2 explain-in-own-words items with model-answer reveals allocated (U2, U4)
- [x] Every forward promise / reveal arc names its explicit payoff unit

