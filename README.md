# Trisomy 21 Perturbs Oligodendrocyte Developmental States and Oligo–Neuron Communication in Human Forebrain Assembloids

Analysis code accompanying:

> Baker Campbell N.\*, Khanna S.\*, Kim M., Kharitonova E.K., Weidman M.P., Headings C., Chung C., Chung S., Field G., Linetsky M., Thunemann M., Campbell J., Medalla M., Zeldich E. *Trisomy 21 Perturbs Oligodendrocyte Developmental States and Oligo–Neuron Communication in Human Forebrain Assembloids.* [Journal, Year, DOI — to be added]
>
> \*These authors contributed equally.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

---

## Overview

We used isogenic euploid and trisomy 21 iPSC-derived forebrain assembloids (FAs) from three cell line pairs (WC-24-02-DS, ILD, DS1-iPS4) and profiled them at 150 days in vitro by single-cell (scRNA-seq) and single-nucleus (snRNA-seq) RNA sequencing. This repository contains the code used to:

1. Perform quality control and integrate scRNA-seq and snRNA-seq data
2. Annotate cell types and compare cell-type composition between genotypes
3. Subcluster and characterize oligodendrocyte lineage cells (OLLCs)
4. Identify gene programs (Celda modules), STRING association networks and GO enrichment
5. Infer OLLC trajectories (Slingshot pseudotime)
6. Perform paired differential expression (scMetaIntegrator)
7. Infer neuron–OLLC communication (CellChat)
8. Compare FA OLLCs with human fetal and early postnatal reference datasets

## Data availability

| Data | Source |
|---|---|
| FA scRNA-seq and snRNA-seq (raw FASTQs and Cell Ranger count matrices) | GEO: **GSE[XXXXXX]** |
| Human fetal cortex reference | GEO: GSE305146 |
| Early postnatal human prefrontal cortex reference | Risgaard et al. (2026) [accession to be added] |

## Repository structure

| Folder | Content | Figures |
|---|---|---|
| `01_QC/` | Quality control with singleCellTK (mitochondrial content, scDblFinder, DecontX) | Supp. Fig. 3 |
| `02_integration_clustering/` | SCTransform, Harmony integration, clustering and cell-type annotation | Fig. 3 |
| `03_composition/` | Cell-type proportion analysis with propeller | Supp. Fig. X |
| `04_OLLC_subclustering/` | OLLC subclustering, cluster markers, GSEA, genotype enrichment | Fig. 3, Supp. Fig. 6 |
| `05_celda_modules/` | Celda modules, module enrichment, STRING networks | Fig. 4 |
| `06_pseudotime/` | Slingshot trajectory inference | Fig. 3/4 |
| `07_differential_expression/` | scMetaIntegrator DE (OLLC_3 vs OLLC_2; trisomic vs euploid), GO analysis, depth sensitivity check | Fig. 4, Supp. Tables |
| `08_cellchat/` | CellChat per sample, consensus heatmaps, circle plots, L–R bubble plots | Fig. 5, Supp. Fig. 9 |
| `09_reference_comparison/` | Fetal reference correlation; postnatal correlation, module-based mapping and CellChat | Fig. 2, Fig. 5 |
| `utils/` | Shared helper functions | – |

*Update the figure column once figure numbers are final.*

## Requirements

Analyses were run in R 4.4.0 on the Boston University Shared Computing Cluster. Main packages:

- Seurat 5.4.0, SeuratObject, harmony
- singleCellTK, scDblFinder, celda (DecontX, celda_CG)
- slingshot 2.12.0, SingleCellExperiment
- scMetaIntegrator, MetaIntegrator
- CellChat
- clusterProfiler, org.Hs.eg.db, STRINGdb
- speckle (propeller)
- ggplot2, dplyr, tidyr, pheatmap, igraph, ggraph, openxlsx

Full package versions are listed in `sessionInfo.txt`.

Upstream processing: Cell Ranger 7.2.0 (scRNA-seq; GRCh38-2024-A) and Cell Ranger ARC 2.0.1 (snRNA-seq, 10x Multiome gene expression; GRCh38).

## Usage

1. Download the count matrices from GEO (GSE[XXXXXX]) and the reference datasets listed above.
2. Set the data and output paths at the top of each script (`data_dir`, `out_dir`).
3. Run the folders in numerical order; each script reads the objects saved by the previous step.

## License

This code is released under the MIT License (see `LICENSE`).

## Citation

If you use this code, please cite the publication above and the archived version of this repository (Zenodo DOI: 10.5281/zenodo.XXXXXXX).

## Contact

- Sonal Khanna (sonaldk@bu.edu)
- Ella Zeldich (ezeldich@bu.edu) – corresponding author
