# MEM-2026-0005: Canvas responsiveness collapse and design system drift — rules without implementation contracts produce pedagogically complete but technically broken artifacts

**Status:** Supported
**Curator:** Repository maintainer (solo Stage 1 operator)
**Created / review date:** 2026-08-15; amended 2026-09-29 (iteration 2)
**Scope:** Interactive lesson generation and evaluation in Learning OS (Stage 1 pipeline)
**Tags:** canvas-engineering, design-system, prompt-design, quality-gate, implementation-contract, workflow
**Evidence records:** [EVAL-2026-0007](../evaluations/eval-2026-0007-linear-algebra-foundations-v4-v7-qa-design-audit.md), [RUN-20260815-0001](../runs/run-20260815-0001-linear-algebra-foundations-v7.md), [EVAL-2026-0006](../evaluations/eval-2026-0006-linear-algebra-foundations-v7.md), [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md), [RUN-20260929-0001](../runs/run-20260929-0001-multivariate-calculus-v2.md) (revision 1), [EVAL-2026-0015](../evaluations/eval-2026-0015-multivariate-calculus-v2.md)
**Supersedes / conflicts-with:** none (Iterations 1–2; iteration 2 amends)

## Lesson

The 2026-08-15 reproduction run built CAN-2026-0006 (v7) from the unchanged source (SRC-2026-0001) under `prm-generator-lesson-standard@0.4.0` with full depth-bar and spec-conformance duties. The candidate passed all six P5 audits and the adversarial gate with zero Major/Critical findings, scored 3.58 weighted (non-independent, degraded-mode Audit 6), and closed as `private-pilot-complete`. A subsequent independent QA and design audit (EVAL-2026-0007) compared v7 against the v4 benchmark and found **severe implementation regressions** that every existing gate missed:

- **Canvas architecture collapse (P0):** v7's `cv()` helper reads static HTML `width`/`height` attributes (always 640×360) and applies DPR once at load. Zero `window.addEventListener("resize", draw)` listeners exist across all 13 canvas widgets. When the browser window resizes or the container differs from 640px, the CSS `width: 100%; height: auto` stretches/squashes the canvas bitmap, causing blurry lines, misaligned labels, and severe distortion. v4 uses a responsive `makeView()` pattern that measures `clientWidth` at every draw, applies DPR scaling dynamically, and attaches resize listeners to all widgets (8 found).
- **Generic projection (P0):** v7 uses a single `plot(ctx, w, h, range)` helper computing `s = Math.min(w, h) / (2 * range)`. All canvases are 640×360, so the scale is always height-constrained, wasting horizontal space. v4 uses per-widget `makeView(id, xMin, xMax, yMin, yMax)` with tailored aspect ratios.
- **Hardcoded pixel offsets (P0):** The least-squares lab (W12) uses `px = function(x){ return 50 + x * (W - 75) / 5 }` — hardcoded offsets that break with any container width change.
- **Angular arc bug (P0):** The dot product lab (W7) uses `Math.max`/`Math.min` on angles, drawing the reflex angle when vectors cross quadrant boundaries. v4 uses signed angular difference with wrapping.
- **Design system drift (P1):** v7 loses the frosted-glass sticky nav (`backdrop-filter: blur(6px)` → solid white), uses `flex-wrap: wrap` causing multi-line nav wrapping, drops the `[aria-current]` active-state styling, centers the header (v4 left-aligns), removes metadata chips, drops inline color legends (`.legend-inline`), uses terse single-letter slider labels, reduces design tokens from 22+ to 14, and removes `-webkit-font-smoothing: antialiased`.

## Why this is believed

- Direct artifact comparison v4 ↔ v7 with line-level citations: v4 `makeView` at lines 1170–1183 vs v7 `cv()` at line 1239; v4 resize listeners (8 found) vs v7 (zero); v4 `.legend-inline` elements (7 found) vs v7 (zero); v4 `backdrop-filter: blur(6px)` at line 46 vs v7 solid `background: var(--card)` at line 26.
- The generation prompt (@0.4.0, item 7) lists "canvas text equivalents; reduced-motion; print fallbacks" but **never specifies canvas responsiveness, DPR scaling, resize handling, or coordinate projection contracts**. The prompt names design categories ("ink/paper/line neutrals + one accent") but does not pin specific values or require specific design features.
- The QA checklist (pre-2026-08-15) has no canvas responsiveness checks, no design token conformance checks, no nav design contract checks, and no widget label quality checks. The audits verified *pedagogical* correctness (depth, gates, ladders, assessment) but not *implementation* correctness (canvas architecture, design system).
- The six audits passed with a clean adversarial gate because the checklist's canvas checks (Audit 2) verify extrema bounds (no off-canvas rendering) but not the responsive viewport contract. The artifact is *mathematically correct* but *technically broken* for real browser conditions.

## Iteration 2 (2026-09-29) — partial rule restoration and state styling no gate could see

The Class 4 lineage (CAN-2026-0013 → CAN-2026-0014; RUN-20260924-0001 → RUN-20260929-0001) shipped through a full six-audit pass and rendered verification with a group of interaction-state styles missing: `.feedback.ok`/`.feedback.no` (all graded feedback rendered as bare text), the base `.callout` rule (only the inert `.callout.good`/`.callout.info` overrides existed, so all six callout blocks rendered as plain prose), `.gloss-list`, and the `.mastery` markup wrapper. Root cause: the v1 assembly incident dropped a block of stylesheet-tail rules and the repair restored only the two rules it noticed; the v2 rebuild carried the design system verbatim. Every gate passed because they are text-, presence-, or assignment-level — a `className="feedback no"` in the DOM is invisible to them — and the module's other lessons ship different, complete state families (Class 1: `.fb.ok/.fb.no/.fb.note`; Classes 2–3: `.feedback.ok/.no`), so the gap existed only in this lineage and looked like a platform-wide non-issue.

A learner reported the symptom (a wrong-answer Check rendering as unstyled text beside a styled Hint box). Revision 1 restored the rules (text verbatim from the sibling lessons), added an amber `.feedback.note` refusal state and `✓`/`✗` glyphs, and re-verified end-to-end: the new `scripts/verify-candidate.py` state-styling check was proven to fail on the pre-fix bytes and pass on the remediated bytes, and 27/27 browser computed-style assertions passed with zero page/console errors.

**Iteration-2 rules:** (1) a state class assigned by script is a visual contract — DOM presence is not a rendered state, and only computed-style evidence closes it; (2) partial restoration of displaced rules must verify the whole lost group, not the rules that happened to be noticed; (3) identical-symptom absence across sibling lessons is not evidence of correctness when those lessons use different mechanisms.

## Recommended action

1. **Canvas engineering standard** (`docs/01-product/canvas-engineering-standard.md`, ADR-0013): codifies the responsive `makeView` pattern, per-widget viewport declaration, resize listener requirement, normalized transform contract, color legend contract, and angular arc computation rule.
2. **Design system contract** (lesson standard §10.1–10.4): pins the design token set with specific values, establishes the navigation design contract (frosted glass, single-line scroll, pill links, active state), the header design contract (left-aligned, metadata chips), and the widget label quality rule (descriptive mathematical labels).
3. **Prompt card @0.5.0**: adds the canvas engineering clause (item 7), the design system clause (item 8), and the canvas/design conformance sweep (item 15).
4. **QA checklist**: Audit 5 gains ten new checks covering canvas responsiveness, resize listeners, normalized transforms, per-widget viewport, color legends, angular arcs, design token conformance, nav design contract, header design contract, and widget label quality.
5. **XS template**: gains per-widget viewport range declaration (`xMin/xMax/yMin/yMax`).
6. **SKILL.md**: P4 gains a canvas engineering verification step (grep-based checks for resize listeners, clientWidth, hardcoded offsets, legends, token count, nav contract).
7. **Revision 1 (2026-09-29) — state-styling coverage:** QA checklist Audit 5 gains the interaction-state styling coverage item and Audit 6 the state-styling computed-style check; `scripts/verify-candidate.py` gains the mechanical state-styling check; the Class 4 artifact was remediated in place as CAN-2026-0014 revision 1 (no new candidate ID).

## Counterexamples and limitations

- The canvas engineering standard codifies the *pattern* from v4 but does not build a shared JavaScript library — that remains Stage 2+ scope (ADR-0013, Option B rejected).
- Design token values are pinned as *defaults*; a lesson may adjust them with documented rationale in the XS record. The standard prevents *accidental* drift, not *deliberate* variation.
- The v7 regressions were caught by a *human-initiated* comparative audit (EVAL-2026-0007), not by the pipeline's own gates. The new checks are designed to catch these classes at P5, but their effectiveness is unproven until the next governed generation run.
- Evidence comes from one source package and non-independent review; the "degraded mode" Audit 6 (no browser) meant the canvas defects were invisible to the pipeline's own verification.
- **Iteration 2 caveats:** the state-styling defect was found by a learner after two full verification passes; the new mechanical check closes the named contract classes (`.feedback.ok/.no`, base-before-variant rules) while the generic class-token sweep stays note-level. v1 of the Class 4 lesson remains frozen with the same missing rules (historical artifact), and the Class 1–3 lessons under-implement the §10.1 `✓`/`✗` marker — candidates for a future platform-consistency pass, not retroactive edits.

## Retrieval guidance

Consult at P3 (XS authoring — declare per-widget viewport ranges), at P4 generation (prompt card ≥ 0.5.0; canvas engineering verification step), and at P5 (were the canvas/design checks executed with evidence?). At P5/P6 (iteration 2), additionally require computed-style evidence for every graded state and group-level verification of any displaced-rule restoration. Pair with MEM-2026-0004 (compliant-minimum collapse — the pedagogical analog of this implementation-level failure) and MEM-2026-0003 (structural checks cannot see dynamic defects — the canvas responsiveness contract is a *dynamic* property).

## Privacy and retention

No personal data; retain as a standing generation/audit guard until superseded by comparison-run evidence.