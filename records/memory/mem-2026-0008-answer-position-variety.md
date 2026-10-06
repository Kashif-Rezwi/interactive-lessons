# MEM-2026-0008: Vary the correct-answer position across diagnostic options

**Confidence:** Tentative
**Curator:** Repository maintainer (solo Stage 1 operator)
**Created / review date:** 2026-10-06
**Scope:** Lesson generation (P4) and QA (P5 Audit 4/5) in the Learning OS Stage 1 pipeline
**Tags:** assessment, mcq, option-stack, answer-position, generation-bias
**Evidence records:** [RUN-20261006-0001](../runs/run-20261006-0001-probability-basics-v1.md), [EVAL-2026-0016](../evaluations/eval-2026-0016-probability-basics-v1.md)
**Supersedes / conflicts with:** none (Iteration 1 — original); strengthens the MCQ item of the [lesson QA checklist](../../library/rubrics/lesson-qa-checklist.md) and P-01 in the pattern catalog

## Lesson

When a single session authors many diagnostic MCQs and prediction gates, the correct option tends to land at the same position. In CAN-2026-0015 all nine unit-check MCQs and all three gates had the correct answer at position **b** — a pattern a learner could exploit without understanding, which weakens the assessment even though every distractor and rule was correct. The defect was caught by the adversarial gate's fresh-perspective sweep (not by any mechanical check, since option position is invisible to `verify-candidate.py`) and fixed in-generation by reordering six items so the correct position varied across a/b/c.

**The lesson:** answer-position variety is a per-lesson property that a text-level QA pass does not see; it must be checked by reading the rendered option order (or by a dedicated positional tally), and the generator should deliberately distribute the correct option across positions.

## Why this is believed

- One concrete observation: the CAN-2026-0015 draft had 12/12 correct answers at position b; the fix reordered six of them and the suite re-passed (0 failures).
- The mechanism is a known authoring bias (default-first-correct drafting) and is not caught by mechanical structure checks.

## Recommended action

1. Add a QA-checklist item (Audit 4/5): tally the correct-answer position across all MCQs and gates; flag if any single position exceeds ~60% of items.
2. Generate options with the correct answer deliberately placed at varying positions (rotate a/b/c).
3. Promote to `Supported` after a second confirming lesson; `Established` after a third.
