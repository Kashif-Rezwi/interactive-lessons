# RUN-20261006-0002: Probability basics v2 (Class 5 deepening)

**Status:** Pilot complete
**Parent run:** [RUN-20261006-0001](run-20261006-0001-probability-basics-v1.md) (v1, same source)
**Owner:** Repository maintainer (solo Stage 1 operator)
**Objective:** Deepen the Class 5 interactive lesson beyond v1 at benchmark-band depth from [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md): keep the nine teaching units and the verified v1 design system, and add (a) a two-point fundamental-theorem lab (W10) and a discrete PMF-recovery staircase lab (W11) in U5, (b) a Gaussian mean/width bell lab (W12) in U9, (c) continuous-expectation (L7) and continuous-variance (L8) ladders, (d) two mastery items (M12 transfer, M13 reasoning) for a 13-item mastery, and (e) three glossary terms (second moment, 68–95 rule, two-point conversion); all readouts computed live; nothing hard-codes what can be computed.
**Budget:** One generation; maximum two revision cycles
**Iteration counts:** generation = 1; in-generation corrections = 3 (one editor payload-size split; one storage-namespace rename `prob1-*` → `prob2-*`; one M12 value re-derived from a fresh CDF F=x⁴ to avoid reusing the M3 worked number) ; revision cycles = 0 (per [ADR-0006](../../docs/adr/0006-record-iteration-accounting.md))
**Classification:** production
**Operating scope:** Stage 1 private pilot
**Review-independence summary:** non-independent
**Public-release eligibility:** ineligible

## Input manifest

- Source: [SRC-2026-0005](../sources/src-2026-0005-probability-basics.md), SHA-256 `837a1736e4286cf6b8b0d91792dd6611162dfb811332860a5dfca67fc60fd0ac`
- Concept model: [CM-2026-0014](../concepts/cm-2026-0014-probability-basics.md) (41 anchored claims — the 38 v1 claims plus 3 deepening claims; 37 concepts; 10 misconceptions)
- Learning plan: [LP-2026-0015](../plans/lp-2026-0015-probability-basics.md) (9 units + orientation; L1–L8; 13-item mastery; depth-pass table)
- Experience specification: [XS-2026-0015](../specifications/xs-2026-0015-probability-basics-v2.md) (12 canvas widgets W1–W12; 3 gates; 8 ladders; EQ-001–EQ-023; 45-term registry)
- Candidate: `CAN-2026-0016`, `probability-basics-v2.html`
- Prompt card: `prm-generator-lesson-standard@0.6.0`, digest `532febec136b` (the card file is the persisted prompt content)
- Benchmark: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) (calibration exemplar, per [ADR-0011](../../docs/adr/0011-benchmark-definition-and-artifact-change-protocol.md)); implementation reference: CAN-2026-0014 (`multivariate-calculus-v2.html`) and the v1 candidate CAN-2026-0015
- Tooling: `scripts/verify-candidate.py` (strict), `scripts/check-repo.py`, Python 3 harness (numeric recomputation + answer-key cross-check), Node (`node --check` + stub-DOM draw smoke test), headless Google Chrome (rendered verification)

## Generation events

| Time | Candidate ID | Model/configuration | Prompt digests | Cost/latency | Warnings/errors |
| --- | --- | --- | --- | --- | --- |
| 2026-10-06 | CAN-2026-0016 | Cline (Claude Sonnet 4.6), autonomous orchestrator | prm-generator-lesson-standard@0.6.0 `532febec136b` + prm-orchestrator-autonomous@0.1.0 | single session | 3 in-generation corrections (editor payload split; storage-namespace rename; M12 value re-derived); 0 assembly incidents |

**Generation method:** single-session superset build — copy the verified v1 artifact, rename its storage namespace, and add the deepening surfaces (W10–W12 markup + draw functions, L7–L8, M12–M13, three glossary entries, slider/resize wiring), reusing the module's verified design system (tokens, nav, `makeView`, storage/gates/ladders/checks/mastery contracts) unchanged. Every surface verified on the final hash.

## Evaluation and defects

### Standing verification audits (P5 Audits 1–6)
- **Audit 1 (Coverage):** all 61 source cells still mapped (the v2 coverage matrix extends the v1 matrix); the three new CM claims (#39 two-point theorem, #40 second moment, #41 Gaussian 68–95) each have a live element (W10, the U7 second-moment prose + EQ-023, W12). No silent drops.
- **Audit 2 (Mathematical & canvas extrema):** every new answer key recomputed independently — L7 (2/3≈0.667, 0.5, 0.75), L8 (1/18≈0.083, 1/12≈0.083, 0.0375), M12 (0.8⁴−0.3⁴=0.4015); the W10 readout shows area = F(b)−F(a) as one number; W11 shows F(x)−F(x⁻)=1/6; W12 peak = 1/(σ√(2π)). Extrema forced: a==b → 0; x=1 or 6 on the staircase; σ=0.4 and 2.5.
- **Audit 3 (Dependency order):** read-in-order sweep confirms W10/W11 (U5) follow the PDF, CDF, and the fundamental theorem; L7 follows the expectation definition; L8 follows the variance definition; W12 follows the Gaussian density.
- **Audit 4 (Pedagogical & depth-calibration contract):** 8 ladders (all 3-rung), 3 gates, 13-item confidence-tagged mastery, 2 explain-in-own-words items, 45-term glossary, branched concept map, per-unit ledes and reveal arcs (LP-2026-0015).
- **Audit 5 (Technical & behavioral simulation):** `verify-candidate.py --strict` 0 failures; `node --check` clean; Node stub-DOM executes all 12 draw functions with 0 exceptions; no duplicate IDs; all `data-target`/`data-term` wiring resolves.
- **Audit 6 (Rendered-output verification per [ADR-0010](../../docs/adr/0010-rendered-output-verification.md)):** performed with headless Google Chrome. 0 page console errors; the new readouts (`r10`, `r11`, `r12`) populated live in the dumped DOM; screenshots captured at 320/640/1024px. **Limitation:** headless Chrome without device-metrics emulation enforced a minimum layout width, so the 320px capture was a crop of a wider layout and matched the v1 baseline byte-for-byte in its clipping — the true 320px mobile breakpoint was therefore not exercised; 500/640/1024px rendered cleanly with no clipping.

### Adversarial re-examination (mandatory gate per [ADR-0009](../../docs/adr/0009-forced-adversarial-re-examination-gate.md))
- Re-examination method(s): read-in-order fresh re-pass; behavioral simulation of handler edge cases; canvas-extrema forcing; honesty/provenance scan.
- Elements covered: gate commitment bypass (G1–G3 unchanged, still hide the widget until a committed answer and differentiate per choice); grading boundaries (L7/L8/M12 tolerances checked against exact values — e.g. L8 r2 answer 1/12 stored as 0.083 with tol 0.005 covers 0.0833); confident-miss routing (M12/M13 route to the `prob2-review` list when wrong *and* `sure`); reset from corrupted localStorage (the `prob2-*` keys parse-guarded; a corrupted value falls back to defaults); canvas extrema (W10 a==b → 0; W11 x=1 and x=6; W12 σ=0.4 and σ=2.5 → peak 0.997 and 0.160); honesty scan (no release/benchmark/efficacy claims; provenance header updated to CAN-2026-0016 / RUN-20261006-0002 / CM-2026-0014 / LP-2026-0015 / XS-2026-0015; colophon unchanged).
- Findings & severity: clean pass with documented evidence. One Minor observation — the W12 canvas renders short-and-wide (64px tall at 1024px width) because its mathematical viewport (12 wide × 1.1 tall) sets the aspect ratio; this matches the module's existing wide-plot convention (W1 renders 61px tall) and is not a defect.

### Re-verification pass (WF-008)
- Sampled checks re-executed: strict verifier (0 failures); Node draw smoke (12/12 clean); headless render (0 console errors; new readouts populated).
- Headline claims reproduced: yes — the two-point identity, the PMF-recovery identity, and the Gaussian peak all reproduce exactly.

## Reflection and root-cause hypothesis

The deepening was designed as a **superset** rather than a regeneration: the v1 artifact already conformed to the canonical skeleton (post-revision 1) and passed every check, so the cheapest correct path was to extend it, reusing the design system verbatim and changing only the storage namespace (to keep v2 progress independent of v1). This avoided re-introducing the skeleton-drift class that MEM-2026-0009 documents. The main risks were (a) reusing a worked number across assessment items (mitigated by choosing F=x⁴ for M12) and (b) an under-verified new canvas (mitigated by the extrema forcing in the adversarial pass). The one real limitation is environmental: true 320px mobile emulation is unavailable in the plain headless-Chrome harness, so that breakpoint remains structurally (not visually) verified.

## Revision history and regression checks

No post-evaluation revision. In-generation corrections (all pre-evaluation): (1) the first CM/LP/XS editor payloads exceeded the tool's 6 000-character recommendation and were split; (2) the copied v1 storage namespace `prob1-*` was renamed to `prob2-*` before any other edit; (3) the M12 mastery number was re-derived from F=x⁴ (0.4015) rather than reusing the M3 F=x³ worked value. Regression checks on the final hash: `verify-candidate.py --strict` 0 failures; `node --check` clean; stub-DOM draw smoke 12/12 clean; headless render 0 console errors.

## Decision and approvers

**Final candidate identity at closure:** CAN-2026-0016, `probability-basics-v2.html`, SHA-256 `c37befb55ae2703126b8c5e4c30f257e6816db9b444dc197a2326cc20f458b69`, 166,370 bytes (1,621 lines) — single build
**Disposition:** private-pilot-complete
**Decision scope:** private pilot
**Approvers and limitations:** repository maintainer (solo Stage 1 operator); non-independent review; ineligible for public release; rendered verification performed at 500/640/1024px but the true 320px mobile breakpoint is unverified (headless-harness limitation); no screen-reader specialist pass; no second evaluator.

## Memory disposition

- **Promoted:** [MEM-2026-0010](../memory/mem-2026-0010-superset-deepening.md) — deepen a conformant lesson by a verified **superset** (reuse the design system, extend with labs/ladders/mastery, rename the storage namespace) rather than regenerating; it avoids re-introducing the skeleton-drift class (MEM-2026-0009). Evidence: this run.
- **Rejected observations:** (a) "give W10 a prediction gate too" — rejected: G2 already tests the area-vs-height idea in U5; a second gate in one unit dilutes the commitment signal. (b) "split U5 into two units (conversion, then two-point/discrete)" — rejected: the two-point and discrete forms are the *same* theorem; keeping them in U5 preserves the reveal arc.
- **Carried forward:** the two-point conversion lab (W10) as a candidate pattern after one more reuse; the Gaussian shape lab (W12) as a reusable "parameter→shape" pattern.

## Lineage audit

Source `837a1736…` → SRC-2026-0005 → CM-2026-0014 (extends CM-2026-0013) → LP-2026-0015 → XS-2026-0015 → CAN-2026-0016 (`c37befb5…`) → EVAL-2026-0017. All links resolve in-repo; the prompt snapshot is in the appendix; no session-only knowledge is required to reproduce the run.

## Appendix A: Prompt snapshot

User trigger: "lets build interactive lession for 'content/aiml-4/module-02-math-statistics-for-ml/sources/Probability_Basics_(with_CDF_↔_PDF_Conversion).ipynb'".

Workflow directive: governed P0–P6 generation for the Class 5 source, v2 deepening iteration. On discovering the complete, verified v1 pipeline (SRC-2026-0005 / CM-2026-0013 / LP-2026-0014 / XS-2026-0014 / CAN-2026-0015 / EVAL-2026-0016), the user selected the **improved v2** option: a new candidate plus new governed records that deepen the lesson beyond v1. Generator prompt card `prm-generator-lesson-standard@0.6.0`, SHA-256 `532febec136b15b4988963ad6c5ffb1477163f45013a81fd47474ab6b24c0506` (the card file at [`library/prompts/prm-generator-lesson-standard@0.6.0.md`](../../library/prompts/prm-generator-lesson-standard@0.6.0.md) is the persisted prompt content); orchestrator skill `prm-orchestrator-autonomous@0.1.0`.
