# LP-2026-0011: Learning plan for high-dimensional geometry v1

**Status:** Reviewed  
**Supersedes / iteration position:** Iteration 1 — original  
**Owner:** Repository maintainer  
**Concept model:** [CM-2026-0010](../concepts/cm-2026-0010-high-dimensional-geometry.md)  
**Target learner and prerequisites:** AIML-4 learner who completed Class 1 (vectors, dot products, norms, mean/variance) and Class 2 (SVD, PCA, singular values — vocabulary re-used, not re-derived); comfortable with algebra; no prior probability beyond basic distributions  
**Source and claim links:** [SRC-2026-0003](../sources/src-2026-0003-high-dimensional-geometry.md); claims CM-2026-0010 #1–44

## Measurable learning outcomes

The learner can: (1) compute the dimensionality of real data objects and explain why modern ML is inherently high-dimensional; (2) compute the covered volume fraction ε^d and the covering-grid size (1/ε)^d, and state the sample-complexity consequence; (3) demonstrate distance concentration via a live simulation and explain its sum-of-random-contributions mechanism; (4) compute Euclidean distance and cosine similarity, explain why cosine is magnitude-blind, and use ‖x̂ − ŷ‖² = 2 − 2cos θ to connect the two; (5) predict ‖x‖ ≈ √d for Gaussian vectors and quantify the thin shell via relative spread ≈ 1/√(2d); (6) select appropriate fixes (feature selection, PCA variance budget, regularization, normalization) for named high-d failure modes and connect them to honest ML systems (KNN, clustering, vector search, RAG).

## Sequence and rationale

U0 Orientation (how to learn with the page, labels, loop, concept map) → U1 The dimensionality of everything (real systems' dims; d = w·h·c) → U2 The curse of dimensionality (ε^d collapse, covering-grid explosion, sparsity, sample complexity) → U3 Distance concentration (Euclidean defined, Monte-Carlo distance histogram, contrast ratio, sum-of-contributions mechanism, KNN failure) → U4 Metric choice (cosine defined, magnitude-blindness, positive-orthant replication of cell 11, ‖x̂−ŷ‖² = 2−2cos θ payoff of the metric bridge) → U5 Concentration of measure (N(0, I_d) bridged, norm concentration √d, thin shell; pays off U3's forward promise and explains U3's phenomenon) → U6 From curse to craft (implications and fixes; ML LINK close: semantic embeddings, attention, latent spaces, RAG, vector DBs) → Synthesis + mastery → review list → glossary. Rationale: concentration phenomena (U3) are stated before their explanation (U5) exactly as the source motivates them, but the promise is explicit and paid off; the metric discussion (U4) sits between the phenomenon and its explanation because cosine's stability is itself a consequence of normalization that U5's shell explains. Application names appear only after the mechanism they use.

## Teaching strategy and cognitive-load choices

One visual metaphor throughout: *high-dimensional space is mostly empty, and everything in it looks the same distance from everything else*. Depth pass per unit:

| Unit | Lede | Signature visual (P-14) | Reveal arcs (P-15) | Misconception callouts (≤1/unit) | Computational skills → ladders |
|---|---|---|---|---|---|
| U0 | Learn how the page teaches before the math starts. | Branched concept map (SVG) | — | — | — |
| U1 | Every image, sentence, and click is already a point in a huge space. | `dim-calc` numeric widget (w·h·c live) | "Your data is already high-dimensional" setup → payoff in U6 (vector search runs on exactly these vectors) | "More features always help" | L1 dimensionality arithmetic |
| U2 | Cover a fixed slice of every axis and the covered space vanishes. | `volume-collapse` canvas: unit square with inner ε-box + log bar of ε^d | ε^d setup → payoff in U3 (empty space is why neighbors are far) | "The cube itself grows" (it stays volume 1; the grid explodes) | L2 covered-fraction arithmetic |
| U3 | In high dimensions, nearest and farthest look the same. | `distance-lab` canvas: Monte-Carlo distance histogram, nearest/farthest markers, contrast readout | Forward promise: "U5 explains why this happens" → paid off in U5 | "Points repel each other" (no-mechanism story) | L3 expected-distance arithmetic |
| U4 | Cosine compares direction and ignores magnitude. | `metric-lab` canvas: two vectors, angle + length sliders, live cos/euclidean/dot | Setup: cosine ignores length → payoff immediately (‖x̂−ŷ‖² = 2−2cos θ identity) + in U6 (normalized vector search) | "Cosine depends on magnitude" | L4 cosine computation |
| U5 | Random high-d vectors all have nearly the same length. | `shell-lab` canvas: live norm histogram vs √d marker, relative-spread readout | Pays off U3's promise; thin shell explains distance concentration and normalization | "‖x‖ ≈ d" (source typo; √d is the truth, verified live) | L5 √d norm estimate |
| U6 | Know the failure, pick the fix, and see where modern AI leans on the geometry. | `variance-budget` numeric widget (retained variance from λᵢ, k) | U1's setup pays off (embeddings/vector search/RAG); U4's cosine payoff lands in vector search | "More dimensions reduce overfitting" (backwards) | L6 retained-variance fraction |

Prediction gates (P-01, 3 total): G1 in U2 (covering 10% per axis in 6-D: options 10% / 60% / 0.0001%), G2 in U3 (nearest/farthest ratio at d = 1000: options "much less than 1" / "close to 1" / "much greater than 1"), G3 in U4 (cosine of two random 1000-dim [0,1] vectors: options ≈0 / ≈0.5 / ≈0.75). Gates hide the manipulable until commitment; per-option feedback differentiated by choice; governing rule stated in every feedback.

Explain-in-own-words items (≥2, with model-answer reveals and self-evaluation, no textareas): U3 "why do distances concentrate when you sum many small random contributions" and U5 "why does the thin shell explain distance concentration". Explain-item placement is inside the unit Check blocks.

Mastery check: 8 items (≈ 6 content units + 2), interleaved across units, with 3-level confidence tags (sure / think so / guessing) and confident misses routed to the persistent review list; includes reasoning items (why √d not d; why cosine survives), transfer items (a 512×512 grayscale image sensor; a music-recommendation embedding store), and one error-identification item (find the flaw in a "keep all features + Euclidean KNN" pipeline proposal). No worked numbers reused.

Additional-knowledge triage: must-add bridges — variance of uniform [0,1] (1/12), linearity of expectation, E[(X−Y)²] = 2σ², standard Gaussian N(0, I_d), Monte-Carlo sampling, unit vector/normalization identity ‖x̂−ŷ‖² = 2−2cos θ. Should — softmax one-liner (attention), ANN-search one-liner (vector DBs). Could (collapsed EXTENSION) — Lévy's lemma name; Berry–Esseen; HNSW/LSH index families. Do-not-add — measure-theoretic proofs, transformer architecture internals, differential geometry of manifolds.

Calibration: [BMK-2026-0001](../benchmarks/bmk-2026-0001-linear-algebra-foundations-v4.md) is the active depth exemplar; the Class 2 v2 lesson (CAN-2026-0011) is the implementation reference for component contracts.

## Assessment and evidence of learning

Every unit check has ≥1 constructed-response numeric item (auto-graded with tolerance) plus at least one diagnostic MCQ with per-option misconception feedback; feedback on every miss states the governing rule. Ladders L1–L6 each have 3 rungs with tiered, never-auto-opening hints. Mastery M1–M8 with confidence routing. Persistence: cleared checks fill nav completion dots; misses and confident mastery misses enter a localStorage review list with a spacing invitation and visible reset (graceful fallback when storage is unavailable).

## Accessibility and inclusion intent

Native controls only; keyboard-operable sliders/options; every canvas pairs a text readout with the same numbers and a `.legend-inline` legend; color never the sole encoder; `prefers-reduced-motion` honored; measured WCAG AA contrast; print fallback exposes explanations and hides controls; 16px font floor at all breakpoints.

## Acceptance criteria and review boundary

Strict mechanical verification (`verify-candidate.py`, 0 failures); independent Python recomputation of every displayed number and distribution claim; Node cross-check of the page's live JS math core; dependency-order read-through; six audits + adversarial gate per ADR-0009; rendered browser verification at 320/640/1024px per ADR-0010; repository checker exit 0. Status remains private-pilot-complete, non-independent, ineligible for public release.

## Conformance checklist (depth-calibration contract)

- [x] Active benchmark BMK-2026-0001 cited as calibration exemplar
- [x] Depth-pass table complete for every unit (lede, signature visual, reveal arcs with payoff units, misconception callouts, ladders per skill)
- [x] One full 3-rung faded ladder planned for each of the 6 computational skills (L1–L6)
- [x] ≥ 2 explain-in-own-words items with model-answer reveals allocated (U3, U5)
- [x] Every forward promise / reveal arc names its explicit payoff unit
