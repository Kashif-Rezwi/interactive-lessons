# MEM-2026-0007: Deterministic assembly for long single-file artifacts — and rendered verification catches what syntax checks pass

**Status:** Supported
**Curator:** Repository maintainer (solo Stage 1 operator)
**Created / review date:** 2026-09-24
**Scope:** Generation of governed single-file interactive lessons (and any long generated artifact) in Learning OS Stage 1
**Tags:** assembly, tooling-hazard, rendered-verification, adr-0010, quality-gate, workflow
**Evidence records:** [RUN-20260924-0001](../runs/run-20260924-0001-multivariate-calculus-v1.md), [EVAL-2026-0014](../evaluations/eval-2026-0014-multivariate-calculus-v1.md), [ADR-0010](../../docs/adr/0010-rendered-output-verification.md), [ADR-0012](../../docs/adr/0012-autonomous-pipeline-orchestration.md)
**Supersedes / conflicts-with:** none (Iteration 1 — original)

## Lesson

The 2026-09-24 run built CAN-2026-0013 (`multivariate-calculus-v1.html`, ~157 KB, single file) in one session. Two independent hazards materialized, and both were caught by mechanisms now proven load-bearing:

1. **Estimation-based appends corrupt long files silently.** Appending content to a growing artifact by computing a target line number ("the previous chunk was ~45 lines, so insert at N") places the new content *inside* the previous chunk whenever the estimate falls short of the true end of file. Each such event pushes the previous chunk's tail below the new content; the tails stay in the file but out of order, and later appends compound the displacement. In this run, twelve cascading displacements produced: six missing JS functions (`dots`, `review`, `addReview`, `renderReview`, `setDot`, `markCheck`, plus `gAnswer`/`bindGates`), four truncated widget tails (`drawW1`, `drawW3`, `drawW5`, `drawW7`), two missing closing braces in binder functions, a four-entry glossary boundary violation, and two displaced CSS rules — while the file still *looked* structurally plausible at the section level and its byte count stayed in the expected range.
2. **A shell heredoc is not a safe transport for large template text.** The first write attempt piped a multi-line heredoc through the session shell; the terminal echoed mangled `heredoc>` fragments and produced a corrupted file that had to be discarded. Writing content through a dedicated file-editor operation (one chunk object per call) was reliable.

## Why this is believed

- Sequence evidence in RUN-20260924-0001 §Reflection: the displacements correlate exactly with appends whose recorded target line was below the true end of file; a brace-depth scanner located `bindLadders`/`bindChecks` imbalances at the section boundaries, and a per-marker depth trace (`0,0,…,0,2,3,3`) localized the loss to the ladder→checks boundary.
- `node --check` reported only "Unexpected end of input" — enough to prove damage and, after repair, to prove balance, but it **cannot** detect a restored function that references an undefined variable. The `dyg`/`dydg` typo passed `node --check` and passed presence-count greps, then threw `ReferenceError: dyg is not defined` on page load in the browser — caught only by Audit 6 (ADR-0010). Presence checks ("does `markCheck` exist?") and static parse checks are individually insufficient; the rendered run is what proved the artifact executes.
- Corroborating precedent: [MEM-2026-0005](mem-2026-0005-canvas-responsiveness-and-design-drift.md) established the same pattern for canvas engineering — artifacts can be pedagogically complete and mechanically "conformant" while being technically broken, and only execution-level gates catch it.

## Recommended action

1. **Assemble long artifacts from independent chunk files, then concatenate once.** Author each section as its own file, then join with a single deterministic command. This removes all offset arithmetic and makes each chunk independently reviewable.
2. **When appending is unavoidable, probe the true end of file** and let the tool report the exact boundary; never compute the target from an estimate of a previous chunk's length.
3. **Never route large multi-line content through an interactive shell heredoc**; use a dedicated file-write operation per chunk.
4. **Treat the rendered run as the acceptance gate for execution integrity** (already required by ADR-0010 for Audit 6): after any repair to a generated artifact, re-run the browser pass and require zero page errors — static balance checks alone do not clear a repair.
5. **Keep the recovery diagnostics reproducible**: a section-marker/brace-depth scan and a function-presence inventory are cheap, in-repo-computable checks that localize this defect class in seconds.
