# MEM-2026-0006: Plan-declared reveal arcs survive generation when the LP names the payoff unit

**Confidence:** Supported  
**Curator:** Repository maintainer (solo Stage 1 operator)  
**Created / review date:** 2026-09-07  
**Scope:** Lesson-plan authoring (P2) and generation (P4) in the Learning OS Stage 1 pipeline  
**Tags:** reveal-arc, learning-plan, generation-fidelity, forward-reference, lesson-design  
**Evidence records:** [RUN-20260906-0002](../runs/run-20260906-0002-matrix-decompositions-applications-v2.md), [EVAL-2026-0012](../evaluations/eval-2026-0012-matrix-decompositions-applications-v2.md), [RUN-20260907-0001](../runs/run-20260907-0001-high-dimensional-geometry-v1.md), [EVAL-2026-0013](../evaluations/eval-2026-0013-high-dimensional-geometry-v1.md), [MEM-2026-0004](mem-2026-0004-compliant-minimum-collapse.md) (the negative contrast class)  
**Supersedes / conflicts with:** none (Iteration 1 — original); strengthens P-15 in the pattern catalog

## Lesson

The failure class MEM-2026-0004 documented was the compliant-minimum collapse: a generation that satisfies the letter of the spec while dropping invisible structural investments — the canonical example being a promised reveal arc (the wᵀx payoff in CAN-2026-0004) that never delivered. Two subsequent governed generations from *different, more abstract* sources tested whether plan-level declaration of the arc (with the payoff unit named) protects it:

- CAN-2026-0011 (matrix-decompositions v2, RUN-20260906-0002): every LP-declared arc shipped and paid off, under a from-scratch rebuild.
- CAN-2026-0012 (high-dimensional geometry v1, RUN-20260907-0001): the LP declared a U3 → U5 arc — Unit 3 *names* distance concentration and explicitly promises the mechanism later; Unit 5 pays it off with the norm-concentration widget and an explicit award note. The abstract source (assertion-heavy, near-zero worked numbers) gave the generator every excuse to drop the arc; it did not.

**The lesson:** arc durability is a property of the *plan*, not the generator's goodwill. When the LP declares the arc as a checkable outcome — setup unit, payoff unit, and the connective claim — generation ships it; when it is implicit prose, generation silently drops it (the CAN-2026-0004 failure). Declare reveal arcs with named payoff units at P2, and Audit 1/3 can then verify them mechanically.

## Why this is believed

- Two independent generations (different sources, different source classes, both full-coverage Audit 1 passes) shipped every LP-declared arc, each verified in read-in-order Audit 3 and in the coverage matrix (EVAL-2026-0012, EVAL-2026-0013).
- The single observed arc failure (CAN-2026-0004) had no plan-level declaration — the arc existed only in the generator's judgment (MEM-2026-0004 root-cause).
- The observation is now recorded in P-15 of the pattern catalog with both positive cases and the negative contrast.

## Recommended action

1. Keep the LP template's reveal-arc field mandatory for any lesson with a buildable concept; require setup unit, payoff unit, and the connective claim as checkable outcomes (already the practice that produced both confirming runs).
2. At P5 Audit 1/3, verify each declared arc: setup present in the named unit, payoff present in the named unit, no dangling forward reference. Both confirming runs did this; make it an explicit checklist line rather than incidental evidence.
3. Promote P-15 evidence text with each new confirming lesson; this memory reaches `Established` per the review policy when the pattern has three independent confirming generations (currently two).

## Counterexamples and limitations

- Both confirming generations ran under the same prompt card (@0.6.0) and the same operator; a different card or an autonomous drift could still collapse arcs — the LP declaration limits the blast radius, it does not make collapse impossible.
- Non-independent review: the same operator declared the arcs and verified them; a second evaluator could judge "payoff delivered" differently.
- Two observations is the minimum for a `Supported` memory; it is not yet an established invariant.

## Retrieval guidance

Consult at P2 (declare arcs with named payoff units), at P5 (verify each declared arc mechanically), and when diagnosing a "dangling forward reference" defect (check the LP before blaming the generator). Pair with MEM-2026-0004 (the failure class this memory guards against) and P-15 (the pattern).

## Privacy and retention

No personal data; retain as a standing generation guard until superseded by a confirming or contradicting third generation.