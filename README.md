# Gut Microbiome Analytics: Healthy vs Polyps vs Colorectal Cancer

Exploring how the gut bacterial community shifts from a healthy colon to adenomatous polyps to colorectal cancer, using 16S rRNA sequencing data, Python, and an interactive Power BI dashboard.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nahlah-CS/gut-microbiome-colorectal-analysis/blob/main/notebook/Final_Project.ipynb)

![Dashboard preview](images/dashboard_preview.png)

## Overview

This project analyzes bacterial DNA from 59 samples (19 healthy, 19 with adenomatous polyps, 21 with colorectal cancer; 6,693 distinct bacterial sequences). It asks three questions:

1. Does bacterial diversity differ between the groups?
2. Does the overall bacterial community differ?
3. Which bacterial genera differ, and could any act as early markers?

## Key findings

- The overall bacterial community differs significantly between the three groups (PERMANOVA pseudo-F = 2.28, p = 0.001), and every pair of groups differs after correction.
- Diversity shows only a borderline trend (Shannon, Kruskal-Wallis p = 0.055).
- Ten of 56 tested genera differ after FDR correction (q < 0.05): six are lower in polyps and cancer, and four rise from healthy to polyps to cancer.
- Unsupervised clustering (PCA + KMeans) did not recover the diagnoses (adjusted Rand index = 0.03), so individual profiles overlap too much to classify a person from bacteria alone.

## Repository structure

```
├── notebook/    Colab notebook with all code and outputs
├── report/      Final report (PDF)
├── dashboard/   Power BI file (.pbix) and PDF export
├── images/      Dashboard preview
└── data/        Input data notes
```

## Methods in brief

- Data matching, quality checks, and rarefaction to 3,844 reads per sample
- Alpha diversity: Shannon, Simpson, observed sequences (Kruskal-Wallis, pairwise Mann-Whitney, Benjamini-Hochberg correction)
- Beta diversity: Bray-Curtis distance, PCoA, PERMANOVA (999 permutations)
- Rarefaction curves to check sequencing depth
- Genus-level differential abundance (Kruskal-Wallis with FDR correction)
- PCA and KMeans clustering

## How to reproduce

1. Open the notebook in Google Colab (button above) or in Jupyter.
2. Place the three input files (`metadata.csv`, `seqtab_nochim_export.xlsx`, `taxa_species_export.xlsx`) where the notebook can read them. The first cells upload them in Colab. See `data/README.md` for the source.
3. Run all cells from top to bottom.
4. Install the libraries listed in `requirements.txt` if running locally.

## Dashboard

Built in Power BI with a layout designed in Figma. It includes sample counts, mean age, mean Shannon diversity, observed ASVs, a PCoA map, top genera, genera that differ between groups, and rarefaction curves, with filters for disease status, sex, and age. Open `dashboard/Gut_Microbiome_Dashboard.pbix` in Power BI Desktop (Windows).

## Limitations

Small sample size (about 20 per group), a single sample per person (associations, not causes), relative abundances only, and exploratory genus-level tests.

## Author

[Your name] | [LinkedIn or email, optional]

## License

[MIT, or remove this section if you did not choose a license]
