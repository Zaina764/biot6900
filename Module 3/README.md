# Module 3: Target Triage with Protein Language Models in Ovarian Carcinoma

**BIOT 6900 · Module 3 Assignment (Computational Lab 3)** · Zaina Akhtar · Northeastern University · Disease: **ovarian carcinoma**

This module adds a tractability check to my 15 ovarian carcinoma targets from Module 2. It asks whether each target resembles proteins we already know how to drug, and with which modality (small molecule or antibody). It also scores the course anchor variants (APOE ε2 and ε4, TREM2 R47H, and the TP53 R175H hotspot) and re-ranks the targets for Week 4 (structure prediction).

## Contents

| Path | Description |
|---|---|
| `BIOT6900_Module3_Assignment.ipynb` | Assignment notebook (Steps 1 to 7), runs top to bottom with Restart & Run All |
| `targets_ovarian.csv` | Input: my Module 2 top 15 ovarian targets (copied from `../module2`) |
| `targets_ovarian_w3.csv` | **Deliverable:** re-ranked targets, the hand-off to Week 4 |
| `REPORT.pdf` | Written report (4 pages, with figures) |
| `data/` | The course data pack from Canvas (`BIOT6900_Module3_DataPack.zip`), not committed (see `.gitignore`) |

## Reproducing the analysis

Uses the `biot6900` conda environment with scikit-learn and matplotlib.

1. Download `BIOT6900_Module3_DataPack.zip` from the Module 3 Canvas page, unzip it, rename the folder to `data`, and put it in this folder (the files sit directly inside `data/`).
2. Open `BIOT6900_Module3_Assignment.ipynb` in VS Code, select the `biot6900` kernel, and run **Restart and Run All**. This writes `targets_ovarian_w3.csv`.

## The data pack

The analysis uses the course data pack: a 1,201-protein training panel with small-molecule and antibody clinical-precedence labels and family groups, ESM C embeddings for the reviewed human proteome, and ESM-2 650M variant scores. Variants use UniProt precursor numbering, which includes APOE's 18-residue signal peptide, so R176C is mature R158C (ε2) and C130R is mature C112R (ε4).

## Results summary

- All 15 of my Module 2 targets mapped to a reviewed protein; none were unmapped.
- Leakage guard: 1 of my targets was in the training panel and was removed, leaving 1,200 proteins.
- Family-split validation: AUROC 0.743, average precision 0.548 (chance level 0.333). The random split gave 0.833 and 0.706.
- FGFR2 stayed at rank 1 (p_sm 0.865, nearest neighbour FGFR1 at 0.99). DCLK1 moved up the most relative to its Week 2 position. No target moved more than three places with w = 0.6.
- Sent forward to Week 4: FGFR2 and DCLK1.

## Issues encountered

- No column renaming was needed, since `targets_ovarian.csv` already has `gene` and `score`.
