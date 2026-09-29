# CM-2026-0012: Multivariate calculus for machine learning (v2 concept model)

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 2 — v2 regeneration (iteration of CM-2026-0011; the v1 lineage remains intact and superseded for authoring)  
**Owner:** Repository maintainer  
**Source package:** [SRC-2026-0004](../sources/src-2026-0004-multivariate-calculus.md)  
**Domain review status:** Reviewed by the same operator; non-independent  
**Confidence:** high

**Intake re-verification (2026-09-29):** source SHA-256 `ab11029313a65ed7892248e9ecca7d26b5f19fe7c79f3cd27f64b98cd138fd3e` re-verified unchanged; all 31 cells re-read in order. The claim inventory is **unchanged from CM-2026-0011** — 48 anchored claims, 35 concepts, 16 diagnosed misconceptions — because the source bytes are identical; this iteration re-grounds that set for the v2 artifact and records the lesson-layer deltas. The full anchored claim list, concept/definition table, dependency graph, example/non-example set, misconception list, and artifact dispositions remain traceable in [CM-2026-0011](cm-2026-0011-multivariate-calculus.md) and are not duplicated here (link-not-copy).

**Cross-lesson continuity:** unchanged from CM-2026-0011 — depends on Class 1 (vectors, dot products, norms, slope, function notation; [CM-2026-0007](cm-2026-0007-linear-algebra-foundations.md)), Class 2 (eigenvalue/matrix vocabulary; [CM-2026-0009](cm-2026-0009-matrix-decompositions-applications.md)), and Class 3 (high-dimensional vocabulary; [CM-2026-0010](cm-2026-0010-high-dimensional-geometry.md)); the artifact links back to the governed Class 1 (`linear-algebra-foundations-v10.html`), Class 2 (`matrix-decompositions-applications-v2.html`), and Class 3 (`high-dimensional-geometry-v1.html`) lessons.

## Scope and learning boundary

Same scope and exclusions as CM-2026-0011 (no automatic-differentiation internals, convergence proofs, Lagrangians/KKT, momentum/Nesterov derivations, transformer architecture). v2 reorganizes the artifact into orientation + **seven** teaching units: the merged v1 unit "Jacobian, Hessian & curvature" is split into **U5 The Jacobian** (cells 21–23) and **U6 Hessian & curvature** (cells 24–29), with the advanced-ML view becoming U7 (cells 30–31) — a sequencing/structure change only; no claim leaves the source-grounded set.

## Concepts and definitions

The 35 concepts remain as defined in CM-2026-0011 §Concepts and definitions, in order: ML as optimization; loss function; parameter; high-dimensional parameter space; loss surface; partial derivative; freezing variables; slope along one direction; sensitivity ∂L/∂wᵢ; gradient; steepest-ascent property; negative gradient; gradient magnitude; learning rate η; gradient descent; directional derivative; projection; maximum directional derivative; chain rule; function composition; computational graph; backpropagation; forward/backward pass; **Jacobian**; **vector-valued function**; local transformation meaning; **Hessian**; curvature; definiteness; saddle point; Newton's method; vanishing/exploding gradients; non-convex landscape; adaptive optimizers; stochastic gradients. The v2 split gives the Jacobian cluster (claims 32–35) and the Hessian cluster (claims 36–42) their own units and assessment homes without redefining either.

## Atomic claims and evidence anchors

Unchanged: claims 1–48 as recorded in CM-2026-0011 §Atomic claims, each anchored to source cells 4–31 and re-verified at intake. No claim was added, removed, or reworded (the source is byte-identical); the chain-rule claim 27 continues to carry the corrected formula and its artifact tag, and the recomputation numbers (claims 8, 9, 19, 20, 24, 31) remain the live-checking set.

## Prerequisites and relationships

Dependency graph unchanged from CM-2026-0011 §Dependency graph: OPT→LOSS→PD→GRAD→{GD, DD, JAC, HES}; DD→GRAD is the steepest-ascent payoff edge; CR→BP; JAC→BP; HES→{SADDLE, NEWT}; LOSS+CR→BP; SADDLE+GD→DEEP. FOUNDATION bridges unchanged (MSE, dot product, eigenvalue one-liner, second-order approximation, exponential scaling λᵏ). Source use-before-define repairs unchanged (preview table labeled as preview; steepest-ascent assertion promised in U2 for its U3 proof).

## Examples, non-examples, and misconceptions

Unchanged from CM-2026-0011 §Examples/non-examples and §Diagnosed misconceptions (16 items; each ships as a per-option distractor and/or a misconception callout). v2 adds **constructed practice items**, not new claims: the W6 Jacobian lab (a 2×2 linear map of the unit grid; defaults reproduce the source's cell-23 matrix [[2,1],[0,3]] and (1,1) ↦ (3,3)), the L5 Jacobian-entries ladder, check c5 (J₂₁ of (x²+y², 2xy) at (1,3) → 6; indexing MCQ against misconception 12), and mastery M9 (J₁₂ of (xy², x²y) at (2,3) → 12) — all provenance-tagged as constructed and independently recomputed.

## Ambiguities, gaps, and assumptions

- Cell 18's wrong chain-rule formula dispositioned and corrected with a tag (carried from v1; unchanged).
- The agenda's PART 9/10 numbering inconsistency recorded; one advanced-ML section ships as U7 (unchanged disposition).
- Cells 5 and 29 are opaque base64 figures, replaced by live, labeled canvases (unchanged); cell 23's matrix additionally gains the W6 lab as its live visual.
- Cleared code cells are recomputed live (unchanged; cell 20 → dy/dx = 4 and cell 14 → ≈0.0576 reconfirmed by the v2 harness).
- Assumption unchanged: the learner completed AIML-4 Classes 1–3; no prior multivariable calculus. Cell 25's Newton update keeps its invertibility guard (supplemental); cell 16's maximum claim keeps its cos φ proof (supplemental).

## Review and acceptance criteria

All 31 cells dispositioned; every displayed number recomputed live in-page and independently in the harness (118 checks, 0 failures on the final build; 48 behavioral checks, 0 failures); misconceptions carried as distractors with per-miss feedback; at most one callout per unit; glossary covers every used term with 6 fields; steepest-ascent promise paid off in U3; the new Jacobian lab's determinant cases (flatten det=0, flip det<0, degenerate all-max/all-min, identity) verified both in the harness and in live browser extrema.

## Conformance checklist (depth-calibration contract)

- [x] ≥1 anchored atomic claim per concept (48 claims across 35 concepts; re-verified, unchanged set)
- [x] Full dependency graph covering every prerequisite and flagging every source use-before-define case (via CM-2026-0011, re-verified)
- [x] ≥1 diagnosed misconception per major concept with wrong-answer definitions (16, distractor-ready)
- [x] Every source example anchored to cell (unchanged, re-verified)
- [x] ≥1 non-example per conceptual distinction (unchanged, re-verified)

