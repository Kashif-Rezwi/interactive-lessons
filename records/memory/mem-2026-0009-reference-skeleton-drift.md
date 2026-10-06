# MEM-2026-0009: Diff the candidate against the sibling reference's canonical skeleton, not against memory

**Confidence:** Supported
**Curator:** Repository maintainer (solo Stage 1 operator)
**Created / review date:** 2026-10-06
**Scope:** Lesson generation (P4) and verification (P5) in the Learning OS Stage 1 pipeline
**Tags:** reference-skeleton, orientation-unit, nav-dots, main-landmark, table-styling, generation-drift, verification-gap
**Evidence records:** [RUN-20261006-0001](../runs/run-20261006-0001-probability-basics-v1.md) (revision 1), [EVAL-2026-0016](../evaluations/eval-2026-0016-probability-basics-v1.md), [MEM-2026-0005](mem-2026-0005-canvas-responsiveness-and-design-drift.md) (the sibling design-drift memory), [P-18](../../library/patterns/lesson-patterns.md)
**Supersedes / conflicts with:** none (Iteration 1 — original); extends MEM-2026-0005's design-drift class from component styling to the page skeleton

## Lesson

CAN-2026-0015's initial build was generated in a single session from *partial* reads of the sibling reference artifact. Every presence-level check passed, yet a learner immediately saw that Unit 0 "feels unfinished and misaligned." Investigation found five skeleton defects: (1) nav completion dots were **consumed** (`setDot` queried `.topnav a .dot`) but **never created** — the references create them via JS at load, so §10.2's dots silently never rendered; (2) the U0 learning-loop table and the U8 covariance table used `class="apptable"` with **no CSS rule** for it (the references style `table.apptable,table.looptable` and use `looptable` + caption for the loop table); (3) no `<main id="main">` landmark (references wrap content in it); (4) the header drifted (bare topic `h1`, non-canonical kicker, storage note in the header instead of at U0's end); (5) the mastery summary used the mono `.readout` style instead of the `.msum` summary box.

**The lesson:** the sibling artifacts share a canonical skeleton (now [P-18](../../library/patterns/lesson-patterns.md)) that is *invisible to presence checks* — a class name can exist in markup while its CSS rule, its JS creator, or its landmark wrapper is missing. Root cause: authoring from memory of the reference rather than diffing against it, compounded by a degraded-mode Audit 6 that never clicked a check to see a dot fill.

## Why this is believed

- The defect set is fully reproduced mechanically: reverting the five fixes to a simulated pre-fix build makes the new `verify-candidate.py` skeleton check fail on all three classes (main-landmark, nav-dots, table-styling), while the pre-fix build had passed every earlier check.
- All three prior governed artifacts (md v2, hdg v1, mvc v2) conform to the skeleton — the drift is a property of this generation's method, not of the standard.

## Recommended action

1. At P4, diff the candidate's header + U0 + closing sections against the module's reference artifact element-by-element (P-18 skeleton), in addition to the existing conformance sweeps.
2. At P5, the new skeleton check (`verify-candidate.py`) mechanically enforces the main landmark, nav-dot wiring, table-class styling, and msum styling; the QA checklist carries the Audit 4 orientation-anatomy and Audit 5 skeleton-conformance items.
3. When Audit 6 runs live, click one check to completion and confirm a nav dot actually fills (the behavioral item that the degraded mode could not exercise).
