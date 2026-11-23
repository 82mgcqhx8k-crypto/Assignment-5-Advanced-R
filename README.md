# Assignment-5-Advanced-R

# Differential Gene Expression Analysis

## Overview
This R script performs a comparative gene expression analysis between **Tumor** and **Normal** tissue samples. It integrates raw probe-level expression measurements, sample phenotype metadata, and genomic probe annotations to identify significantly differentially expressed genes (DEGs) with an absolute relative fold change greater than 5 (`|Fold Change| > 5`), summarizes their regulation direction, and generates five publication-ready visualizations.

---

## Input Files
The script expects the following three input files to be located in your `~/Downloads/` directory (or your active R working directory):

1. **`Gene_Expression_Data.xlsx`**  
   * **Format:** Excel workbook (`.xlsx`)
   * **Description:** Contains raw gene expression intensity values with probe identifiers in the first column and sample IDs across the remaining columns.
2. **`Gene_Information.csv`**  
   * **Format:** Comma-separated values (`.csv`)
   * **Description:** Annotation table mapping each `Probe_ID` to its corresponding gene metadata, including `Chromosome` location.
3. **`Sample_Information.tsv`**  
   * **Format:** Tab-separated values (`.tsv`)
   * **Description:** Sample metadata mapping each sample identifier to its experimental phenotype (`group`, e.g., `Tumor` or `Normal`).

---

## Needed R Packages 

  * `readxl` — Reading `.xlsx` expression 
  * `dplyr` — Data filtering, transformation
  * `ggplot2` — Generating bar charts and genomic distribution plots
  * `pheatmap` — Rendering standardized expression heatmaps and hierarchical clustermaps
  * `RColorBrewer` — Generating diverging and sequential color palettes


## How to Run the Script
1. Place `Gene_Expression_Data.xlsx`, `Gene_Information.csv`, and `Sample_Information.tsv` inside your `~/Downloads/` folder.
2. Open the R script in **RStudio**.
3. Review the statistical summary printed in the R Console and inspect the generated plots in Downloads section
---

## Code Structure & Methodology
The R script is organized into six documented stages:

1. **Installation of Packages:** Installs/loads required libraries
2. **Sample grouping:** Maps sample IDs to their phenotype labels and divides the dataset into Tumor and Normal subsets.
3. **Statistical Summary:** Filters for probes with fold change > 5, classifies each probe as higher expressed (upregulated) or (downregulated), and prints summary statistics.

---

## Outputs
* **Console Summary:** Descriptive statistics of filtered DEGs and counts of upregulated vs. downregulated probes.
* **Data Visualizations:**
  1. `Plot1_DEG_Chromosome` — Total count of filtered DEGs across sorted chromosomes.
  2. `Plot2_DEG_Chromosome_Split` — Side by side comparison of Tumor upregulated vs. Normal upregulated DEGs per chromosome.
  3. `Plot3_DEG_Percentage` — Percentage breakdown of upregulated vs. downregulated DEGs.
  4. `Plot4_Heatmap` — Unclustered Z score normalized expression heatmap across samples and filtered probes.
  5. `Plot5_Clustermap` — Hierarchically clustered heatmap grouping samples and probes by expression similarity, annotated by phenotype.
