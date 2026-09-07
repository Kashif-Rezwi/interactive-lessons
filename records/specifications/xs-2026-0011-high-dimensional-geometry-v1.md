# XS-2026-0011: Interactive notes candidate high-dimensional geometry v1

**Status:** Approved  
**Approval scope:** Stage 1 governed generation  
**Supersedes / iteration position:** Iteration 1 — original  
**Source concept model:** [CM-2026-0010](../concepts/cm-2026-0010-high-dimensional-geometry.md)  
**Learning plan:** [LP-2026-0011](../plans/lp-2026-0011-high-dimensional-geometry.md)  
**Target learner:** AIML-4 student, post-Class-1 and post-Class-2 (vectors, dot products, norms, mean/variance; SVD/PCA vocabulary)  
**Artifact family:** Single-file offline HTML  
**Learning outcomes:** per LP-2026-0011 §Measurable learning outcomes (6 outcomes, each exercised by ≥1 assessment item)

## Learner problem and teaching strategy

The source is a wide, assertion-heavy agenda with almost no worked numbers and one opaque figure. The artifact turns it into an explain-before-use path: orientation unit, six units in canonical anatomy (Learn → Predict → Explore → Practice → Check → Connect), synthesis with interleaved mastery, persistent review list, glossary. One visual metaphor throughout: high-dimensional space is mostly empty and everything in it looks equally far. All readouts are computed live in the page; nothing hard-codes what can be computed. Monte-Carlo widgets use a seeded, deterministic PRNG (mulberry32) so every displayed number is exactly reproducible offline.

## Content and evidence map

U0 cells 1–2 (agenda → orientation); U1 cell 4 (dimensionality of images/embeddings/recsys; d = w·h·c; "intuition breaks" claim) + FOUNDATION bridge (a feature = one coordinate); U2 cells 5–6 (curse definition, ε^d collapse, covering-grid explosion, sparsity, sample-complexity sketch; source phrasing "volume grows exponentially" tightened with tag); U3 cells 7–9 (distance concentration, contrast collapse, mechanism, KNN failure; Euclidean distance defined; cell 9's opaque figure replaced by the live `distance-lab` canvas, dispositioned); U4 cells 10–11 (corrupted cosine LaTeX repaired with tag; Euclidean problems; cosine similarity; metric comparison table; cell 11 experiment replicated live with expected values); U5 cells 12–13 (concentration of measure defined; N(0, I_d) bridged; `‖x‖ ≈ d` typo corrected to √d with tag; norm concentration; thin shell; explains U3); U6 cells 14–23 (uniformity summary cell 15; implications cell 17; fixes cells 19–21 incl. PCA cell 20 live variance-budget, regularization table, normalization with repaired LaTeX; advanced ML cell 23: embeddings, attention, latent spaces, RAG, vector DBs). No source cell is silently dropped; the full 23-cell dispositions ship in the evaluation coverage matrix.

## Learning sequence

U0 → U1 → U2 → U3 → U4 → U5 → U6 → Synthesis + mastery (M1–M8) → review list → glossary → colophon. Reveal arcs per LP depth-pass table; every forward reference is a promise with a named payoff unit.

## Interaction and feedback specification

**W1 `dim-calc` (U1, numeric widget, no canvas — reason: the skill is arithmetic on sensor counts, no spatial structure).** Manipulables: width w (slider 16–512, step 16, default 256), height h (slider 16–512, step 16, default 256), channels c (slider 1–4, step 1, default 3). Live readout: d = w·h·c, plus the source's 196,608 reference line and a "time to visit every point at 1 ns per point" line computed live. Degenerate guard: none needed (bounded positive integers). Goal strip: "Build a sensor and watch its dimensionality."

**W2 `volume-collapse` (U2, canvas).** Manipulables: ε (slider 0.05–0.50, step 0.01, default 0.10), d (slider 1–20, step 1, default 2). Canvas draws the unit square with the inner ε×ε box highlighted plus a horizontal log-scale bar for the covered fraction ε^d. Viewport: xMin=0, xMax=1.05, yMin=0, yMax=1.05. Legend: unit cube (side 1), covered box (side ε per axis). Readout: ε^d in scientific notation, number of ε-boxes to fill the cube (1/ε)^d, and the d = 100 extrapolation. Degenerate guard: ε bounded ≥ 0.05; d bounded ≤ 20; ε^d underflow displayed as "≈ 0" below 1e-300. Text equivalent: full numeric readout. Goal strip: "Find the dimension where covering 10% of every axis becomes hopeless."

**W3 `distance-lab` (U3, canvas).** Manipulables: dimension d (slider over the ordered set {1, 2, 3, 5, 10, 30, 100, 300, 1000}, mapped by index, default index 0), experiment reseed n (slider 1–20, step 1). Model: N = 500 points uniform in [0,1]^d (seeded mulberry32), query point = a fixed seeded point; histogram (20 bins) of Euclidean distances from query to all points; nearest and farthest marked. Viewport (autoscale declared): xMin = 0, xMax = √d (theoretical max distance, computed from the current slider value), yMin = 0, yMax = 1 (normalized bin density). Legend: distance histogram, nearest neighbor, farthest neighbor. Readout: d_min, d_max, contrast ratio (d_max − d_min)/d_min, live. Degenerate guard: d = 1 handled (histogram still valid); seeded PRNG makes every number reproducible. Text equivalent: full numeric readout. Goal strip: "Watch nearest and farthest merge as d grows."
**W4 `metric-lab` (U4, canvas).** Manipulables: angle θ of vector w (slider 0–360°, step 5°, default 60°), length L of w (slider 0.3–3, step 0.1, default 2), experiment reseed r (slider 1–10, step 1) for the built-in random-1000-dim replication of source cell 11 (two uniform [0,1]^1000 vectors; live Euclidean ≈ 12.9–13.1 and cosine ≈ 0.75 with the expected values d/6 → √(d/6) ≈ 12.91 and the positive-orthant explanation printed alongside). Vector v fixed at (2, 0). Canvas draws v and w as labeled arrows plus the angle arc (signed-difference method per ADR-0013 §5). Viewport: xMin=−3.2, xMax=3.2, yMin=−3.2, yMax=3.2. Legend: v (reference), w (yours). Readout: dot product, cos θ, Euclidean ‖v − w‖, the normalized identity check ‖v̂ − ŵ̂‖² vs 2 − 2cos θ computed live and shown equal, plus the seeded 1000-dim experiment readout. Degenerate guard: L bounded ≥ 0.3 so w never reaches the origin; θ bounded so the arc is always drawable; seeded PRNG reproducibility. Text equivalent: full numeric readout. Goal strip: "Change w's length and watch which numbers move — and which don't."

**W5 `shell-lab` (U5, canvas).** Manipulables: dimension d (slider index over {2, 4, 10, 30, 100, 300, 1000}, default index 1), reseed n (slider 1–10, step 1). Model: 400 Gaussian vectors (Box–Muller from seeded PRNG), histogram (24 bins) of ‖x‖; vertical marker at √d. Viewport (autoscale declared): xMin = 0, xMax = √(3d), yMin = 0, yMax = 1 (normalized density). Legend: sampled norms, √d marker. Readout: sample mean, sample std, relative spread std/mean, theoretical 1/√(2d), and the fraction of samples within mean ± 2·std. Degenerate guard: d bounded ≥ 2; seeded PRNG reproducibility. Text equivalent: full numeric readout. Goal strip: "Watch the spread of lengths collapse as d grows."

**W6 `variance-budget` (U6, numeric widget, no canvas — reason: the skill is a ratio of sums, no spatial structure).** Manipulables: λ₁–λ₄ (sliders 0.1–10, step 0.1, defaults 6.0/2.5/1.0/0.5), k (slider 1–4, step 1). Live readout: retained variance Σ_{i≤k}λᵢ/Σλᵢ as %, per-component contributions. Degenerate guard: all λ ≥ 0.1 so the denominator never vanishes. Goal strip: "Buy variance with components — how few do you need?"

Canvases: W2, W3, W4, W5 (4 canvases; resize listeners ≥ 4). All sliders follow `.ctrl-grid` + `.slider-control` + `.slider-track` + tabular `.slider-val` (§10.6). All option sets follow `.option-stack` + `.option-item` (§10.7). All goal strips use the `.goal` pattern. Callout density ≤ 1 per unit (§10.8).



## Formula manifest

| Formula ID | Name / Purpose | Equation (display) | Symbol Key Breakdown | Target Unit |
|---|---|---|---|---|
| `EQ-001` | Image dimensionality | `d = w · h · c` | `w`: width in pixels; `h`: height in pixels; `c`: channels per pixel | U1 |
| `EQ-002` | Covered volume fraction | `V(ε, d) = ε^d` | `ε`: per-axis covered fraction; `d`: dimension; `ε^d`: product of d copies | U2 |
| `EQ-003` | Covering-grid size | `N(ε, d) = (1/ε)^d` | `1/ε`: boxes per axis; `^d`: per-axis count raised to the dimension | U2 |
| `EQ-004` | Euclidean distance | `‖x − y‖ = √(Σᵢ (xᵢ − yᵢ)²)` | `xᵢ, yᵢ`: i-th coordinates; `Σᵢ`: sum over dimensions; `√`: square root | U3 |
| `EQ-005` | Expected squared distance (uniform [0,1]) | `E‖X − Y‖² = d/6` | `E`: expectation; each dim contributes `E[(X−Y)²] = 2·(1/12) = 1/6`; `d`: dimension | U3 |
| `EQ-006` | Distance contrast | `c(d) = (d_max − d_min)/d_min → 0` | `d_max, d_min`: farthest/nearest distances; `c(d)`: relative contrast | U3 |
| `EQ-007` | Cosine similarity | `cos θ = (x·y)/(‖x‖ ‖y‖)` | `x·y`: dot product; `‖x‖, ‖y‖`: vector lengths; `θ`: angle between | U4 |
| `EQ-008` | Embedding normalization | `x̂ = x/‖x‖` | `x`: any nonzero vector; `‖x‖`: its length; `x̂`: unit vector (length 1) | U4 |
| `EQ-009` | Normalized-distance identity | `‖x̂ − ŷ‖² = 2 − 2 cos θ` | `x̂, ŷ`: unit vectors; `θ`: angle between them; ties Euclidean to cosine | U4 |

## Term definition registry

| Term | First Appearance | Introductory Intuition / Definition | Glossary Status |
|---|---|---|---|
| dimension / feature | U1 | One measurable coordinate of a data point | Complete |
| embedding | U1 | A learned vector that represents an item's meaning | Complete |
| recommender system | U1 | Predicts preferences from user–item patterns | Complete |
| curse of dimensionality | U2 | The set of failure modes that appear as d grows | Complete |
| hypercube / unit cube | U2 | The d-dim box with all coordinates in [0,1] | Complete |
| coverage / covered fraction | U2 | The share of volume within ε of every axis slice | Complete |
| sparsity | U2 | Fixed data occupies a vanishing share of the space | Complete |
| sample complexity | U2 | How much data a task needs; grows exponentially here | Complete |
| Euclidean distance | U3 | Straight-line length between two points | Complete |
| Monte-Carlo simulation | U3 | Measure something by simulating it many times | Complete |
| distance concentration | U3 | Nearest ≈ farthest as d grows | Complete |
| contrast collapse | U3 | Relative distance spread shrinks toward 0 | Complete |
| KNN (k-nearest neighbors) | U3 | Classify by the labels of the closest points | Complete |
| Central Limit Theorem (CLT) | U3 (named) / U5 (defined) | Sums of many small random parts concentrate | Complete |
| Manhattan distance | U4 | Sum of per-axis absolute differences | Complete |
| dot product | U4 | Multiply pairs and add; measures alignment | Complete |
| cosine similarity | U4 | Dot product divided by lengths; angle only | Complete |
| positive orthant | U4 | The region where all coordinates are ≥ 0 | Complete |
| unit vector / normalization | U4 | Vector scaled to length 1 | Complete |
| scale invariance | U4 | Unchanged when a vector is stretched | Complete |
| concentration of measure | U5 | Random high-d quantities hug their mean | Complete |
| Gaussian distribution N(0, I_d) | U5 | The standard bell curve, one per coordinate | Complete |
| norm | U5 | A vector's length | Complete |
| thin shell | U5 | Most volume sits near the sphere's surface | Complete |
| overfitting | U6 | Memorizing training data instead of learning | Complete |
| feature selection | U6 | Keep only useful dimensions | Complete |
| PCA | U6 (link) | Project onto max-variance directions (Class 2) | Complete |
| t-SNE / UMAP | U6 | Visualization projections; local vs global trade-offs | Complete |
| regularization (L1/L2/dropout/early stopping) | U6 | Penalties and training tricks against overfitting | Complete |
| vector database | U6 | Stores embeddings; retrieves by similarity | Complete |
| attention | U6 (ML LINK) | Tokens compare each other with dot products | Complete |
| latent space | U6 (ML LINK) | The learned compressed coordinate system | Complete |
| RAG | U6 (ML LINK) | Retrieve context by similarity before generating | Complete |
| semantic similarity | U6 (ML LINK) | Closeness in meaning, measured as closeness in space | Complete |

| `EQ-010` | Norm concentration | `‖x‖ ≈ √d, x ~ N(0, I_d)` | `x`: Gaussian vector; `N(0, I_d)`: standard Gaussian in d dims; `√d`: root-mean length | U5 |
| `EQ-011` | Relative norm spread | `σ/μ ≈ 1/√(2d)` | `σ`: std of ‖x‖; `μ`: mean of ‖x‖ ≈ √d; shrinks as d grows | U5 |
| `EQ-012` | Retained variance | `R(k) = Σ_{i≤k} λᵢ / Σᵢ λᵢ` | `λᵢ`: i-th variance (eigenvalue); `k`: components kept; `R(k)`: retained fraction | U6 |

## Visual/representation rationale

Histograms for all Monte-Carlo evidence (distances U3, norms U5) with marked theoretical values; labeled arrows for vectors (taught convention) with a signed-difference angle arc; the unit square + inner ε-box for coverage; log-scale bars for exponential quantities with the number printed beside them so the visual never carries meaning alone; matrices/tables as bordered grids. One accent hue plus semantic good/bad/warn; pinned token set per standard §10.1.

## Assessment and misconception checks

Unit checks (each: 1 auto-graded numeric + 1 diagnostic MCQ with per-option misconception feedback; U3 and U5 add an explain-in-own-words item with model-answer reveal): U1 numeric d = w·h·c variant; U2 numeric ε^6; U3 numeric E‖X−Y‖ for d = 12 (√2 ≈ 1.414 tolerance 0.05) + contrast MCQ; U4 numeric cos between (1,0) and (1,1)/√2 (0.707, tol 0.02) + scale MCQ; U5 numeric √144 = 12 + shell MCQ + explain item; U6 numeric retained variance for λ = (4, 3, 2, 1) at k = 2 (7/10 = 70%, tol 1). Ladders L1–L6 × 3 rungs. Gates G1–G3 with commitment-gated unlock and differentiated feedback. Mastery M1–M8 with confidence routing (sure/think-so/guessing), reasoning + transfer + error-identification items, no reused worked numbers. Strict modality: MCQ / bounded auto-graded numeric only; zero `<textarea>`, zero unvalidated free text; options in `.option-stack`.

## Accessibility and inclusion plan

Semantic landmarks (header/nav/main/section/footer), logical heading order, `aria-live` readouts, keyboard-operable native controls, canvas text equivalents with identical numbers, legends plus labels (color never sole encoder), `prefers-reduced-motion` disables transitions, print stylesheet exposes content and hides controls, focus-visible rings, 16px floor at every breakpoint, no drag-only or hover-only interaction.

## Performance/responsiveness intent

Single file; zero external requests; all canvases responsive via `makeView` (clientWidth at draw time, DPR scaling, aspect-ratio height, resize listeners ≥ canvas count); Monte-Carlo workloads bounded (500×1000 max ≈ 0.5M multiply-adds per redraw, re-run only on slider change); nav single-line horizontal scroll; storage guarded with try/catch and reset.

## Acceptance criteria and evaluation dimensions

`verify-candidate.py` strict pass (0 failures); every Formula-Manifest equation present in a `.formula` block with `.symkey`; every Term-Registry term defined at first mention and linked to a 6-field glossary entry; every widget matches its declaration element-for-element; six audits + adversarial gate pass; rendered verification at 320/640/1024px with 0 console errors; repository checker exit 0; disposition private-pilot-complete, non-independent, release-ineligible.

## Concept map (dependency nodes and directed edges)

Nodes: DIM (dimensionality of data), VOL (ε^d collapse), SPARSE (sparsity), SAMPLE (sample complexity), DIST (distance concentration), MECH (sum-of-contributions mechanism), METRIC (metric choice: Euclidean vs cosine), NORM (normalization/unit vectors), SHELL (concentration of measure & thin shell), MLFAIL (KNN/clustering/overfitting), FIX (feature selection/PCA/regularization), SEARCH (embeddings/vector search/RAG).
Edges: DIM→VOL; VOL→SPARSE; SPARSE→SAMPLE; SPARSE→DIST; MECH→DIST; SHELL→MECH; SHELL→NORM; DIST→METRIC; NORM→METRIC; METRIC→SEARCH; DIST→MLFAIL; DIM→MLFAIL; MLFAIL→FIX; NORM→SEARCH; SHELL→FIX (variance budget).

## Conformance checklist (depth-calibration contract)

- [x] Every widget declares learner-manipulable variable(s) or explicit "static demo" justification (W1, W6 numeric by stated reason)
- [x] Every canvas widget declares input bounding (sliders, min/max) — ε, d, θ, L, reseed bounded; fixed models bounded by construction
- [x] Every canvas widget declares its mathematical viewport (W2 0–1.05/0–1.05; W3 0–√d / 0–1 autoscale; W4 ±3.2/±3.2; W5 0–√(3d) / 0–1 autoscale)
- [x] Controls declare atomic `.slider-control` encapsulation and `.option-stack` layout
- [x] Complete Formula manifest (EQ-001–EQ-012) mapped to unit `.formula` blocks
- [x] Complete Term definition registry (34 terms); zero deferred jargon
- [x] Assessment modality strictly MCQ / bounded auto-graded numeric; no `<textarea>`
- [x] Exhaustive glossary term set listed from the CM (every term used gets 6 fields)
- [x] Concept map declares explicit dependency nodes and directed edges (multi-branch)
- [x] Every LP-planned ladder (L1–L6), prediction gate (G1–G3), and reveal arc has a specified element
- [x] Canvas text equivalents specified for every visual component

