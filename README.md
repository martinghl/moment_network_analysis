
# Expression Network Analysis

This project focuses on the comprehensive analysis of gene expression data from **Ulcerative Colitis (UC)** patients and **Healthy Controls (HC)**. Using advanced statistical and network-based methods, the analysis aims to uncover differences in gene expression patterns, network topology, and module assignments between the two groups.

---

## **Analysis Workflow**

### **1. Data Preprocessing**
- Source datasets:
  - [GSE117993: Transcription profiles of rectal biopsies in pediatric inflammatory bowel diseases](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE117993)
  - [GSE109142: Mucosal transcriptome of rectal biopsies in pediatric ulcerative colitis patients](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE109142)
- Key preprocessing steps:
  - Filtered genes based on variance and removed genes with near-zero variance.
  - Normalized gene expression values.
  - Split datasets into UC and HC groups for downstream analysis.

### **2. Differential Expression Analysis**
- Performed using `limma` to identify significant differences in expression levels between UC and HC groups.

### **3. Network Construction**
- Constructed **gene co-expression networks** for both UC and HC groups using:
  - Soft-thresholding power selection (`pickSoftThreshold`) to achieve scale-free topology.
  - Adjacency and Topological Overlap Matrices (TOM) for connectivity analysis.

### **4. Motif Analysis**
- Extracted key network motifs (e.g., triangles, V-shapes, 3-stars, and squares) using:
  - Subsampling of networks to calculate motif counts.
  - Computed normalized U-statistics for motifs across groups.

### **5. Module Detection**
- Identified gene modules using dynamic tree cutting based on TOM similarity.
- Compared module assignments between UC and HC groups and visualized overlaps.

### **6. Eigengene Analysis**
- Calculated module eigengenes and performed statistical tests to compare eigengene expression between UC and HC groups.

### **7. Statistical Testing**
- High-dimensional covariance tests (`PEtests`) to compare network structures.
- Bootstrap analysis of motif count distributions.

### **8. Visualization**
- Generated various plots, including:
  - Density and histogram plots for adjacency matrix values.
  - Scale-free topology plots.
  - Module dendrograms and heatmaps of module overlaps.
  - Motif distribution and eigengene comparisons.

---

## **Key Outputs**
- **Differential Expression Results:** List of significant genes (`significant_genes.csv`).
- **Networks:**
  - UC Network (`g_uc_pearson.csv`) - [View on GitHub](./g_uc_pearson.csv)
  - HC Network (`g_hc_pearson.csv`) - [View on GitHub](./g_hc_pearson.csv)
- **R Data Objects:**
  - Processed data and results saved as `pearson.RData`.
- **Visualizations:**
  - Density plots, heatmaps, and motif distribution comparisons.

---

## **How to Run the Analysis**

1. Clone the repository:
   ```bash
   git clone <repository-link>
   cd Expression_Network_Analysis
   ```

2. Set up your environment:
   - Install required R packages:
     ```R
     install.packages(c("WGCNA", "igraph", "ggplot2", "parallel", "caret", "reshape2", "progress", "ggpubr", "pheatmap"))
     ```

3. Execute the scripts in order:
   - `uchc_data_cleaning.ipynb`: Preprocess data.
   - `Differential_Expression.Rmd`: Perform differential expression analysis.
   - `Expression_Network_Analysis.Rmd`: Construct networks, analyze motifs, and detect modules.

4. Outputs will be saved in the `output/` directory.

---

## **Contact**
For questions or collaborations, contact **Martin Li** via [email@example.com](mailto:email@example.com).

---

**Happy Analyzing!**
