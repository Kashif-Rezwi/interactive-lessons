# CM-2026-0011: Multivariate calculus for machine learning (v1 concept model)

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 1 — original  
**Owner:** Repository maintainer  
**Source package:** [SRC-2026-0004](../sources/src-2026-0004-multivariate-calculus.md)  
**Domain review status:** Reviewed by the same operator; non-independent  
**Confidence:** high

**Cross-lesson continuity:** This lesson depends on Class 1 concepts (vectors, dot products, norms, slope of a line, function notation — CM-2026-0007), Class 2 concepts (eigenvalues, matrix vocabulary — CM-2026-0009), and Class 3 vocabulary (high-dimensional space, concentration — CM-2026-0010). The artifact links back to the governed Class 1 (`linear-algebra-foundations-v10.html`), Class 2 (`matrix-decompositions-applications-v2.html`), and Class 3 (`high-dimensional-geometry-v1.html`) lessons where those concepts reappear but are not re-derived.

## Scope and learning boundary

The lesson reorganizes the 31-cell source into an orientation unit plus six dependency-ordered units: why ML is optimization (loss as a function of many parameters), partial derivatives, the gradient and gradient descent, directional derivatives, the chain rule and backpropagation, and the second-order view (Jacobian, Hessian, curvature, saddles, Newton's method) plus the advanced ML perspective (deep networks, vanishing/exploding gradients, adaptive optimizers). It adds only FOUNDATION bridges the source assumed: mean-squared-error as a concrete loss, the dot-product definition of projection, eigenvalues as "curvature along principal directions" (reused from Class 2, one-line bridge), the second-order/Taylor view f(θ+δ) ≈ f(θ)+∇f·δ+½δᵀHδ behind the definiteness classification, and exponential growth/decay λᵏ behind vanishing/exploding gradients. It does not teach automatic-differentiation internals, convergence proofs, Lagrangians/KKT conditions, momentum/Nesterov derivations, or transformer architecture — those are named, bridged in one line, and bounded as EXTENSION or ML LINK context.

## Concepts and definitions

| Concept | Definition | Source anchor |
|---|---|---|
| ML as optimization | A model learns by adjusting parameters to minimize a loss | Cells 3–4 |
| Loss function | A number measuring prediction error; examples: classification, regression, cross-entropy, reconstruction | Cell 4 |
| Parameter | A trainable number the model adjusts (weights, biases) | Cells 4, 6 |
| High-dimensional parameter space | The space of all parameter settings; modern nets have millions–billions of axes | Cell 6 |
| Loss surface | Geometric reading: loss is a surface/hypersurface over parameters | Cells 6, 27 |
| Partial derivative | Rate of change of f w.r.t. one variable, all others held fixed | Cell 8 |
| Freezing variables | Computing ∂f/∂x means treating y (etc.) as a constant | Cell 8 |
| Slope along one direction | A partial measures the tilt along one axis of the surface | Cells 8–9 |
| Sensitivity ∂L/∂wᵢ | How strongly parameter i affects the loss; large = strong effect | Cell 9 |
| Gradient | The vector of all partial derivatives ∇f = [∂f/∂x, ∂f/∂y, …] | Cell 12 |
| Steepest ascent property | The gradient points in the direction of fastest increase | Cells 6, 12 |
| Negative gradient | Points in the direction of fastest decrease | Cells 6, 12 |
| Gradient magnitude | ‖∇f‖ measures how steep the surface is locally | Cell 12 |
| Learning rate η | Step-size scalar controlling how far each update moves | Cell 12 |
| Gradient descent | Iterative update θ := θ − η∇f(θ) | Cell 12 |
| Directional derivative | Rate of change along any unit direction u: D_u f = ∇f·u | Cell 16 |
| Projection | D_u f is the gradient's component along u (dot product) | Cell 16 |
| Maximum directional derivative | Occurs when u aligns with ∇f; value ‖∇f‖ | Cell 16 |
| Chain rule (single variable) | For y = f(g(x)): dy/dx = dy/dg · dg/dx | Cell 18 (source formula `dy/dg = dg/dx` corrected) |
| Function composition | Nested functions; deep nets are chains of compositions | Cell 18 |
| Computational graph | Nodes = quantities, edges = dependencies; organizes forward values and backward derivatives | Cell 18 |
| Backpropagation | Repeated application of the chain rule through the graph, layer by layer | Cell 18 |
| Forward / backward pass | Compute values (and loss) forward; propagate derivatives backward | Cell 18 |

| Jacobian | Matrix J_ij = ∂f_i/∂x_j of a vector-valued function; shape (output × input) | Cell 22 |
| Vector-valued function | F(x) = [f₁(x), …, f_m(x)]; maps inputs to several outputs | Cell 22 |
| Local transformation meaning | Jacobian describes local stretch/scale/rotation near a point | Cell 22 |
| Hessian | Matrix of second-order partials H_ij = ∂²f/∂xᵢ∂xⱼ; symmetric when mixed partials match | Cell 25 |
| Curvature | Second derivative measures how the slope itself changes (bending) | Cell 25 |
| Definiteness | Positive definite → bowl (local min); negative definite → dome (local max); indefinite → saddle | Cell 25 |
| Saddle point | Critical point with mixed curvature: up in some directions, down in others | Cells 25, 27 |
| Newton's method | Second-order update θ := θ − H⁻¹∇f, using curvature to size the step | Cell 25 |
| Vanishing / exploding gradients | Repeated chain-rule multiplication by factors <1 or >1 shrinks/grows gradients exponentially | Cell 31 |
| Non-convex landscape | Deep-net loss surfaces contain plateaus, cliffs, and many saddles | Cell 31 |
| Adaptive optimizers | Adam, RMSProp, Adagrad scale per-parameter steps using gradient statistics | Cell 31 |
| Stochastic gradients | Mini-batch/noisy gradient estimates for large-scale training | Cell 31 |

## Atomic claims (anchored; ≥1 per concept)

1. A model learns by minimizing error (cell 4); 2. loss families: classification, regression, cross-entropy, reconstruction (cell 4); 3. linear-regression loss depends on parameters w₁, w₂, b (cell 4); 4. modern networks have millions–billions of parameters (cell 6); 5. training navigates a high-dimensional surface (cell 6); 6. loss ↔ surface, gradient ↔ steepest ascent, negative gradient ↔ fastest descent, Hessian ↔ curvature (cell 6 table); 7. a partial derivative is the rate of change w.r.t. one variable holding others fixed (cell 8); 8. for f = x²+3y: ∂f/∂x = 2x and ∂f/∂y = 3 (cell 8); 9. at (2,4) the partials are 4 and 3 (cell 10); 10. a partial is the slope along one frozen direction (mountain east-west vs north-south) (cell 8); 11. partials describe the local tilt and directional steepness of z=f(x,y) (cell 9); 12. ∂L/∂wᵢ measures the sensitivity of the loss to parameter i (cell 9); 13. large partial → strong local effect; small partial → weak effect (cell 9); 14. the gradient stacks all partials into a vector (cell 12); 15. the gradient points in the direction of steepest increase (cell 12); 16. the negative gradient points downhill fastest (cells 6, 12); 17. ‖∇f‖ measures local steepness; large = steep, small = flat (cell 12); 18. gradient descent updates θ := θ − η∇f(θ) (cell 12); 19. from x=5 with η=0.1 on f=x², twenty steps land at ≈0.0576 (cell 14, recomputed live); 20. the directional derivative along unit u is D_u f = ∇f·u (cell 16); 21. it answers "how fast does f change if I move in THIS direction" (cell 16); 22. it projects the gradient onto the chosen direction (cell 16); 23. the maximum directional derivative occurs along the gradient, with value ‖∇f‖ (cell 16); 24. for ∇f=[3,4], ‖∇f‖ = 5 (cell 16); 25. deep learning chains nested compositions: input→layer→activation→…→loss (cell 18); 26. gradients must flow backward through the composition (cell 18); 27. for y=f(g(x)), dy/dx = dy/dg·dg/dx (cell 18, source formula corrected); 28. the chain rule propagates derivatives through the computational graph layer by layer (cell 18); 29. backpropagation is repeated chain rule (cell 18); 30. without the chain rule deep learning cannot exist (cell 18); 31. for x=2, g=x², y=g+1: dy/dx = 4 (cell 20, recomputed live); 32. the Jacobian collects all first-order partials of a vector-valued function (cell 22); 33. J_ij = ∂f_i/∂xⱼ; shape is (outputs × inputs) — the 3-output/2-input example is 3×2 (cell 22); 34. the Jacobian describes local stretching, scaling, rotation (cell 22); 35. Jacobians are used in backpropagation, normalizing flows, diffusion models, sensitivity analysis (cell 22); 36. the Hessian collects second-order partials H_ij = ∂²f/∂xᵢ∂xⱼ (cell 25); 37. positive curvature = bowl, negative = dome, mixed = saddle (cell 25 table); 38. positive definite → local minimum, negative definite → local maximum, indefinite → saddle (cell 25); 39. deep-learning landscapes contain many saddle points and flat plateaus, making optimization hard (cell 25); 40. Newton's method uses θ := θ − H⁻¹∇f for faster optimization (cell 25); 41. the gradient gives direction, the Hessian gives shape (cell 27); 42. valley = minimum, peak = maximum, saddle = mixed curvature (cell 27 table); 43. deep nets are highly non-convex with billions of parameters (cell 31); 44. repeated chain rule makes gradients shrink or explode exponentially (cell 31); 45. this creates unstable training (cell 31); 46. loss landscapes contain flat regions, steep cliffs, saddle points (cell 31); 47. Adam/RMSProp/Adagrad use gradient statistics and adaptive scaling (cell 31); 48. large-scale optimization uses distributed systems, stochastic gradients, noisy updates, curvature-aware methods (cell 31).


## Dependency graph and prerequisite flags

OPT (ML as optimization) → LOSS (loss over parameters) → PD (partials; needed because loss has many variables) → GRAD (gradient = stacked partials) → {GD (gradient descent needs the gradient), DD (directional derivative needs the gradient and dot product)}; GRAD → JAC (Jacobian generalizes the gradient to vector outputs); GRAD+DD → HES-precondition (the steepest-ascent claim is *explained* by DD's dot-product argument — payoff arc); HES (Hessian/curvature) → {SADDLE (definiteness classification), NEWT (Newton's method)}; LOSS+CR (chain rule) → BP (backpropagation); CR → DEEP (repeated chain rule → vanishing/exploding); SADDLE+GD → DEEP (landscape challenges, adaptive optimizers). FOUNDATION bridges required: MSE (for a concrete loss), dot product (Class 1, reused), eigenvalue (Class 2, one-line bridge: for a diagonal Hessian the eigenvalues are the diagonal entries), second-order approximation f(θ+δ) ≈ f(θ)+∇f·δ+½δᵀHδ (for why definiteness classifies critical points), exponential scaling λᵏ (for vanishing/exploding). Source use-before-define cases repaired: the source uses the geometric table (gradient/Hessian names, cell 6) before defining them (cells 12, 25) — the lesson keeps the table as a *preview* labeled as such, with definitions arriving in U2/U5; the source states the steepest-ascent property (cell 12) before the projection argument that explains it (cell 16) — kept as an explicit promise paid off in U3.

## Examples and non-examples

Examples: f=x²+3y partials (cell 8); (2,4) partials = 4, 3 (cell 10); gradient-descent trajectory 5 → ≈0.0576 (cell 14); ∇f=[3,4] with ‖∇f‖=5 (cell 16); chain-rule product at x=2 → 4 (cell 20); Jacobian [[2,1],[0,3]] (cell 23); linear regression L(w₁,w₂,b) (cell 4). Non-examples: the gradient is NOT a single number (it is a vector — contrast with "the biggest partial"); a partial is NOT the total change (only the change along one axis); the gradient is NOT a descent direction (its negative is); D_u f is NOT ∇f (it is the projection — a number); the Jacobian is NOT the Hessian (first vs second order); a critical point is NOT automatically a minimum (the Hessian decides); λᵏ decay is NOT subtraction (per-layer factors multiply).

## Diagnosed misconceptions (distractor-ready, with wrong-answer definitions)

1. "The gradient is the largest partial derivative (a number)" → misses that the gradient is the vector of all partials.
2. "A partial derivative changes only one variable's value" → confuses the operation (freeze others mathematically) with moving in the space.
3. "At a critical point (∇f=0) we found a minimum" → misses that curvature decides; saddles are critical too.
4. "Hessian eigenvalues +5, −3 means a shallow minimum" → mixed signs = saddle, not minimum.
5. "A bigger learning rate always converges faster" → misses the overshoot/divergence threshold (η < 2/λ_max for a quadratic).
6. "Gradient descent moves along the gradient" → sign error: it moves opposite.
7. "The directional derivative requires u to be the gradient" → any unit direction works; it is a projection.
8. "D_u f is maximized by u = ∇f (unnormalized)" → u must be a unit vector; the max value is ‖∇f‖ (the unnormalized (3,4) dot gives 25, not 5).
9. "Perpendicular to the gradient, f still rises (just slower)" → it is flat to first order (D_u f = 0).
10. "The chain rule adds the local derivatives" → they multiply.
11. "Backpropagation is a separate algorithm unrelated to calculus" → it is repeated chain rule on the computational graph.
12. "The Jacobian's shape is (inputs × outputs)" → it is (outputs × inputs).
13. "The Hessian is the matrix of first derivatives" → that is the Jacobian; the Hessian is second order.
14. "Newton's method always works because it uses curvature" → H⁻¹ must exist and the local quadratic must be a good model (a saddle's H⁻¹ points somewhere unhelpful).
15. "Vanishing gradients come from subtracting something at each layer" → repeated multiplication by factors <1 shrinks exponentially.
16. "A flat region has gradient exactly zero" → it is *near* zero; tiny gradients mean tiny steps, hence plateaus stall training.


## Ambiguities, gaps, and assumptions

- Cell 18's written chain-rule formula `dy/dg = dg/dx` is mathematically false (it equates two unrelated derivatives); the intended statement dy/dx = dy/dg·dg/dx is recovered from context and the cell-20 code (which correctly multiplies dy_dg·dg_dx), emitted correctly, and tagged as an artifact correction.
- The agenda (cell 2) lists PART 1–8 then PART 10; the body's advanced-ML section is labeled PART 9 (cell 30). Disposition: one section (advanced ML perspective); numbering inconsistency recorded, no content lost.
- Cells 5 and 29 are opaque inline base64 PNGs (a linear-regression fit and a 3-D loss surface) with no axes, labels, or captions; both are non-reconstructable as-is and are replaced by live, labeled canvases (the U1 loss explorer, the U2 contour labs, and the U5 curvature lab), recorded as intentional replacements, not copies.
- All four code cells have cleared outputs; the lesson recomputes each live (cell 10 → 4, 3; cell 14 → the 5·0.8²⁰ ≈ 0.0576 trajectory; cell 20 → 4; cell 23 → the matrix, shown as a live transformation on a test vector).
- Cell 12's update is written θ:=θ−η∇f(θ); the lesson keeps the notation and adds the plain-language reading and step-size intuition the source leaves implicit (labeled supplemental).
- Cell 25's Newton update needs H⁻¹ to exist; the lesson adds the guard note (invertibility + local-model validity), tagged supplemental — the source presents Newton's method unconditionally.
- Cell 16's "maximum change occurs along the gradient" is asserted but not argued; the lesson proves it via the projection argument (D_u f = ‖∇f‖cos φ ≤ ‖∇f‖), tagged supplemental, paying off the U2 promise.
- The source names Adam/RMSProp/Adagrad without mechanisms; the lesson gives a one-line mechanism (per-parameter adaptive scaling from gradient statistics) and bounds the rest as EXTENSION.
- The source's "Hessian tells whether the surface curves upward/downward" (cell 25) is direction-dependent (a saddle curves both ways); the lesson states the per-direction version and uses definiteness as the classifier, tagging the tightening.
- Assumption: the learner completed AIML-4 Classes 1–3 (vectors, dot products, norms, function graphs; eigenvalue vocabulary; high-dimensional space). Links point to the governed lessons where those are taught.

## Review and acceptance criteria

All 31 source cells dispositioned in the coverage matrix; every displayed number recomputed live in-page or independently verified in Python; the chain-rule formula correction and both figure replacements tagged; misconceptions appear as distractors with per-miss feedback; at most one callout per unit; glossary covers every used term with 6 fields; the steepest-ascent promise is paid off explicitly.

## Conformance checklist (depth-calibration contract)

- [x] ≥ 1 anchored atomic claim per concept (48 claims across 35 concepts)
- [x] Full dependency graph covering every prerequisite and flagging every source use-before-define case
- [x] ≥ 1 diagnosed misconception per major concept with clear wrong-answer definitions (16 misconceptions)
- [x] Every source example anchored to cell
- [x] ≥ 1 non-example per conceptual distinction the source draws
