# RUN-20261006-0001: Probability basics v1 (Class 5 interactive lesson)

**Status:** Pilot complete  
**Parent run:** none (first generation for SRC-2026-0005)  
**Owner:** Repository maintainer (solo Stage 1 operator)  
**Objective:** Generate the Class 5 interactive lesson (probability basics, CDF ↔ PDF conversion) at benchmark-band depth from [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md): nine teaching units (random variables → PMF → PDF → CDF → conversion → expectation → variance → covariance → ML connections), a signature conversion lab, three prediction gates, six faded ladders, nine unit checks, an 11-item interleaved mastery check, two explain-in-own-words items, a ~40-term glossary, and a branched concept map; all readouts computed live; nothing hard-codes what can be computed.  
**Budget:** One generation; maximum two revision cycles  
**Iteration counts:** generation = 1; in-generation corrections = 3 (one shell-heredoc mangling during harness authoring, re-authored as a file; one harness case-sensitivity defect corrected; one answer-position variety fix reordering six options and their keys); revision cycles = 0 (per [ADR-0006](../../docs/adr/0006-record-iteration-accounting.md))  
**Classification:** production  
**Operating scope:** Stage 1 private pilot  
**Review-independence summary:** non-independent  
**Public-release eligibility:** ineligible

## Input manifest

- Source: [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md), SHA-256 `837a1736e4286cf6b8b0d91792dd6611162dfb811332860a5dfca67fc60fd0ac`
- Concept model: [CM-2026-0013](../concepts/cm-2026-0013-probability-basics.md) (60 anchored claims, 35 concepts, 16 diagnosed misconceptions)
- Learning plan: [LP-2026-0014](../plans/lp-2026-0014-probability-basics.md) (9 units + orientation; L1–L6; 11-item mastery; depth-pass table)
- Experience specification: [XS-2026-0014](../specifications/xs-2026-0014-probability-basics-v1.md) (9 canvas widgets W1–W9; 3 gates; 6 ladders; EQ-001–EQ-023; 42-term registry)
- Candidate: `CAN-2026-0015`, `probability-basics-v1.html`
- Prompt card: `prm-generator-lesson-standard@0.6.0`, digest `532febec136b` (the card file is the persisted prompt content)
- Benchmark: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) (calibration exemplar, per [ADR-0011](../../docs/adr/0011-benchmark-definition-and-artifact-change-protocol.md)); implementation reference: CAN-2026-0014 (`multivariate-calculus-v2.html`, nearest governed component-contract artifact)
- Tooling: `scripts/verify-candidate.py` (strict), `scripts/check-repo.py`, Python 3 harness (numeric recomputation + answer-key cross-check), Node (`node --check` + stub-DOM draw smoke test)

## Generation events

| Time | Candidate ID | Model/configuration | Prompt digests | Cost/latency | Warnings/errors |
| --- | --- | --- | --- | --- | --- |
| 2026-10-06 | CAN-2026-0015 | Cline (Claude Sonnet 4.6), autonomous orchestrator | prm-generator-lesson-standard@0.6.0 `532febec136b` + prm-orchestrator-autonomous@0.1.0 | single session | 3 in-generation corrections (harness heredoc mangling; harness case-sensitivity; answer-position variety); 0 assembly incidents |

**Generation method:** single-session authoring of the single-file HTML against the pinned CM/LP/XS, reusing the module's verified design system (tokens, nav, `makeView`, storage/gates/ladders/checks/mastery contracts) from the sibling reference and applying the source's own content. Every surface verified on the final hash.

## Evaluation and defects

### Standing verification audits (P5 Audits 1–6)
- **Audit 1 (Coverage):** all 61 source cells mapped to units with dispositions; five opaque figures (cells 8, 19, 29, 31, 58) recovered as live/plainly-stated content; the cell-26 CDF upper-limit typo corrected to 1 with a tag; broken LaTeX splits re-emitted. Full coverage matrix in [EVAL-2026-0016](../evaluations/eval-2026-0016-probability-basics-v1.md).
- **Audit 2 (Mathematical & canvas extrema):** independent Python harness recomputed every displayed number, widget default, ladder answer, unit-check key, and mastery key (60+ values; e.g. dice 1/6, F(0.3)=0.09, E[X]=3.5, Var≈2.92, Corr=6/(2·3)=1, eigenvalues of [[2,1],[1,2]] = 3,1); all matched (0 failures). Canvas extrema: every canvas input is slider-bounded (n 2–12, k 1–6, a/b 0–1, x 0–1, s 0–3, ρ −1..1); the W3 b<a case is guarded (swap); W8/W9 use a fixed seed (mulberry32) so extrema are deterministic. `node --check` clean; stub-DOM execution of all 9 draw functions at defaults: 0 exceptions.
- **Audit 3 (Dependency order):** read-in-order sweep from an empty taught-so-far set: distribution/discrete-continuous (U1) precede PMF (U2) and PDF (U3); CDF (U4) precedes the conversion (U5); expectation (U6) precedes variance (U7); covariance (U8) precedes PCA (U9). No use-before-explain found; forward references name payoff units.
- **Audit 4 (Pedagogical & depth-calibration):** every unit has a lede, intuition-first prose, a worked number, a signature visual, and a constructed-response check; L1–L6 are full 3-rung ladders with never-auto-opening hints; 3 gates hide their widget until commitment with option-specific feedback; 2 explain items with model answers (E1 U5, E2 U7); mastery is 11 interleaved items with confidence tags, confident-miss routing, reasoning/transfer/error-identification coverage and no reused numbers; glossary 41 entries, 6 fields each; concept map is a 13-node/16-edge branched graph revisited at synthesis; callout density ≤1/unit.
- **Audit 5 (Technical & behavioral):** `verify-candidate.py --strict` = PASSED (0 failures; 9 canvases, 6 ladders, 3 gates, 19 formula blocks, 41 glossary entries, 10 slider-track encapsulations, font floor ≥16px, option stacks, callout discipline, state-styling). 234 unique IDs, no duplicates; every data-wiring target resolves; keyboard-operable native controls; offline storage with reset and corrupted-storage recovery.
- **Audit 6 (Rendered-output verification, ADR-0010):** **degraded mode** — no browser subagent available in this environment; a Node stub-DOM execution of all nine draw functions (0 exceptions) and `node --check` were run in place of live rendering. Live screenshots at 320/640/1024px, console capture, reduced-motion, and print are recorded as **not performed**; the evaluation caps Visual/UX/Technical at 2.5 per the skill's degraded-mode rule.

### Adversarial re-examination (mandatory gate per ADR-0009)
- **Re-examination method(s):** (1) read-in-order fresh-perspective re-pass; (2) handler-level simulation of boundary cases; (3) canvas-extrema forcing; (4) honesty/provenance scan.
- **Elements covered:** gate commitment-bypass (each gate refuses without a commitment — verified in source), grading boundaries (numeric tolerances accept the intended rounded answer and reject near-misses), confident-miss routing on both MCQ and numeric mastery items, reset from corrupted localStorage (review filter drops unknown IDs), and the W3 a>b degenerate case (guarded). Canvas extrema: s=0 collapses the spread lab to a single spike (renders on-canvas); ρ=±1 collapses the cloud to a line (ellipse degenerates to a segment; no off-canvas rendering).
- **Findings & severity:** one Minor — the initial draft placed every MCQ/gate correct answer at position **b** (answer-position predictability); remediated in-generation by reordering six items (c1m→a, c4m→c, c7m→a, g2→a, g3→c, m7→a) so the correct position now varies across a/b/c. Clean otherwise.

### Re-verification pass (WF-008)
- **Sampled checks re-executed:** `verify-candidate.py --strict` re-run on the final hash (0 failures); Python harness re-run (0 failures); Node `node --check` + stub-DOM smoke re-run (0 exceptions).
- **Headline claims reproduced:** yes — the artifact hash below is the verified build.

## Reflection and root-cause hypothesis

The source is unusually "clean" for a notebook (no code, only prose plus five opaque figures and one typo), so generation risk concentrated on (a) recovering the opaque figures and the CDF typo faithfully, and (b) the CDF↔PDF arc's dependency order. Both were handled by stating recovered content plainly and tagging corrections. The one process lesson (answer-position predictability) is a reusable QA check, promoted below.

## Revision history and regression checks

No post-evaluation revision cycles. In-generation corrections (all pre-evaluation): (1) harness heredoc mangled by the shell → re-authored the harness as a file; (2) harness case-sensitivity false positives → fixed the harness (not the artifact); (3) answer-position variety → reordered six options and their keys, then re-ran the full suite (0 failures).

## Decision and approvers

**Final candidate identity at closure:** CAN-2026-0015, `probability-basics-v1.html`, SHA-256 `fa438356badf5b0e40d3929d7ac8317cbaa2e6b6ba4d270e4121cc307991c35d`, 145,525 bytes (1,411 lines)  
**Disposition:** private-pilot-complete  
**Decision scope:** private pilot  
**Approvers and limitations:** repository maintainer (solo Stage 1 operator); non-independent review; ineligible for public release; **degraded-mode Audit 6 (no browser)** — live rendered verification deferred; no screen-reader specialist pass; no second evaluator.

## Memory disposition

- **Promoted:** [MEM-2026-0008](../memory/mem-2026-0008-answer-position-variety.md) — MCQ/gate correct-answer position should vary; a single-session generator reliably parks the correct option at one position. Evidence: this run's Minor defect and in-generation fix.
- **Rejected observations:** (a) "the seeded-cloud widget (W8/W9) deserves its own pattern entry now" — deferred: it reuses P-16's seeded-deterministic discipline; promote after one more reuse. (b) "split U4 (CDF) into the conversion unit" — rejected: the CDF's four properties need their own home before the conversion arc pays off.
- **Carried forward:** the two-panel "area ↔ height" conversion lab as a candidate pattern (P-17) after one more reuse.

## Lineage audit

Source `837a1736…` → SRC-2026-0005 → CM-2026-0013 → LP-2026-0014 → XS-2026-0014 → CAN-2026-0015 (`fa438356…`) → EVAL-2026-0016. All links resolve in-repo; the prompt snapshot is in the appendix; no session-only knowledge is required to reproduce the run.

## Appendix A: Prompt snapshot

User trigger: "lets build interactive lession for 'content/aiml-4/module-02-math-statistics-for-ml/sources/Probability_Basics_(with_CDF_↔_PDF_Conversion).ipynb'"

Workflow directive: governed P0–P6 generation for the Class 5 source — intake and source record (SRC-2026-0005), concept model (CM-2026-0013), learning plan (LP-2026-0014), experience specification (XS-2026-0014), candidate build (CAN-2026-0015), strict verification, six audits, adversarial gate, evaluation authoring, module README update, repository checker, and compounding updates. Generator prompt card `prm-generator-lesson-standard@0.6.0`, SHA-256 `532febec136b15b4988963ad6c5ffb1477163f45013a81fd47474ab6b24c0506` (the card file at [`library/prompts/prm-generator-lesson-standard@0.6.0.md`](../../library/prompts/prm-generator-lesson-standard@0.6.0.md) is the persisted prompt content); orchestrator skill `prm-orchestrator-autonomous@0.1.0`.
