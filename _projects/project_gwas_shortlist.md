---
layout: page
title: "GWAS-based gene shortlist for NAFLD"
description: A cautious, transparent genetics evidence triage using the GWAS Catalog API
img: assets/img/projects/bioinfo/gwas_shortlist/gwasCard.jpg
importance: 3
category: Science
giscus_comments: true
toc:
  sidebar: left
---

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.html path="assets/img/projects/bioinfo/gwas_shortlist/gwas_hero.png" title="NAFLD | GWAS Catalog | Gene-level evidence triage" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
Public GWAS association evidence for non-alcoholic fatty liver disease aggregated to a gene-level shortlist using a transparent scoring heuristic.
</div>

This mini-project demonstrates a clean, end-to-end workflow for **genetics-driven target triage** using public GWAS data.  
The goal is to generate a **ranked shortlist of genes** supported by human genetic evidence for **non-alcoholic fatty liver disease (NAFLD)**, while keeping assumptions and limitations explicit.

### Why this project
In applied computational biology, genetics is often used as an early signal for target prioritization. This project focuses on:
- working with real-world public GWAS APIs and their constraints
- converting heterogeneous association records into a tidy, reviewable evidence table
- aggregating variant- and locus-level evidence to the gene level
- producing interpretable outputs rather than opaque scores

This is **evidence triage**, not causal inference.

---

## Data

**Trait:** non-alcoholic fatty liver disease  
**EFO ID:** `EFO_0003095`

**Source:** GWAS Catalog REST API (v2)

The GWAS Summary Statistics API does not currently expose full genome-wide summary statistics for NAFLD. Therefore, this project uses **curated association-level records** retrieved via the GWAS Catalog REST API.

Key fields used:
- association p-values
- study accession identifiers
- genomic locus coordinates
- GWAS Catalog–provided mapped genes
- publication identifiers (PubMed)

---

## Methods

### 1) Association retrieval
GWAS association records are queried by EFO identifier using the `/v2/associations` endpoint.  
Responses are paginated and retrieved iteratively by following server-provided `next` links.

This yields a list of association records corresponding to NAFLD and closely related liver phenotypes as defined by GWAS Catalog curation.

---

### 2) Normalization and cleaning
API responses contain nested structures and list-valued fields. These are normalized into a dataframe by:
- extracting a consistent subset of fields per association
- coercing p-values to numeric
- preserving provenance fields (study accession, publication)
- representing genomic locations as stable `chr:position` locus identifiers

A raw, normalized association table is retained for traceability.

---

### 3) Gene-level evidence table
Each GWAS association may map to one or more genes. To support gene-level aggregation:
- `mapped_genes` are parsed into individual gene symbols
- the table is converted to long format using `explode`, producing one row per (association × gene) link
- evidence is de-duplicated at the level of (study, locus, gene) to avoid inflating support counts

The result is a **gene-evidence table** suitable for aggregation.

---

### 4) Gene-level aggregation
For each gene, the following features are computed:
- **p_min**: strongest supporting p-value
- **n_loci**: number of distinct supporting loci
- **n_studies**: number of distinct supporting studies
- **n_pubs**: number of distinct supporting publications

These features capture both **strength** and **breadth** of genetic support.

---

### 5) Transparent evidence score
A simple, interpretable heuristic score is used to rank genes:

- `-log10(p_min)` is capped to prevent a single extreme association from dominating
- additional weight is given to replication across studies and loci

The score is intended for **prioritization and inspection**, not as a predictive model.

---

## Results (example run)

The top-ranked genes by evidence score include well-known NAFLD-associated loci, such as:
- **PNPLA3**
- **TM6SF2**
- **APOE**
- **GCKR**
- **GPAM**

The presence of established NAFLD genes provides a basic sanity check that the ingestion, normalization, and aggregation steps behave as expected.

<div class="row justify-content-center">
  <div class="col-md mt-3 mt-md-0 text-center">
    {% include figure.html path="assets/img/projects/bioinfo/gwas_shortlist/top_genes_score.png" title="Top genes ranked by GWAS evidence score." class="img-fluid rounded z-depth-1" zoomable=true %}
  </div>
</div>
<div class="caption">
Top 15 genes ranked by the transparent GWAS evidence score.
</div>

<div class="row justify-content-center">
  <div class="col-md mt-3 mt-md-0 text-center">
    {% include figure.html path="assets/img/projects/bioinfo/gwas_shortlist/loci_vs_studies.png" title="Distinct loci vs studies supporting each gene." class="img-fluid rounded z-depth-1" zoomable=true %}
  </div>
</div>
<div class="caption">
Diagnostic scatter plot showing breadth of genetic support per gene.
</div>

---

## Outputs and artifacts

Produced by the notebook:
- `outputs/top_genes.csv` – ranked gene shortlist with aggregation features
- `outputs/gene_evidence.csv` – long-format evidence table linking associations to genes
- `outputs/plots/top_genes_score.png`
- `outputs/plots/loci_vs_studies.png`

These outputs are designed to be reviewable and reusable.

---

## Discussion

### What this analysis suggests
- Public GWAS association data can be systematically aggregated into a compact gene shortlist.
- Combining association strength with replication across loci and studies provides a more informative ranking than p-values alone.
- Even with curated, non–fine-mapped data, transparent heuristics can support early-stage target triage.

### Important limitations
- GWAS associations do not establish causality.
- `mapped_genes` represent plausible mappings, not definitive gene assignments.
- Lead associations are not fine-mapped credible sets.
- The scoring scheme is heuristic and context-dependent.

### Reasonable next steps
- Replace mapped-gene expansion with locus-to-gene evidence (fine-mapping, eQTL colocalization, chromatin interactions).
- Integrate functional genomics layers and tissue specificity.
- Benchmark shortlisted genes against known disease biology and internal datasets.

---

## Reproducibility

The repository includes:
- a single notebook implementing the workflow
- exported CSV outputs for inspection
- minimal dependencies (pandas, numpy, requests, matplotlib)

The project is designed to be run end-to-end in a standard Python environment.
