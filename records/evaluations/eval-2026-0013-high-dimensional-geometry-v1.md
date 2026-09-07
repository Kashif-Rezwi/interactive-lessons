# EVAL-2026-0013: High-dimensional geometry v1 (first governed generation)

**Candidate ID/version:** CAN-2026-0012, [high-dimensional-geometry-v1.html](../../content/aiml-4/module-02-math-statistics-for-ml/generated/high-dimensional-geometry-v1.html), SHA-256 `534b370053453bc909bb4ce4296c6672389ec51ae55ed6c8e514576b2021e469`, 146,124 bytes  
**Rubric version:** Stage 1 evaluation framework (operational anchors, WF-007) + lesson standard §10.6–10.8  
**Evaluator role/identity:** Repository maintainer, Reviewer profile  
**Evaluation mode:** script-assisted, browser-assisted, non-independent  
**Operating scope:** Stage 1 private pilot  
**Review independence:** non-independent  
**Reviewer relationship or limitation:** same operator generated and evaluated; no screen-reader specialist pass; no second evaluator; screenshots captured but evaluated via programmatic geometry (evaluator model cannot inspect images)  
**Public-release eligibility:** ineligible  
**Confidence:** medium  
**Recommendation:** private-pilot-complete  
**Iterations reviewed:** builds = 1 (final hash above); revision cycles = 0; in-generation corrections = 2 (both re-verified, see RUN-20260907-0001)

## Scope and evidence inspected

Source notebook (21 Markdown cells + 2 executed code cells, SHA re-verified), CM-2026-0010 / LP-2026-0011 / XS-2026-0011, the candidate HTML, `verify-candidate.py` strict output (0 failures, 9 notes), Python closed-form recomputation (10/10), answer-key cross-check (20/20 within tolerance), PRNG canonical-form cross-check (2 keys × 8 samples, Node vs Python identical), Node math-core harness replicating page draw code (W3/W4/W5 live values), live browser session evidence (agent-browser 0.27.0 via CDP: zero console errors, 320/640/1024px overflow measurements and screenshots, gate/ladder/mastery/persistence/reduced-motion traces), and the run ledger.

### Coverage matrix (all 23 source cells)

| Cells | Source content | Disposition | Lesson location |
|---|---|---|---|

## Dimension scorecard

| Dimension | Score (0–4) | Evidence | Defects/severity | Recommended remedy | Confidence |
|---|---:|---|---|---|---|
| Educational quality | 3.5 | Orientation unit; 6-unit anatomy; 3 commitment gates; 6 full ladders (12 rungs); 2 explain items; 8-item confidence-calibrated mastery with routing; U3→U5 reveal arc paid off | None material | — | medium |
| Factual/mathematical accuracy | 3.5 | Closed-form 10/10; answer keys 20/20 in tolerance; PRNG canonical-form match; browser readouts match fixed Node core bit-for-bit; three source artifacts corrected with tags | None observed | — | medium-high |
| Source grounding | 3.5 | 23/23 cells dispositioned (matrix above); opaque figure replaced with live experiment; constructed additions tagged | None | — | medium |
| Interactivity and agency | 3.5 | 17 sliders across 6 widgets (4 canvas), goal strips, live readouts, commitment-gated unlock, seeded reproducibility | None material | — | medium-high |
| Accessibility and inclusion | 3.5 | Native controls, aria-live, canvas text equivalents + legends on all 4 canvases, 16.5px at all widths, reduced-motion honored, print CSS, focus-visible | No screen-reader specialist pass | Specialist review before any public release | medium |
| Visual clarity | 3.5 | Pinned tokens, frosted nav + dots, labeled canvases, distance histogram, norm distribution, variance bars; zero overflow at 320/640/1024 | None | — | medium |
| User experience | 3.5 | Orientation, map + revisit, persistent dots/review list with spacing invitation and reset, storage fallback note | None material | — | medium |
| Completeness | 3.5 | All LP outcomes shipped; glossary 32×6 fields with verifier-enforced target resolution; formula manifest 11/11 | None | — | medium |
| Readability | 3.5 | Short blocks; per-symbol keys; direct definitions; zero-jargon first mentions (softmax repaired); mechanism-before-application | None material | — | medium-high |
| Technical feasibility/performance intent | 3.5 | 146KB single file; 0 external requests; 4/4 resize listeners; strict verifier clean; zero console errors; JS syntax validated | None | — | medium |

## Weighted result and gate check

Weighted score: **3.50 / 4.00** (all dimensions 3.5 under the Stage 1 default weights summing to 100). All hard-gate dimensions ≥ 3.5; no score 0–1; no unresolved critical defect; complete lineage. Gate satisfied for **private-pilot-complete**. Public release is ineligible: review is non-independent, no specialist accessibility pass, and Stage 1 policy conditions (calibration review, Human Accountable Owner approval) are not met.

## Disagreement or uncertainty

Judgment-based qualities (lede aptness, signature-visual aesthetics, density balance) were assessed by a single non-independent evaluator; those axes are provisional. The evaluator cannot inspect images; all rendered claims rest on measured geometry (font sizes, scroll widths, element bounding boxes, backing-store extents, live readouts), which is stronger evidence than unaided visual inspection but is not a visual-design review. The abstract source required the largest share of constructed numbers so far; each is closed-form verified and live-computed, but the depth-band judgment (matching the benchmark's feel) remains a single-reviewer call.

## Non-negotiable blockers

None for private-pilot scope. The candidate must not be described as a public release, benchmark result, or efficacy claim.

## Reviewer sign-off

Disposition: **private-pilot-complete** — first governed artifact for the Class 3 source (SRC-2026-0003); no superseded version. Future work: independent review and a screen-reader specialist pass before any public release; a second Monte-Carlo-based lesson would confirm the seeded-PRNG pattern (P-16 candidate) for promotion.
| 1–2 | Title, agenda | transcribed → orientation | U0 (loop, labels, concept map) |
| 4 | Real system dimensionalities (196,608; BERT 768; embeddings) | included-expanded + FOUNDATION bridges | U1 + W1 |
| 5–6 | Curse of dimensionality; ε^d volume; sample complexity | included-expanded + constructed numbers | U2 + W2 + L1/L2 |
| 7 | Sparsity; covering-grid intuition | included-expanded | U2 |
| 8 | Distance concentration; contrast collapse; KNN failure (defines concentration before mechanism — source ordering defect) | included-expanded; ordering repaired with forward promise | U3 + promise → U5 |
| 9 | Opaque inline base64 PNG figure (unlabeled axes) | replaced by live seeded canvas; dispositioned non-reconstructable | U3 + W3 (distance-lab) |
| 10 | Euclidean vs cosine; malformed LaTeX cosine block; metric table | included-expanded; LaTeX repaired with tag | U4 + metric table + EQ-005 |
| 11 (code) | Random 1000-dim vectors: Euclidean ≈ 13.0, cosine ≈ 0.749 | replicated as live seeded experiment with expected values; "≈ 0.75" scoped distributionally | U4 + W4 + L4 |
| 12 | Concentration of measure named | included-expanded | U5 + W5 |
| 13 | Norm claim `‖x‖ ≈ d` (typo for √d); thin shell | included-expanded; typo corrected with tag | U5 + EQ-007 |
| 15 | Uniformity summary (all effects combined) | included | U6 |
| 17 | ML implications (KNN, clustering, overfitting, embeddings, representation learning) | included (mechanism-anchored, bridged) | U6 Connect |
| 19 | Practical fixes: feature selection, PCA | included-expanded; PCA re-referenced as Class 2 concept with link | U6 + W6 |
| 20 (code) | PCA code (100×1000 → 100×10) | included-expanded (variance-budget widget) | U6 + W6 + L6 |
| 21 | t-SNE, UMAP, regularization table, metric selection, normalization; malformed LaTeX block | included-expanded; LaTeX repaired with tag | U6 + table + EQ-010 |
| 23 | Advanced ML perspective (semantic embeddings, attention, latent spaces, RAG, vector databases) | included (bridged; softmax first-mention repaired in-generation) | U6 DEEP DIVE |