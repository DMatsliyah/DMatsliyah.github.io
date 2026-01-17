---
layout: page
title: "RNA-seq NAFL vs NASH classifier"
description: A cautious, leakage-safe ML workflow on bulk liver RNA-seq
img: assets/img/projects/bioinfo/rnaseq_classifier/rnaseqCard.jpg
importance: 3
category: Science
giscus_comments: true
toc:
  sidebar: left
---

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/projects/bioinfo/rnaseq_classifier/rna_hero.jpg" title="NAFL vs NASH | Bulk liver RNA-seq | L1 Logistic Regression" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
A simple baseline classifier built on bulk liver RNA-seq to separate NAFL from NASH, shown with holdout evaluation outputs.
</div>

This mini-project demonstrates a clean, end to end machine learning workflow for transcriptomics, focusing on validation hygiene and interpretability. The goal is to build a baseline classifier that distinguishes **NAFL** from **NASH** using bulk liver RNA-seq counts.

### Why this project
In applied computational biology, even a simple model can be informative if the evaluation is handled responsibly. This project focuses on:
- correct sample alignment (expression matrix ↔ phenotype table)
- leakage-safe preprocessing using scikit-learn `Pipeline`
- cross-validation for hyperparameter selection on training only
- producing reviewable artifacts (metrics, plots, coefficient-ranked genes)
---

## Data

**Public source:** GEO Series **GSE167523**  available on [NCBI GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE167523)

Files used:
- `GSE167523_Raw_gene_counts_matrix.txt.gz` (raw counts)
- `GSE167523_Sample_phenotype_correspondence.xlsx` (labels and metadata)

**Label used:** `NAFL/NASH` mapped to:
- NAFL → 0
- NASH → 1

---

## Methods

### 1) Input handling and alignment
Bulk RNA-seq data often arrives as a matrix with genes and samples, plus a separate phenotype table. Before any modeling:
- transpose counts if needed so the matrix is **samples x genes**
- create or select a sample key that matches the sample naming in the counts matrix
- filter and reorder phenotype rows to match expression rows exactly

Sanity checks:
- confirm `expr_aligned.index` equals `pheno_aligned.index`
- confirm `X.shape` is (n_samples, n_genes)
- confirm `y` has only {0, 1}

### 2) Preprocessing in a leakage-safe Pipeline
Raw RNA-seq counts reflect sequencing depth and have heavy-tailed distributions. The pipeline uses:

1. **CPM normalization + log1p transform**
   - CPM (counts per million) normalizes each sample by its library size
   - log1p stabilizes variance and makes values more ML-friendly

2. **Variance filtering**
   - removes constant genes with zero variance

3. **Standard scaling**
   - important for L1-regularized models because regularization is scale-sensitive

### 3) Model choice
**Sparse logistic regression (L1 penalty, saga solver)** was chosen because:
- it works well in high-dimensional settings (many genes, fewer samples)
- it yields interpretable coefficients
- L1 drives sparsity, producing a short gene list rather than thousands of weak features

### 4) Validation design
- single **holdout test split** (stratified 80/20)
- hyperparameter selection (C) via **5-fold stratified CV on training only**
- report metrics on the held-out test set exactly once
---

## Results (example run)
On one 80/20 stratified split (20 samples in the test set), the baseline produced:
- Best hyperparameter: `C = 2`
- Test ROC AUC: **0.96**
- Test PR AUC: **~0.96**
- Confusion matrix (0=NAFL, 1=NASH): `[[8, 2], [1, 9]]`
  - 8 NAFL correctly predicted as NAFL
  - 2 NAFL predicted as NASH
  - 9 NASH correctly predicted as NASH
  - 1 NASH predicted as NAFL

Interpretation notes:
- These numbers reflect one specific split with a small test set `(n=20)`.
- With this sample size, results can vary noticeably across different splits.
- The main takeaway is that a nontrivial signal appears to be present in this dataset under this preprocessing and model, but it should be treated as a preliminary baseline.

<div class="row justify-content-center">
  <div class="col-md mt-3 mt-md-0 text-center">
    {% include figure.html path="assets/img/projects/rnaseq_nafld/roc_curve.png" title="ROC curve on one held-out test split." class="img-fluid rounded z-depth-1" zoomable=true %}
  </div>
</div>
<div class="caption">
ROC curve on one held-out test split (ROC AUC 0.96 for this run).
</div>

<div class="row justify-content-center">
  <div class="col-md mt-3 mt-md-0 text-center">
    {% include figure.html path="assets/img/projects/bioinfo/rnaseq_classifier/confusion_matrix.png" title="Confusion matrix on one held-out test split." class="img-fluid rounded z-depth-1" zoomable=true %}
  </div>
</div>
<div class="caption">
Confusion matrix on one held-out test split: [[8, 2], [1, 9]].
</div>

---

## Interpretable gene shortlist

The fitted model provides a ranked list of genes by absolute coefficient magnitude. Practical interpretation:
- positive coefficients push predictions toward class 1 (NASH)
- negative coefficients push predictions toward class 0 (NAFL)
- coefficient magnitude reflects model-weighted association under this setup, not biological causality

The top-ranked genes for the run are exported to:
- [outputs/top_genes_by_abs_coef.csv](/assets/files/projects/rna_seq/top_genes_by_abs_coef.csv)

---

## Outputs and artifacts

Produced by the notebook:
- outputs/metrics.json (best params, ROC AUC, PR AUC, confusion matrix)
- outputs/top_genes_by_abs_coef.csv (coefficient-ranked genes)
- outputs/roc_curve.png
- outputs/confusion_matrix.png

---

## Discussion

### What this baseline suggests
- In this dataset and for one split, the model produced a high ROC AUC and a relatively small number of errors on the holdout test set.
- The sparse linear model yields an inspectable gene list, which can be a useful starting point for follow-up checks.

### Important limitations
- Small test set: with n=20 test samples, estimates are noisy.
- Bulk tissue: liver RNA-seq reflects cell mixture and heterogeneity.
- Model outputs are not mechanistic claims and should not be interpreted as proof of disease drivers.

### Reasonable next steps
- Repeat the outer split multiple times and report mean ± std for ROC AUC and PR AUC.
- Track how stable the top genes are across repeated splits.
- Add a small set of sanity-check plots showing expression distributions for a few recurrent genes.

---

## Reproducibility

A compressed archive containing the files needed to run this pipeline can be [downloaded here](/assets/files/projects/rna_seq/RNAseq_classifier.zip)

---
