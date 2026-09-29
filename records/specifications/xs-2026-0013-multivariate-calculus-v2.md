# XS-2026-0013: Interactive lesson candidate multivariate calculus v2

**Status:** Approved  
**Approval scope:** Stage 1 governed generation  
**Supersedes / iteration position:** Iteration 2 — v2 regeneration (iteration of XS-2026-0012, whose unamended contracts remain the baseline; deltas are declared below)  
**Source concept model:** [CM-2026-0012](../concepts/cm-2026-0012-multivariate-calculus.md)  
**Learning plan:** [LP-2026-0013](../plans/lp-2026-0013-multivariate-calculus.md)  
**Target learner:** AIML-4 student, post-Class-1/2/3 (unchanged)  
**Artifact family:** Single-file offline HTML  
**Learning outcomes:** per LP-2026-0013 §Measurable learning outcomes (7 outcomes, each exercised by ≥1 assessment item)

## Learner problem and teaching strategy

Unchanged from XS-2026-0012: the agenda-style notebook (31 cells; four cleared code cells; two opaque figures; one wrong chain-rule formula) becomes an explain-before-use path: orientation unit, seven units in canonical anatomy (Learn → Predict → Explore → Practice → Check → Connect), synthesis with interleaved mastery, persistent review list, glossary. One metaphor throughout: training is walking downhill on a surface the model can feel but cannot see. All readouts computed live; nothing hard-codes what can be computed. v2 restructures the merged Jacobian+Hessian unit into U5 (Jacobian) and U6 (Hessian & curvature) per EVAL-2026-0014, adding the Jacobian lab, ladder, unit check, and mastery item.

## Content and evidence map

U0 cells 1–2 (orientation; PART 9/10 numbering disposition carried); U1 cells 3–6 (+ MSE foundation; cell 5's opaque figure replaced by the W1 loss explorer); U2 cells 7–14 (partials; gradient; gradient descent; cell 14's 5 → ≈0.0576 recomputed live); U3 cells 15–16 (directional derivative; cos φ proof; ∇f=[3,4] example); U4 cells 17–20 (chain rule with the corrected cell-18 formula tagged; computational graph; cell 20's x=2 → 4 recomputed live); **U5 cells 21–23** (Jacobian definition J_ij = ∂f_i/∂x_j; (outputs × inputs) shape; the 3×2 example; cell 23's matrix [[2,1],[0,3]] as the live W6 lab; applications); **U6 cells 24–29** (Hessian; curvature; definiteness classification; saddles; Newton with invertibility guard; PART 8 summary woven in; cell 29's opaque figure replaced by the W7 curvature lab); U7 cells 30–31 (non-convex landscapes; λᵏ vanishing/exploding; adaptive optimizers; stochastic/distributed large-scale). No silent drops; full coverage matrix ships in EVAL-2026-0015.

## Learning sequence

U0 → U1 → U2 → U3 → U4 → U5 → U6 → U7 → Synthesis + mastery (M1–M9) → review list → glossary → colophon. Every forward reference is a promise with a named payoff unit (LP-2026-0013).

## Interaction and feedback specification

**W1 `loss-eval` (U1, canvas).** Unchanged data/sliders/readout except the tightened viewport (below). Viewport: xMin=−2, xMax=10, yMin=**−1**, yMax=10 (aspect 1.167 → 0.917; data y∈[2,9] and the least-squares optimum remain visible; extreme fits clip at the canvas edge as before).

**W2 `partial-lab` (U2, canvas, gated by G1).** Unchanged; viewport ±3.4 / ±2.6. **W3 `descent-lab` (U2, canvas).** Unchanged; viewport ±3.4 / ±2.6. **W4 `direction-lab` (U3, canvas, gated by G2).** Unchanged; viewport ±3.4 / ±2.6. **W5 `graph-lab` (U4, canvas).** Unchanged; viewport ±3.4 / ±2.6.

**W6 `jacobian-lab` (U5, canvas, new).** Constructed interactive for claims 32–35; defaults reproduce cell 23's matrix. Manipulables: four entry sliders a,b,c,d (range −3..3, step 0.1; defaults 2,1,0,3). Canvas: two panel-clipped grids — left = input neighborhood with the unit square highlighted and basis arrows e₁,e₂; right = the same neighborhood under J (sheared grid, unit-square image as a parallelogram, basis-image arrows). Readout: live matrix, det = ad−bc with classification (|det|<0.05 → collapsed/singular; det<0 → orientation flipped; else preserved with |det| area scale), basis images, J·(1,1), and the source-matrix note at defaults. Goal strip: "deform the square — flatten it to a line (det = 0), then flip it over (det < 0)". **Viewport: xMin=−13.5, xMax=13.5, yMin=−7.25, yMax=7.25 (two 13.5-unit panels; equal x/y scale so shapes are never distorted).** Degenerate guard: none needed (slider-bounded); the det≈0 and degenerate all-max/all-min cases are driven in verification.

**W7 `curv-lab` (U6, canvas, gated by G3).** Unchanged design (two live parabola panels; a/c sliders −3..6; definiteness classifier + Newton note); viewport ±3.4 / ±2.6. **W8 `chain-depth` (U7, numeric, no canvas by stated reason).** Unchanged (λ 0.5..1.5, k 1..100; λᵏ readout with 10⁻⁴/10⁴ thresholds and stability band).

Assessment keys (all auto-graded; strict modality — no textareas): gates G1 (correct: gradient direction), G2 (5 along (3,4)/5), G3 (saddle); ladders L1–L7 ×3 rungs — L1 4/1, L2 6/60, L3 5/0.707, L4 −20/24, **L5 9/0 (new)**, L6 −8/−2, L7 0.0115/17.45; unit checks c1–c7 (numeric: 2.5, 12, 10, 12, **6 (new c5)**, 10, 0.0282; MCQ answers: c1 b, c2 b, c3 a, c4 b, **c5 a (new)**, c6 c, c7 b); mastery M1–M9 with confidence routing (numeric: 36, 7.2, 2.121, **12 (new M9)**; MCQ: M2 a, M3 c, M5 a, M6 a, M8 b; M3/M9 confident-miss routing verified). Explain items e2/e4 unchanged. Storage namespace `mvc2-*` with graceful fallback and reset; corrupted-storage recovery verified.

## Formula manifest

15 equations, unchanged from XS-2026-0012 (EQ-001 partial definition; EQ-002 f = x²+3y partials; EQ-003 gradient; EQ-004 magnitude; EQ-005 gradient descent; EQ-006 directional derivative; EQ-007 projection bound; EQ-008 single-variable chain rule (corrected, tagged); EQ-009 multivariable chain rule; EQ-010 Jacobian J_ij with shape — **target unit U5**; EQ-011 Hessian; EQ-012 second-order view; EQ-013 Newton with guard; EQ-014 MSE; EQ-015 λᵏ). Each ships inside a `<div class="formula">` block with a `<ul class="symkey">`; the P5 sweep verified 15/15 blocks with 15 symbol keys.

## Term definition registry

44 terms, unchanged from XS-2026-0012 §Term definition registry (optimization → residual connection), each defined at first mention and linked to a 6-field glossary entry; zero deferred jargon. v2 introduces no new domain term (the Jacobian lab's determinant/area-scale language is explained inline and the term "determinant" is used only with its plain-language gloss at first mention).

## Visual/representation rationale

Unchanged, plus: the Jacobian gets a representation where its meaning is geometric — a live plane deformation with equal x/y scale, so stretch, shear, rotation, collapse, and reflection are literally visible; the two-panel before/after split keeps the input reference fixed while the output panel carries the transformation.

## Accessibility and inclusion plan

Unchanged from XS-2026-0012 (semantic landmarks, heading order, aria-live readouts, keyboard-operable controls, per-canvas text equivalents, color never sole encoder, reduced motion, print fallback, focus rings, 16px floor, no drag-only interaction). v2 additions: W6's canvas text equivalent describes both panels, the basis arrows, and the highlighted image; all four sliders carry descriptive aria-labels; the legend names all three encodings.

## Performance/responsiveness intent

Single file; zero external requests; seven canvases each responsive via `makeView` (clientWidth at draw time, DPR scaling, aspect-ratio height) with 7 resize listeners = canvas count; W6's per-redraw workload is bounded (26 grid segments + 2 shapes + 4 arrows per panel); all widget math closed-form; nav single-line horizontal scroll; concept map internally scrollable at narrow widths (overflow-x auto; 592px surface in a 294px viewport at 320px — verified).

## Acceptance criteria and evaluation dimensions

`verify-candidate.py` strict pass (0 failures: 7 canvases, 7 ladders, 15 formulas, 44 glossary entries, slider/option/font/callout contracts); every formula-manifest equation present with a symbol key; every registry term defined and linked; every widget matches this specification element-for-element (including W6 viewport −13.5/13.5/−7.25/7.25 and W1 yMin −1); six audits + adversarial gate pass; live rendered verification at 320/640/1024px with 0 console errors; repository checker exit 0; disposition `private-pilot-complete`, non-independent, release-ineligible.

## Concept map (dependency nodes and directed edges)

Unchanged from XS-2026-0012 (13 nodes, 16 directed edges; the DD→GRAD dashed payoff edge remains; verified 16/16 edges present).

## Conformance checklist (depth-calibration contract)

- [x] Every widget declares learner-manipulable variable(s) or explicit "static demo" justification (W8 numeric by stated reason)
- [x] Every canvas widget declares input bounding (sliders, min/max) — all manipulables slider-bounded
- [x] Every canvas widget declares its mathematical viewport (W1 −2..10 / −1..10; W2/W3/W4/W5/W7 ±3.4 / ±2.6; **W6 two panels −13.5..13.5 / −7.25..7.25**)
- [x] Controls declare atomic `.slider-control` encapsulation and `.option-stack` layout
- [x] Complete Formula manifest (EQ-001–EQ-015) mapped to unit `.formula` blocks (15/15 verified)
- [x] Complete Term definition registry (44 terms); zero deferred jargon
- [x] Assessment modality strictly MCQ / bounded auto-graded numeric; no `<textarea>`
- [x] Exhaustive glossary term set listed from the CM (every term used has 6 fields; 44 entries verified)
- [x] Concept map declares explicit dependency nodes and directed edges (multi-branch; 16 edges verified)
- [x] Every LP-planned ladder (L1–L7), prediction gate (G1–G3), and reveal arc has a specified element
- [x] Canvas text equivalents specified for every visual component

