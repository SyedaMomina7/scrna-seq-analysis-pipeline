#  scRNA-seq Analysis Workflow

##  Overview
This document explains the step-by-step workflow used for analyzing single-cell RNA sequencing (scRNA-seq) data using Scanpy.

The pipeline transforms raw gene expression data into biologically meaningful insights such as cell clusters and cell-type identification.

---

## Pipeline Summary


Raw Data → QC → Filtering → Normalization → Feature Selection → PCA → UMAP → Clustering → Annotation → Differential Expression


---

##  Step-by-Step Workflow

### 1. Data Loading
- Input data is loaded in 10X Genomics format.
- Stored as an AnnData object for efficient processing.

---

### 2. Quality Control (QC)
We compute:
- Number of genes per cell
- Total counts per cell
- Percentage of mitochondrial genes

 Purpose:
- Identify low-quality or damaged cells

---

### 3. Filtering
- Remove cells with:
  - Very low gene counts
  - Very high mitochondrial percentage
- Remove genes expressed in very few cells

 Purpose:
- Clean dataset for reliable analysis

---

### 4. Doublet Detection
- Scrublet is used to detect doublets (two cells captured as one)

 Purpose:
- Prevent incorrect clustering

---

### 5. Normalization
- Normalize total counts per cell
- Apply log transformation

 Purpose:
- Make gene expression comparable across cells

---

### 6. Feature Selection (HVGs)
- Select Highly Variable Genes (HVGs)

 Purpose:
- Focus on informative genes
- Reduce noise

---

### 7. Dimensionality Reduction

#### PCA (Principal Component Analysis)
- Reduces high-dimensional data into fewer components

#### UMAP (Uniform Manifold Approximation and Projection)
- Visualizes cells in 2D space

 Purpose:
- Capture structure of data for clustering

---

### 8. Clustering
- Leiden algorithm applied at multiple resolutions:
  - Low resolution → fewer clusters
  - High resolution → more detailed clusters

 Purpose:
- Identify groups of similar cells

---

### 9. Cell Type Annotation
- Use known marker genes to assign biological identities

Examples:
- CD4 → Helper T cells
- MS4A1 → B cells

 Purpose:
- Give biological meaning to clusters

---

### 10. Differential Gene Expression
- Wilcoxon rank-sum test is used

 Purpose:
- Identify genes that distinguish clusters

---

##  Outputs

- UMAP plots
- QC visualizations
- Cluster labels
- Marker gene plots
- Differential expression tables

---

##  Conclusion
This workflow provides a complete pipeline for analyzing scRNA-seq data, from raw input to biological interpretation.

It ensures:
- Data quality
- Robust clustering
- Meaningful biological insights
