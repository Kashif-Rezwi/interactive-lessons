# RUN-20260907-0001: High-dimensional geometry v1 (first governed generation)

**Status:** Pilot complete  
**Owner:** Repository maintainer (solo Stage 1 operator)  
**Objective:** Governed first generation of the Class 3 interactive notes (high-dimensional geometry) from the source notebook, at benchmark-band depth: full 23-cell source pass, six-unit experience with six ladders, three prediction gates, 8-item confidence-calibrated mastery, four live canvases, and honest dispositions for the source's transcription artifacts.  
**Budget:** One generation; maximum two revision cycles  
**Classification:** production  
**Operating scope:** Stage 1 private pilot  
**Review-independence summary:** non-independent  
**Public-release eligibility:** ineligible

## Input manifest

- Source: [SRC-2026-0003](../sources/src-2026-0003-high-dimensional-geometry.md), SHA-256 `06dd3341d2d65699f172fffba11b271bfd47404cb716d388890cf7cdaa69d63d` (re-verified at intake)
- Concept model: [CM-2026-0010](../concepts/cm-2026-0010-high-dimensional-geometry.md)
- Learning plan: [LP-2026-0011](../plans/lp-2026-0011-high-dimensional-geometry.md)
- Experience specification: [XS-2026-0011](../specifications/xs-2026-0011-high-dimensional-geometry-v1.md)
- Candidate: `CAN-2026-0012`, `high-dimensional-geometry-v1.html`
- Prompt card: `prm-generator-lesson-standard@0.6.0`, digest `532febec136b` (the card file is the persisted prompt content)
- Benchmark: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) (calibration exemplar, per ADR-0011); implementation reference: CAN-2026-0011 (matrix-decompositions v2)

## Generation events

| Time | Candidate ID | Model/configuration | Prompt digests | Cost/latency | Warnings/errors |
| --- | --- | --- | --- | --- | --- |
| 2026-09-07 | CAN-2026-0012 | Cline (Claude Sonnet 4.6), autonomous orchestrator | prm-generator-lesson-standard@0.6.0 `532febec136b` + prm-orchestrator-autonomous@0.1.0 | single session | 2 in-generation corrections (below) |
## Evaluation and defects

### Standing verification audits (P5 Audits 1–6)
- **Audit 1 (Coverage): PASS.** All 23 source cells dispositioned in the coverage matrix (EVAL-2026-0013): cells 1–2 → U0; cell 4 → U1 (FOUNDATION bridges: dimension/feature, embedding, recommender); cells 5–6 → U2 (ε^d and covering-grid formulas; "volume grows exponentially" tightened with tag); cells 7–9 → U3 (Euclidean distance defined; cell 9's opaque base64 figure replaced by the live `distance-lab` canvas, dispositioned as non-reconstructable); cells 10–11 → U4 (corrupted cosine LaTeX corrected with tag; cell 11 experiment replicated live with expected values); cells 12–13 → U5 (N(0,I_d) bridged; `‖x‖≈d` typo corrected to √d with tag); cells 14–23 → U6 (uniformity summary; fixes incl. PCA variance-budget widget; regularization table; normalization LaTeX repaired; attention softmax bridged). No silent drops; full matrix ships in EVAL-2026-0013.
- **Audit 2 (Mathematical & canvas extrema): PASS.** Independent Python closed-form recomputation: 10/10 prose/formula numbers (196,608; 0.01²; 0.01¹⁰; √(1000/6)=12.9099; √1000=31.6228; 1/√2000=2.236%; default variance budget R(2)=85%). All 20 assessment keys re-derived and cross-checked against the page's stored keys within declared tolerances (0 out of tolerance). Gate answers (g1=c, g2=b, g3=c) and MCQ letters re-derived. Seeded PRNG cross-check: the page's `mulberry32` is the canonical algorithm — Node execution of the page's own core matched an independent Python reimplementation exactly for two keys. Live JS core (Node harness) reproduced the exact widget values the browser shows: W3 d=1000 seed 3 → d_min 12.396, d_max 13.613, contrast 0.098 (✓ < 10%); W5 d=1000 seed 1 → mean 31.598 (√1000=31.623), σ/μ ≈ 2.2% (theory 2.24%); W4 cell-11 replication → cosine 0.747/0.757 (theory ≈0.75), Euclidean 13.09/12.77 (theory ≈12.91). Canvas extrema driven live (Audit 6). Zero hard-coded widget outcomes (all readouts live-computed, verified live). PASS.
- **Audit 3 (Dependency order): PASS.** Fresh read-in-order sweep: dimension/feature/embedding/recommender defined in U1 before use; curse/hypercube/coverage defined in U2; Euclidean defined before its concentration use (U3); cosine and dot product defined before the metric table (U4); normalization and the ‖x̂−ŷ‖² identity derived before U6's "normalize embeddings" prescription; N(0, I_d) and Monte-Carlo bridged before U5's widgets; PCA re-referenced as a Class 2 concept with a link (not re-derived); CLT and concentration of measure named in U3 with an explicit forward promise paid off in U5; softmax bridged at first mention (in-generation repair); the source's own ordering defect (cell 8 naming concentration before defining it) repaired with the promise label.

- **Audit 4 (Pedagogical & depth-calibration contract): PASS.** 6 content units in canonical anatomy plus orientation; all 6 computational skills each with a full 3-rung ladder (L1–L6, 12 checkable rungs), tiered never-auto-opening hints (12); 3 prediction gates with commitment-gated unlock and per-option feedback; 2 explain-in-own-words items with model-answer reveals (U3, U5); 8-item interleaved mastery with 3-level confidence tagging and routing; glossary 32 six-field entries with all `data-term` targets resolving (verifier-enforced); branched 12-node concept map present at orientation and revisited in synthesis; callout discipline ≤ 1 per unit (verified); strict assessment modality: 0 `<textarea>`, bounded numeric and MCQ only.
- **Audit 5 (Technical & behavioral): PASS.** `verify-candidate.py --strict`: PASSED (0 failures, 9 notes) — 17/17 range inputs inside `.slider-track`+`.slider-control` (per-element §10.6), 11 formula blocks + 11 symkeys, option stacks (§10.7), body font 16.5px ≥ 16px floor, zero duplicate IDs, zero `<textarea>`, zero external references, colophon-only closing, provenance header present. ADR-0013 contract: 4 canvases, 4 `makeView` occurrences with XS-declared viewports, 4 `resize` listeners (≥ canvas count), DPR `setTransform`, `clientWidth` at draw time, normalized X/Y only, signed-difference angle arc in W4, `.legend-inline` on all 4 canvases. Handler-level behavioral simulation in the live browser — all branches exercised: gate refusal with no selection ("Commit to an answer first"); gate reveal after commitment; differentiated per-option gate feedback; ladder with empty input; MCQ per-option feedback with governing rule; mastery without confidence tag; confident-miss routing (M1 wrong + sure → review list); reset clears the review list; localStorage review persistence across reload (PERSIST-TEST item survived reload); storage fallback note path reviewed in code. PASS.
- **Audit 6 (Rendered-output verification, ADR-0010): PASS — live browser (agent-browser 0.27.0, Chrome/Chromium via CDP).** Zero console messages/errors at load and after full interaction; page title correct; 4 canvases render with backing store (cv2 258×258 at 320px after gate-unlock); 17 range inputs present; body font 16.5px; `document.documentElement.scrollWidth` == `innerWidth` at 1024, 640, and 320 (zero horizontal overflow at all three breakpoints); screenshots captured at 1024/640/320px (evaluator cannot inspect images; all rendered claims rest on measured geometry — the established pattern from RUN-20260904-0001); live interaction traces: gate unlock → canvas drawn with pixels; slider redraw (`{ddim:8, dseed:3}` → d=1000 readout d_min=12.396, d_max=13.613, contrast=0.098 exactly as predicted); W5 `{sdim:6, sseed:1}` → mean 31.598/std 0.695 matching the fixed Node core; W6 variance readout live; reduced-motion emulation resolved `scroll-behavior: auto`; print stylesheet present. No degraded-mode caps.

### Adversarial re-examination (mandatory gate per ADR-0009)

- Re-examination methods: (1) read-in-order dependency re-pass from a fresh perspective (found one first-mention gap — softmax in the attention paragraph — fixed as an in-generation correction); (2) behavioral simulation of edge cases in the live browser (gate refusal, empty ladder input, confident-miss routing, persistence across reload, reset from stored state); (3) canvas-extrema forcing within XS-declared slider ranges (nothing renders off-canvas; signed-arc code path exercised); (4) honesty & provenance scan (provenance header matches RUN identity; colophon-only closing; no release/benchmark/efficacy claims; source-derived numbers reproduced honestly; the three source transcription artifacts each tagged; the cell-11 "≈ 0.75" scoped as a distributional statement, not a single draw; opaque figure replaced and dispositioned).
- Findings and severity: 1 in-generation Major (softmax jargon at first mention), 1 in-generation minor (missing glossary entries `g-clt` / `g-concentration` breaking the verifier). No defect routed to a revision cycle after inspection.

### Re-verification pass (WF-008)

- Sampled checks re-executed after both corrections: strict verifier PASSED (0 failures, 9 notes); answer-key cross-check 20/20; `node --check` on the extracted script PASSED; PRNG cross-check re-run PASSED; 320/640 overflow re-measured (none); affected interaction traces re-run.
- Headline claims reproduced: 0.01²=0.0001 and 0.01¹⁰=1e-20; √1000=31.62; 1/√(2·1000)=2.24%; W3 d=1000 contrast 0.098; W4 seeded cos ≈ 0.75; W6 R(2)=85%.

## Reflection and root-cause hypothesis

Class 3's source was unusually abstract (assertion-heavy, near-zero worked numbers, one opaque figure, three corrupted code blocks). The governed workflow turned it into a measurable, simulated sixth-skill lesson: the additions (ε^d, E‖X−Y‖² = d/6, √d, 1/√(2d), R(k)) were exactly the numbers the source implied but never wrote, each verified by closed form and by live seeded Monte-Carlo. The seeded PRNG (mulberry32) was the keystone: it converted the source's "random" demonstration into exactly reproducible live evidence and made the Node/Python cross-check straightforward. Both in-generation defects were discovered by the standing gates (verifier glossary-resolution check; fresh read-in-order pass) — a confirmation that the standing machinery catches what single-pass authoring misses. Harness lesson: an earlier Node driver consumed PRNG draws building a query vector even for the Gaussian mode, shifting the stream and initially misreading the live widget; the correction (replicate the page's own draw code exactly) reproduced the browser bit-for-bit — a test-harness note, not an artifact defect.

## Revision history and regression checks

- In-generation correction 1: glossary targets `g-clt` / `g-concentration` existed in prose but lacked 6-field entries → added entries; strict verifier + glossary-execution re-run.
- In-generation correction 2: softmax first mention in the U6 attention paragraph without introduction → added a one-line bridge (zero-jargon compliance).
- No post-evaluation revision cycles.

## Memory disposition

- MEM candidate 1 (promote): "reveal-arc durability" — LP-declared reveal arcs with named payoff units survived generation a second time (CAN-2026-0011 and CAN-2026-0012 both ship every planned arc; the U3→U5 concentration payoff resolves in U5 with an explicit award note). Two independent observations → promote as a new memory item.
- MEM candidate 2 (draft, pattern catalog): seeded deterministic PRNG for Monte-Carlo claims (reproducibility + cross-check + honest "seeded run" labeling) — drafted into the pattern catalog as Candidate with this run's evidence; promotion after a second lesson.
- QA checklist: no uncaught defect class; the harness PRNG-consumption note recorded in the evaluation reflection only (observed class is test-harness, not artifact; forward risk noted: trap the next Monte-Carlo lesson's harness from binding the seed derivation to the UI readout).

## Lineage audit

SRC-2026-0003 → CM-2026-0010 → LP-2026-0011 → XS-2026-0011 → CAN-2026-0012 → EVAL-2026-0013. No superseded lineage for this Class 3 package; first generated artifact for the Class 3 source.

## Decision and approvers

**Final candidate identity at closure:** CAN-2026-0012, `high-dimensional-geometry-v1.html`, SHA-256 `534b370053453bc909bb4ce4296c6672389ec51ae55ed6c8e514576b2021e469`, 146,124 bytes  
**Disposition:** private-pilot-complete  
**Decision scope:** private pilot  
**Approvers and limitations:** Repository maintainer (solo Stage 1 operator); non-independent review; public release ineligible; no screen-reader-specialist pass; no second evaluator  
**Iteration counts:** generation = 1; in-generation corrections = 2; revision cycles = 0 (per ADR-0006)

## Appendix A: Verifier + syntax evidence (WF-008/WF-015 persistence)

- `python3 scripts/verify-candidate.py --strict content/aiml-4/module-02-math-statistics-for-ml/generated/high-dimensional-geometry-v1.html` → **Result: PASSED (0 failures, 9 notes)**; elements: 4 canvases, 50 buttons, 106 inputs, 0 textareas, ~32 glossary entries, 3 gates, 6 ladders, 11 formulas; notes: provenance OK, colophon OK, slider-layout OK, slider-encapsulation 17/17, font-floor ≥ 16px, option-layout OK, formula 11 blocks/11 keys, callout discipline OK.
- `grep -c '<textarea'` = 0; duplicate-id check = 0; external-ref check = 0; units = 6; gates = 3; ladder buttons = 12; hints = 12; explain items = 2; mastery items = 8; resize listeners = 4; makeView calls = 4; `node --check` on extracted script = PASS.

## Appendix B: Mathematical execution methods and outputs

- Closed forms (Python): 10/10 prose/formula claims PASS (recomputation of 196,608; 0.01²; 0.01¹⁰; √(1000/6); √1000; 1/√2000; R(2) default).
- Answer keys: 20/20 within declared tolerance (Python re-derivation cross-checked against the page's stored `ans:` values); tolerance-aware, not bitwise — the page stores display-precision values (e.g., 0.707) graded with per-item tolerances.
- PRNG cross-check (Node executing the page's own `mulberry32` core vs independent Python reimplementation): PASS for 2 keys × 8 samples: `[0.56912404, 0.57620116, 0.78674645, 0.85932308, 0.10766108, 0.80528784, 0.62168676, 0.62037071]` identical in both.
- Live widget values (Node core replicating page draw code; verified equivalent output live in browser): W3 d=1 min 0.0027 / max 0.5676 / contrast 211.7; d=10 0.6005 / 1.8761 / 2.124; d=1000 seed 3 12.396 / 13.613 / 0.0982. W4 seed 1 cos 0.7466 / Euclidean 13.090; seed 5 cos 0.7574 / Euclidean 12.765. W5 d=2 seed 1 mean 1.2961 / σ 0.6592 / rel 0.5086; d=1000 seed 1 mean 31.5980 / σ 0.6952 / rel 0.0220.

## Appendix C: Rendered-output evidence (ADR-0010, agent-browser 0.27.0 / CDP)

- console/errors: 0 console messages or errors at launch and after full interaction.
- title: "High-Dimensional Geometry · Interactive Notes v1"; body font: 16.5px; canvases: 4; range inputs: 17.
- `scrollWidth == innerWidth` measured at all three breakpoints: "1280 vs 1280" (default), "640 vs 640", "320 vs 320".
- Gate unlock traces: g1 → w2 display ≠ none, cv2 size 258×258, readout "Covered fraction V(ε,d) = εd …"; g2/g3 → w3/w4 visible, cv3/cv4 backing store > 0.
- Slider traces: `ddim=8; dseed=3` → r3: "d = 1000 … d_min = 12.396 · d_max = 13.613 … Contrast … = 0.098"; `sdim=6; sseed=1` → r5: "mean ‖x‖ = 31.598 … σ/μ = 2.2% vs theory 1/√(2d) = 2.24% … within mean ± 2·std: 69%".
- Mastery routing: m1 wrong + sure → "feedback no … Confident miss: M1 — go back"; reset → "Nothing queued — clear the checks above and see."
- Persistence: localStorage `hdg1-review` set → reload → review list renders the stored item.
- Refusal branches: gate with cleared selection → "Commit to an answer first — that commitment is what makes the reveal worth it."; ladder empty input → "Enter a number first."; mastery without confidence → "Also tag your confidence (sure / think so / guessing)…".
- Reduced-motion: emulated; computed `scroll-behavior` = "auto". Screenshots saved at 1024/640/320px (evaluator has no image input; measured geometry is the evidence of record).

## Appendix D: Prompt snapshot

User trigger: "hey lets use the repo setup to build interactive notes for this [file: High_Dimensional_Geometry.ipynb]"

Workflow directive: governed P0–P6 lesson generation for the Class 3 source — SRC (intake + hash), CM (anchored claims + misconceptions), LP (6 units + orientation, depth pass, 3 prediction gates, 2 explain items, 8-item mastery), XS (6 widgets: W1/W6 numeric with reason, W2/W3/W4/W5 canvases with declared viewports), single file per prompt card @0.6.0, strict verification, six audits, adversarial gate, evaluation authoring, module README update, repository checker, and compounding asset updates. Generator prompt card `prm-generator-lesson-standard@0.6.0`, SHA-256 `532febec136b15b4988963ad6c5ffb1477163f45013a81fd47474ab6b24c0506` (the card file is the persisted prompt content); orchestrator skill `prm-orchestrator-autonomous@0.1.0`.
