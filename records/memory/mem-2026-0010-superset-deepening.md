# MEM-2026-0010: Deepen a conformant lesson by a verified superset, not a regeneration

**Confidence:** Supported
**Curator:** Repository maintainer (solo Stage 1 operator)
**Created / review date:** 2026-10-06
**Scope:** Lesson generation (P4) in the Learning OS Stage 1 pipeline — producing a v(N+1) from a conformant v(N)
**Tags:** iteration-strategy, superset-deepening, design-system-reuse, storage-namespace, skeleton-drift, verification
**Evidence records:** [RUN-20261006-0002](../runs/run-20261006-0002-probability-basics-v2.md), [EVAL-2026-0017](../evaluations/eval-2026-0017-probability-basics-v2.md), [MEM-2026-0009](mem-2026-0009-reference-skeleton-drift.md) (the drift class this avoids), [MEM-2026-0005](mem-2026-0005-canvas-responsiveness-and-design-drift.md)
**Supersedes / conflicts with:** none (Iteration 1 — original); complements MEM-2026-0009 by giving the safe path for a *deepening* iteration

## Lesson

When a candidate already conforms to the canonical skeleton and passes every check, the cheapest correct way to produce a deeper version is a **superset**, not a regeneration: copy the conformant artifact, rename its local-storage namespace (e.g. `prob1-*` → `prob2-*`) so the new version's progress is independent, and *add* the new surfaces (labs, ladders, mastery items, glossary terms, slider/resize wiring) while reusing the design system (tokens, nav, `makeView`, storage/gates/ladders/checks/mastery contracts) verbatim. Regenerating from scratch re-opens the whole skeleton-drift class (MEM-2026-0009) and re-authors verified markup for no gain.

## Why this is believed

- CAN-2026-0016 (probability v2) was produced as a superset of the verified CAN-2026-0015 (probability v1): the added surfaces (W10–W12, L7–L8, M12–M13, three glossary terms) integrated cleanly, and `verify-candidate.py --strict` passed on the first full run with 0 failures — no skeleton defect recurred.
- The one non-additive change required was the storage-namespace rename; forgetting it would silently couple v2 progress to v1's saved dots/review list.
- The deepening raised the weighted score (3.63 → 3.79) mainly by enabling *live* rendered verification (Audit 6) that v1 deferred, showing that a superset iteration can also close verification debt.

## Recommended action

1. For a v(N+1) whose v(N) already conforms, prefer a superset: copy → rename the storage namespace → add surfaces → re-verify. Reserve regeneration for when the *structure* (unit sequence, skeleton) must change.
2. Always rename the local-storage namespace in the copy; treat the prefix as part of the artifact identity.
3. Re-run the full verification suite on the final hash (strict verifier, `node --check`, stub-DOM draw smoke, and — where a browser is available — live render).

## Counterexamples and limitations

- If the deepening changes the unit sequence or the skeleton, a superset is the wrong tool (a structural change is a regeneration; see the multivariate-calculus v1→v2 split of Jacobian/Hessian).
- A superset inherits v(N)'s defects; it is only safe when v(N) is conformant. Copying a defective base propagates the defect.
- Adding a canvas without a matching `resize` listener or declared viewport reintroduces the canvas-responsiveness class (MEM-2026-0005); the superset still needs the full canvas-engineering sweep.

## Retrieval guidance

Recall this when asked to "improve"/"deepen" an existing lesson or to bump a candidate version. The decision rule: conformant base + additive change → superset; structural change → regenerate.

## Privacy and retention

No learner data involved; all evidence is in-repo run/eval records.
