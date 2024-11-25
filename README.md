
# Expression Network Analysis Pipeline

This repository provides a comprehensive pipeline for analyzing differential gene expression and constructing gene co-expression networks for Ulcerative Colitis (UC) and Healthy Control (HC) groups. The analysis includes data cleaning, filtering, differential expression analysis, network construction, covariance testing, motif analysis, and exploratory network comparisons.

## Data Sources

The source data used for this analysis includes transcription profiles obtained from two studies:
1. [Transcription profiles of rectal biopsies obtained during diagnostic colonoscopy for pediatric inflammatory bowel diseases (GSE117993)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE117993)
2. [Mucosal transcriptome of rectal biopsies in treatment-naïve, pediatric ulcerative colitis patients (GSE109142)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE109142)

## Analysis Workflow

### 1. Data Cleaning and Preprocessing
- The `uchc_data_cleaning.ipynb` notebook processes UC and HC datasets to ensure consistency and quality.
- Key steps include:
  - Removal of genes with near-zero variance.
  - Scaling TPM data to simulate count data for differential expression analysis.
  - Filtering genes with missing or infinite values.

### 2. Differential Expression Analysis
- Conducted using `edgeR` to identify significantly differentially expressed genes between UC and HC groups.
- Outputs include:
  - Significant genes (`significant_genes_edgeR.csv`) filtered by FDR < 0.05 and |logFC| > 1.5.
  - Volcano plots to visualize gene expression patterns.

### 3. Gene Co-expression Network Construction
- Networks constructed using:
  - Pearson correlation for UC and HC datasets.
  - Fisher transformation and p-value thresholding for adjacency matrix generation.
- Network metrics:
  - Node count, edge count, density, average degree, and clustering coefficient.

### 4. Covariance Matrix Comparison
- High-dimensional covariance tests performed using the `PEtests` package to assess differences between UC and HC covariance structures.
- Methods include:
  - Ledoit-Wolf shrinkage (`lc` method).
  - Cai-Liu-Xia test (`clx` method).
  - Cauchy combination test (`pe.cauchy`).
  - Fisher combination test (`pe.fisher`).

### 5. Motif Analysis
- Motif types analyzed:
  - Triangles, V-shapes, three-stars, and squares.
- Subsampling and normalization applied for motif counting.
- Violin plots illustrate motif distribution differences between UC and HC groups.

### 6. Random Projection Covariance Testing
- Random projections applied to reduce dimensionality for covariance comparisons.
- Permutation tests conducted to compute statistical significance of observed covariance differences.

### 7. Exploratory Network Comparisons
- Network community structures analyzed using clustering and modularity.
- Enrichment analysis planned for identified communities.

## Files in this Repository

- `uchc_data_cleaning.ipynb`: Notebook for cleaning and preprocessing UC and HC datasets.
- `Differential_Expression.Rmd`: R Markdown file for performing differential expression analysis using `edgeR`.
- `Expression_Network_Analysis.rmd`: R Markdown file for constructing and analyzing co-expression networks, covariance testing, and motif analysis.
- `significant_genes_edgeR.csv`: CSV file with significant differentially expressed genes identified by `edgeR`.

## Requirements

### R Packages
- edgeR
- ggplot2
- ggrepel
- ggalign
- WGCNA
- caret
- foreach
- doParallel
- huge
- PEtests

### Python Packages (Optional)
- numpy
- scipy
- pandas
- matplotlib

## Usage Instructions

1. **Data Preparation**: Download the source datasets from the provided GEO links and save them as `uc_data.csv` and `hc_data.csv`.
2. **Preprocessing**: Run the `uchc_data_cleaning.ipynb` notebook to clean and preprocess the data.
3. **Differential Expression Analysis**: Use the `Differential_Expression.Rmd` file to perform DE analysis.
4. **Network Analysis**: Execute `Expression_Network_Analysis.rmd` for network construction, motif analysis, and statistical tests.

## Contributors

- **Martin Li**: Project leader and developer of analysis pipeline.
- **Dr. Wen Zhou**: Project advisor.

## Acknowledgements

- Data provided by studies GSE117993 and GSE109142.
- Support and feedback from NYU Biostatistics and Computational Biology departments.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
