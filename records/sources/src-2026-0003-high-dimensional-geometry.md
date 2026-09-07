# SRC-2026-0003: High-dimensional geometry

**Status:** Recorded  
**Owner:** Repository maintainer  
**Content package:** [AIML-4 Module 2](../../content/aiml-4/module-02-math-statistics-for-ml/README.md)  
**Version:** 1.0

## Source identity

**Source file:** [High_Dimensional_Geometry.ipynb](../../content/aiml-4/module-02-math-statistics-for-ml/sources/High_Dimensional_Geometry.ipynb)  
**SHA-256:** `06dd3341d2d65699f172fffba11b271bfd47404cb716d388890cf7cdaa69d63d`  
**Language and scope:** English; AIML-4 Module 2 high-dimensional geometry — the curse of dimensionality, distance concentration, concentration of measure, metric choice (Euclidean vs cosine), and ML implications/fixes.  
**Sensitive-content flags:** None known.

## Citation anchors

The notebook contains 21 Markdown cells and 2 executed code cells (Python/numpy/sklearn, with recorded outputs). Claims are anchored by one-based cell ordinal and visible heading. Cells 1–2 are the title/agenda; cell 4 motivates with real system dimensionalities (256×256×3 images = 196,608 dims; BERT 768 / OpenAI 1536 / Sentence-Transformers 384–1024; recommender embeddings); cell 6 covers the curse (volume growth ε^d, sparsity, sample complexity); cell 8 covers distance concentration, contrast collapse, and KNN failure; cell 9 is one opaque inline base64 PNG figure (unlabeled axes); cell 10 contrasts Euclidean vs cosine with a malformed LaTeX cosine block and a metric comparison table; cell 11 is code computing Euclidean distance (≈13.0) and cosine (≈0.749) for two random 1000-dim uniform vectors; cell 13 covers concentration of measure, the norm claim `‖x‖ ≈ d` (a typo for √d), and the thin shell; cell 15 combines the effects into a uniformity summary; cell 17 covers ML implications (KNN, clustering, feature explosion, overfitting, embeddings/vector search, representation learning); cell 19 covers practical fixes (feature selection, PCA) with a PCA code cell following (cell 20: 100×1000 → 100×10); cell 21 covers t-SNE, UMAP, a regularization methods table, metric selection, and embedding normalization with a second malformed LaTeX block; cell 23 covers the advanced ML perspective (semantic embeddings, attention, latent spaces, RAG, vector databases). Three LaTeX blocks (cells 10, 21) are corrupted (`cos(theta)=fracxcdoty…`, `x norm = fracx∣∣x∣∣`) and are treated as transcription artifacts; the intended formulas are recoverable from context.
