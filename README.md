# Proteomic Analysis using the DEP Package

This repository contains R scripts for proteomic data analysis, primarily using the `DEP` package. The data focuses on understanding the proteomic changes in different experimental conditions, specifically related to Tauopathy models (e.g., S305N and P301S). This README will walk you through the functionality of the provided scripts, dependencies, and the steps involved in the analysis.

---

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Data Description](#data-description)
- [Usage](#usage)
  - [Dataset 1: S305N 6 Months vs 15 Months](#dataset-1-analysis)
  - [Dataset 2: S305N vs P301S in Hippocampus](#dataset-2-analysis)
  - [Dataset 3: S305N vs P301S in Cortex](#dataset-3-analysis)
- [Key Functions](#key-functions)
- [Output](#output)
- [Contributors](#contributors)

---

## Overview

This project implements a proteomic data analysis pipeline using the `DEP` package in R, a powerful tool for differential protein expression analysis from mass spectrometry (MS) data. The analysis includes normalization, imputation of missing values, statistical testing for differential expression, and visualization of results such as volcano plots, heatmaps, PCA, and correlation matrices.

---

## Installation

Before running the analysis, ensure you have R installed on your system. You will also need the following packages:

```r
install.packages(c("DEP", "dplyr", "readr", "ggplot2", "ggrepel"))
```
To install `DEP`, you might need to install it from Bioconductor: https://bioconductor.org/packages/devel/bioc/vignettes/DEP/inst/doc/DEP.html

## Data Description

### Dataset 1: S305N 6 Months vs 15 Months
- **Source**: `/data/Set1-Total_abundance_protein_None.tsv`
- This dataset compares proteomic profiles between S305N (a Tauopathy mutant) at 6 months and 15 months.

### Dataset 2: S305N vs P301S in Hippocampus
- **Source**: `/data/Set2-Total_abundance_protein_None.tsv`
- This dataset compares the proteomic changes in the hippocampus of S305N and P301S models.

### Dataset 3: S305N vs P301S in Cortex
- **Source**: `/data/Cortex_Total_abundance_protein_None.tsv`
- This dataset compares the proteomic profiles of S305N and P301S in the cortex region.

---

## Usage

Each dataset is analyzed separately, following these steps:

1. **Data Loading**: The data is loaded using the `read_tsv()` function from the `readr` package.
2. **Preprocessing**: 
   - Unwanted proteins (e.g., "tau") are filtered using the `grepl()` function.
   - Proteins with low peptide counts (PSMs) are removed.
   - Duplicated gene names are checked and resolved using the `make_unique()` function.
3. **Experimental Design**: The conditions (e.g., control vs. mutant) and replicates are defined.
4. **Filtering**: Proteins identified in replicates are filtered to reduce noise.
5. **Normalization**: Variance Stabilizing Normalization (VSN) is applied to the data.
6. **Imputation**: Missing data is imputed using a Gaussian distribution (MNAR).
7. **Statistical Testing**: Manual pairwise comparisons are performed to identify significant differentially expressed proteins.
8. **Visualization**: Various visualizations like PCA, heatmaps, and volcano plots are generated to illustrate the findings.

## Key Functions

### Data Preprocessing and Wrangling
- **`grepl()`**: Used to filter proteins of interest (e.g., tau).
- The rest of the function used are from the DEP package, a beautiful tutorial is here: https://bioconductor.org/packages/devel/bioc/vignettes/DEP/inst/doc/DEP.html

---

## Output

The pipeline generates various outputs in both visual and tabular formats:
- **Barplots**: Frequency of identified proteins across conditions.
- **PCA plots**: Visualizing the principal components of the data.
- **Heatmaps**: Showing significant protein clusters.
- **Volcano Plots**: For identifying significantly upregulated or downregulated proteins.


---

## Contributors

- **Xheni Prebibaj**.

