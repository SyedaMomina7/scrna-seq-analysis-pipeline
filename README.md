# 🧬 Single-Cell RNA-seq Analysis using Scanpy

##  Overview

This repository contains a complete pipeline for analyzing single-cell RNA sequencing
(scRNA-seq) data using the **Scanpy** framework. The workflow includes preprocessing,
quality control, clustering, visualization, and cell-type annotation.

The dataset used consists of **human bone marrow mononuclear cells** from the
NeurIPS 2021 benchmarking dataset.

---

##  Features

- Data loading from 10X Genomics format
- Quality control (QC metrics & filtering)
- Doublet detection using Scrublet
- Normalization and log transformation
- Highly variable gene selection
- Dimensionality reduction (PCA, UMAP)
- Clustering using Leiden algorithm
- Marker gene-based annotation
- Differential gene expression analysis

---

##  Project Structure
scRNA-seq-analysis/
├── notebook/           #notebooks for analysis
├── results/            # Output figures and tables
├── docs/               # Documentation
├── README.md
└── requirements.txt

---
##  Installation

### Option 1: pip

```bash
pip install -r requirements.txt
```

### Option 2: conda

```bash
conda env create -f environment.yml
conda activate scrna-env
```

---

##  Workflow

### 1. Data Preprocessing
- Load 10X data
- Calculate QC metrics:
  - Number of genes
  - Total counts
  - Mitochondrial percentage

### 2. Filtering
- Remove low-quality cells
- Remove genes expressed in few cells

### 3. Doublet Detection
- Scrublet used to identify artificial cell multiplets

### 4. Normalization
- Total count normalization
- Log transformation

### 5. Feature Selection
- Identify Highly Variable Genes (HVGs)

### 6. Dimensionality Reduction
- PCA for variance compression
- UMAP for visualization

### 7. Clustering
- Leiden clustering at multiple resolutions:
  - `0.02` — coarse
  - `0.5` — moderate
  - `2.0` — fine

### 8. Cell Type Annotation
- Marker gene-based identification
- Dotplots for validation

### 9. Differential Expression
- Wilcoxon rank-sum test
- Cluster-specific marker genes

---

##  Key Outputs

- UMAP visualizations
- QC plots (violin, scatter)
- Marker gene dotplots
- Cluster annotations
- Differential gene expression tables

---

##  Example Marker Genes

| Cell Type     | Marker Genes   |
|---------------|----------------|
| CD4+ T Cells  | CD4, IL7R      |
| CD8+ T Cells  | CD8A, CD8B     |
| B Cells       | MS4A1          |
| NK Cells      | GNLY, NKG7     |
| Monocytes     | CD14, FCN1     |

---

##  Tools & Libraries

- [Scanpy](https://scanpy.readthedocs.io)
- [AnnData](https://anndata.readthedocs.io)
- [NumPy](https://numpy.org)
- [Matplotlib](https://matplotlib.org)
- [Scrublet](https://github.com/swolock/scrublet)

---

##  References

- [Scanpy Documentation](https://scanpy.readthedocs.io)
- [NeurIPS 2021 Dataset Benchmark](https://openproblems.bio/neurips_2021)
- [scRNA-seq Best Practices](https://www.sc-best-practices.org)

---

##  Author

Syeda Momina Assad

---

## ⭐ Future Improvements

- [ ] Batch correction (Scanorama / scVI)
- [ ] Automated cell-type annotation
- [ ] Integration with multi-omics dataSonnet 4.6Cl
