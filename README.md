# Epigenomics-Chromatin-Analysis-Pipeline-Visualization-GM12878-ATAC-seq-Data-GSE47753
Epigenomics Chromatin Analysis Pipeline Visualization GM12878 ATAC seq Data GSE47753
# Gold-Standard Chromatin Accessibility Analysis Pipeline: GM12878 ATAC-seq (GSE47753)

This repository contains a complete Python analysis pipeline for characterizing chromatin accessibility using the "Gold Standard" ATAC-seq dataset from the seminal Buenrostro et al. (2013) study.

The pipeline retrieves, processes, and visualizes ATAC-seq peak data for the **GM12878 lymphoblastoid cell line**, generating both publication-quality static plots and modern interactive visualizations.

## 🔬 Technical Title

**Gold-Standard Chromatin Accessibility Analysis Pipeline: Static and Interactive Visualization of GM12878 ATAC-seq Data (GSE47753)**

## 🚀 Key Features

* **Automated Data Retrieval:** Fetches metadata using `GEOparse` and downloads the high-confidence merged peak file directly from the NCBI GEO database via `wget`.
* **Data Processing:** Loads raw BED files, calculates peak lengths, filters for standard human chromosomes, and cleans the data for analysis.
* **Static Visualization:** Uses Matplotlib and Seaborn to generate:
    * Peak Length Distribution Histograms.
    * Bar Charts of Peak Counts per Chromosome.
    * Box Plots of Peak Length Variability by Chromosome.
* **Interactive Visualization:** Uses Plotly to create an interactive, zoomable histogram for detailed exploration of peak length distributions.
* **Quantitative Summary:** Exports detailed descriptive statistics (mean, median, quartiles, etc.) for each chromosome to a CSV file.

## 💾 Dataset Information

* **Source:** NCBI Gene Expression Omnibus (GEO)
* **Series Accession:** [GSE47753](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE47753)
* **Sample Metadata:** [GSM1155957](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM1155957) (GM12878 50k Rep 1)
* **Data File:** `GSE47753_GM12878_ATACseq_50k_AllReps_ZINBA_pp08.bed.gz` (Merged high-confidence peaks from all replicates)
* **Organism:** *Homo sapiens*
* **Cell Line:** GM12878 (B-lymphoblastoid cells)

## 🛠️ Setup and Installation

### Prerequisites

* Python 3.x
* Jupyter Notebook or a Python IDE (VS Code, PyCharm) that supports running code cells (`# %%` blocks).

### 1. Install Required Libraries

Run the following command (or execute the first cell in the notebook) to install the necessary packages:

```bash
pip install GEOparse pandas matplotlib seaborn plotly
2. System Tools (Optional)

The pipeline uses standard command-line tools for downloading and unzipping files. Ensure you have wget and gunzip installed (standard on Linux/macOS).
📋 Analysis Workflow

The analysis is structured into seven sequential steps:
Step,Action,Description
1,Setup,Imports libraries and configures the plotting style.
2,Metadata,Fetches and displays metadata for the representative sample GSM1155957.
3,Download,Downloads the merged peak file (.bed.gz) from GEO.
4,Processing,"Loads the BED file into a Pandas DataFrame, computes peak lengths (end - start), and filters for valid chromosomes (chr1-22, X, Y)."
5,Static Plots,"Generates histograms, bar charts, and box plots to visualize peak distributions."
6,Interactive Plots,Creates a Plotly histogram for interactive exploration of peak lengths.
7,Export,Saves summary statistics to GM12878_ATAC_summary.csv.
📊 Key Findings

The analysis of 99,885 ATAC-seq peaks revealed the following insights:
1. Peak Length Distribution

    Finding: The distribution is heavily right-skewed with a median peak length of ~599 bp.

    Insight: There is a strong enrichment of shorter fragments (< 200 bp), which typically correspond to nucleosome-free regions (NFRs) indicative of active regulatory elements like promoters and enhancers.

2. Chromosomal Distribution

    Finding: Peak counts correlate strongly with chromosome size. Larger chromosomes (e.g., chr1, chr2) contain the most peaks.

    Insight: Sex chromosomes (chrX, chrY) show significantly fewer peaks than autosomes, consistent with their smaller size and unique biological regulation.

3. Length Consistency

    Finding: Box plots show that the median peak length and interquartile range are remarkably consistent across all autosomes.
Insight: This suggests a conserved fundamental structure of open chromatin across the genome, with biological mechanisms of accessibility operating uniformly across chromosomes.
