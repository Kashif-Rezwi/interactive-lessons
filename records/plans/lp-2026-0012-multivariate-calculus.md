# LP-2026-0012: Learning plan for multivariate calculus for machine learning v1

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 1 — original  
**Owner:** Repository maintainer  
**Concept model:** [CM-2026-0011](../concepts/cm-2026-0011-multivariate-calculus.md)  
**Target learner and prerequisites:** AIML-4 learner who completed Class 1 (vectors, dot products, norms, slope of a line, function notation), Class 2 (matrix/eigenvalue vocabulary), and Class 3 (high-dimensional space vocabulary); comfortable with algebra; no prior multivariable calculus  
**Source and claim links:** [SRC-2026-0004](../sources/src-2026-0004-multivariate-calculus.md); claims CM-2026-0011 #1–48

## Measurable learning outcomes

The learner can: (1) explain why training an ML model is an optimization problem over a high-dimensional parameter space and compute a concrete loss (MSE) for given parameters on a small dataset; (2) compute partial derivatives of multivariable functions, assemble the gradient vector, and interpret each partial as one axis's slope and as the loss's sensitivity to one parameter; (3) apply the gradient-descent update θ := θ − η∇f, predict the effect of the learning rate (including the overshoot threshold on a quadratic), and trace a full descent trajectory; (4) compute directional derivatives D_u f = ∇f·u for unit directions, use the projection argument to prove why the gradient is the steepest-ascent direction, and explain why the perpendicular direction is first-order flat; (5) apply the single-variable chain rule through a computational graph, multiply local derivatives along a path (backward pass), and explain backpropagation as repeated chain rule; (6) read a Jacobian and its (outputs × inputs) shape, compute Hessian entries, classify critical points via definiteness (bowl / dome / saddle), and explain Newton's method and its guard conditions; (7) predict exponential vanishing/exploding of repeated chain-rule factors (λᵏ) and connect landscape challenges and adaptive optimizers to the calculus of Units 2–5.

## Sequence and rationale

U0 Orientation (how to learn with the page, labels, loop, concept map) → U1 Why calculus in ML (optimization, loss as function of parameters; live MSE tuning) → U2 Partials & the gradient (freeze-and-differentiate, gradient vector, steepest-ascent promise, gradient descent and the learning rate) → U3 Directional derivatives (projection, the max is ‖∇f‖ — pays off U2's promise; the flat perpendicular) → U4 Chain rule & backpropagation (nested compositions, computational graphs, repeated chain rule) → U5 Jacobian, Hessian & curvature (first-order matrix generalization, second-order curvature, definiteness and saddles, Newton's method) → U6 The deep-learning view (vanishing/exploding gradients as λᵏ, landscape challenges, adaptive optimizers, large-scale training) → Synthesis + mastery → review list → glossary. Rationale: the source's geometric table (cell 6) is a *preview* that the lesson keeps but labels as a preview — gradient and Hessian get real definitions in U2/U5, exactly repairing the source's use-before-define ordering; the steepest-ascent property is asserted in U2 (as in cell 12) but *proven* in U3 via the projection argument (cell 16's insight), an explicit promise-and-payoff arc; the Jacobian is placed after the chain rule because its role in backpropagation is the reason it exists; the advanced-ML section closes the loop by re-using λᵏ arithmetic that the U6 widget grounds live. Application names (normalizing flows, diffusion, Adam) appear only after the machinery they use.


## Teaching strategy and cognitive-load choices

One visual metaphor throughout: *training is walking downhill on a surface the model can feel but cannot see — partials are one-direction tilts, the gradient is the felt steepest direction, curvature is whether the ground bends*. Depth pass per unit:

| Unit | Lede | Signature visual (P-14) | Reveal arcs (P-15) | Misconception callouts (≤1/unit) | Computational skills → ladders |
|---|---|---|---|---|---|
| U0 | Learn how the page teaches before the math starts. | Branched concept map (SVG) | — | — | — |
| U1 | Every model is a machine with dials; the loss is how wrong it is. | `loss-eval` canvas: scatter + line + squared-error squares, MSE live | Hand-tuning setup → payoff in U2 (calculus finds the best dials automatically) | "Optimization means collecting more data / bigger models" | L1 loss/MSE arithmetic |
| U2 | A partial is the slope of one dial, all others frozen. | `partial-lab` contour canvas with gradient arrow + `descent-lab` stepped path | Steepest-ascent promise (asserted here) → proven in U3; hand-tuning payoff: descent-lab lands the U1 optimum | "The gradient is a number — the biggest partial" | L2 partials (freeze-and-differentiate) |
| U3 | The gradient's component along any direction tells how fast you climb that way. | `direction-lab` canvas: gradient + dial direction + projection bar | U2 promise paid off: max D_u f = ‖∇f‖ with the cos φ argument; flat-perpendicular → plateaus (U6) | "Unnormalized u=(3,4) gives 25, the max" | L3 directional-derivative arithmetic |
| U4 | Deep nets are nested functions; gradients flow backward by multiplying local derivatives. | `graph-lab` canvas: computational graph with forward values and backward derivatives | Cell-18 "gradients must flow backward" → paid off immediately by the live backward pass; λᵏ seeded for U6 | "Backprop is a new algorithm unrelated to calculus" | L4 chain-rule products |
| U5 | The Hessian is the tilt of the tilt — it tells the ground how to bend. | `curv-lab` canvas: two live parabola cross-sections + definiteness classifier | Geometric-table preview (U1) → curvature gets its real definition here; Newton one-step landing for quadratics | "∇f=0 means we found a minimum" | L5 Hessian entries & eigenvalue classification |
| U6 | Repeat the chain rule 100 times and small factors compound into vanishing or exploding gradients. | `chain-depth` numeric lab: λᵏ live with vanish/explode thresholds | Flat-perpendicular promise (U3) → plateaus explained; λᵏ (U4 seeded) → vanishing/exploding paid off; adaptive optimizers as the ML response | "Vanishing gradients come from subtraction" | L6 exponential factors λᵏ |

Prediction gates: G1 in U2 (which nudge at a point of f = x²+2y² raises f fastest per unit step: +x / +y / the gradient direction — options a/b/c, correct: the gradient direction), G2 in U3 (∇f=[3,4]: largest possible D_u f over unit u and along which u — options "25 along (3,4)" / "5 along (3,4)/5" / "3 along the x-axis", correct: 5 along the unit gradient), G3 in U5 (critical point with Hessian eigenvalues +4 and −2 — options "local minimum" / "saddle point" / "local maximum", correct: saddle). Gates hide the manipulable until commitment; per-option feedback differentiated by choice; governing rule stated in every feedback.

Explain-in-own-words items (≥2, with model-answer reveals and self-evaluation, no textareas): U2 "why does the negative gradient point in the fastest downhill direction" and U4 "why is backpropagation just the chain rule". Explain-item placement is inside the unit Check blocks.

Mastery check: 8 items (≈ 6 content units + 2), interleaved across units, with 3-level confidence tags (sure / think so / guessing) and confident misses routed to the persistent review list; includes reasoning items (why opposite the gradient; GD behavior at a saddle; multiplicative vs additive decay), transfer items (a 3-D directional derivative; a Jacobian shape question for an R⁴ → R⁷ layer; new functions), and one error-identification item (a teammate misclassifies a positive-definite critical point as a maximum and proposes hunting for an indefinite Hessian instead). No worked numbers reused.

Additional-knowledge triage: must-add bridges — MSE as a concrete loss (EQ-013), dot-product projection (Class 1 reuse), eigenvalue one-line bridge (Class 2 reuse), second-order approximation f(θ+δ) ≈ f(θ)+∇f·δ+½δᵀHδ (why definiteness classifies), exponential scaling λᵏ (vanishing/exploding). Should — one-line adaptive-optimizer mechanism; one-line stochastic-gradient statement. Could (collapsed EXTENSION) — automatic differentiation internals; momentum; non-convexity proofs. Do-not-add — KKT conditions, convergence proofs, transformer internals, numerical linear algebra for H⁻¹.

Calibration: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) is the active depth exemplar; the Class 3 v1 lesson (CAN-2026-0012) is the implementation reference for component contracts and live-computation patterns.

## Assessment and evidence of learning

Every unit check has ≥1 constructed-response numeric item (auto-graded with tolerance) plus at least one diagnostic MCQ with per-option misconception feedback; feedback on every miss states the governing rule. Ladders L1–L6 each have 3 rungs with tiered, never-auto-opening hints. Mastery M1–M8 with confidence routing. Persistence: cleared checks fill nav completion dots; misses and confident mastery misses enter a localStorage review list with a spacing invitation and visible reset (graceful fallback when storage is unavailable).

## Accessibility and inclusion intent

Native controls only; keyboard-operable sliders/options; every canvas pairs a text readout with the same numbers and a `.legend-inline` legend; color never the sole encoder; `prefers-reduced-motion` honored; measured WCAG AA contrast; print fallback exposes explanations and hides controls; 16px font floor at all breakpoints.

## Acceptance criteria and review boundary

Strict mechanical verification (`verify-candidate.py`, 0 failures); independent Python recomputation of every displayed number and answer key; Node cross-check of the page's live JS math core; dependency-order read-through; six audits + adversarial gate per ADR-0009; rendered browser verification at 320/640/1024px per ADR-0010; repository checker exit 0. Status remains private-pilot-complete, non-independent, ineligible for public release.

## Conformance checklist (depth-calibration contract)

- [x] Active benchmark BMK-2026-0001 cited as calibration exemplar
- [x] Depth-pass table complete for every unit (lede, signature visual, reveal arcs with payoff units, misconception callouts, ladders per skill)
- [x] One full 3-rung faded ladder planned for each of the 6 computational skills (L1–L6)
- [x] ≥ 2 explain-in-own-words items with model-answer reveals allocated (U2, U4)
- [x] Every forward promise / reveal arc names its explicit payoff unit

