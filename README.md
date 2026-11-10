# SWYNEX-Biological-Dataset-Selection

**Task 1 — Biological Dataset Selection** | SWYNEX Technologies Internship (Bioinformatics)
**Author:** Prathivraj

---

## 1. Selected Dataset

**Gene Expression Cancer RNA-Seq** (TCGA Pan-Cancer, Illumina HiSeq)

| Item | Details |
|---|---|
| Repository | UCI Machine Learning Repository |
| Dataset page | https://archive.ics.uci.edu/dataset/401/gene+expression+cancer+rna+seq |
| DOI | https://doi.org/10.24432/C5R88H |
| Original data | TCGA Pan-Cancer Analysis Project (Synapse: syn4301332) |
| Creator / donor | Samuele Fiorini (donated 2016) |
| Data type | RNA-Seq gene expression (real-valued, multivariate) |
| Platform | Illumina HiSeq |
| License | CC BY 4.0 (free to use with credit) |
| Access | Public, no login required |

---

## 2. Dataset Size

| Item | Value |
|---|---|
| Samples (rows) | 801 |
| Features (columns) | 20,531 genes |
| Classes | 5 tumor types |
| Missing values (as reported by UCI) | None |
| Download size | 69.5 MB (`TCGA-PANCAN-HiSeq-801x20531.tar.gz`) |

**Files in the archive**

- `data.csv` — gene expression matrix (one row per patient sample, one column per gene)
- `labels.csv` — cancer type of each sample

Gene columns are anonymised as `gene_0 … gene_20530`. Samples are named `sample_0 … sample_800`.

---

## 3. Class Distribution

| Code | Cancer type | Samples |
|---|---|---|
| BRCA | Breast invasive carcinoma | 300 |
| KIRC | Kidney renal clear cell carcinoma | 146 |
| LUAD | Lung adenocarcinoma | 141 |
| PRAD | Prostate adenocarcinoma | 136 |
| COAD | Colon adenocarcinoma | 78 |
| | **Total** | **801** |

The classes are imbalanced (BRCA is the largest, COAD the smallest). This will be taken into account in later analysis.

---

## 4. Research Question

> **Can RNA-Seq gene expression profiles be used to distinguish five different tumor types, and which genes or patterns separate them most clearly?**

**Sub-questions**

1. Do samples of the same cancer type cluster together in a low-dimensional space (e.g., PCA)?
2. Which genes show the highest variation across the dataset?
3. Do the five tumor types have distinct expression "signatures"?

---

## 5. Why This Dataset

- **Public and open.** Free to download under CC BY 4.0, with a DOI for citation.
- **Real biological data.** Derived from TCGA tumor samples, a widely used cancer genomics resource.
- **No lab work needed.** Fully computational, as the task requires.
- **Right size.** Large enough for meaningful analysis (801 × 20,531) but small enough (69.5 MB) for a laptop.
- **Supports all later tasks.** Suitable for cleaning and summary statistics, PCA, heatmaps, boxplots and clustering, and interpretation of expression patterns.

---

## 6. How to Load the Data (Python)

```python
# pip install ucimlrepo pandas
from ucimlrepo import fetch_ucirepo

dataset = fetch_ucirepo(id=401)

X = dataset.data.features   # gene expression matrix (801 x 20531)
y = dataset.data.targets    # cancer type labels

print(X.shape)
print(y.value_counts())
```

Alternatively, download the archive manually from the dataset page above and read `data.csv` and `labels.csv` with `pandas.read_csv()`.

---

## 7. Plan for the Next Tasks

| Task | Plan |
|---|---|
| Task 2 — Data Cleaning and Basic Analysis | Check shape, data types, missing values and duplicates; remove uninformative genes (e.g., zero expression in all samples); summary statistics; class counts |
| Task 3 — Visualization and Interpretation | Class distribution plot, expression histograms, PCA scatter plot, top-variance gene heatmap; interpret the patterns |
| Task 4 — Final Bioinformatics Report | Combine dataset description, methods, results and conclusions into one report |

**Tools:** Python, pandas, NumPy, matplotlib, seaborn, scikit-learn

---

## 8. Limitations

- Gene names are anonymised (`gene_X`), so mapping genes to biological function requires the original submission's probe list.
- Classes are imbalanced.
- The dataset is a random subset of the full TCGA PanCancer collection, so results describe this sample, not all cancers.
- No clinical metadata (age, stage, survival) is included.

---

## 9. References

1. Fiorini, S. (2016). *gene expression cancer RNA-Seq* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5R88H
2. Weinstein, J. N., et al. (2013). The Cancer Genome Atlas Pan-Cancer analysis project. *Nature Genetics*, 45(10), 1113–1120.

---

*No lab work was performed. All data used is publicly available.*
