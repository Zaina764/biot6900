# Module 2 — Ovarian Carcinoma Multi-Omics Target Discovery

## Disease
Ovarian carcinoma

## Datasets

| Layer | Dataset | Source | Link | Access |
|-------|---------|--------|------|--------|
| Transcriptomics (RNA) | CPTAC-OV RNAseq, Gene level, log2 FPKM, 82 tumor samples | LinkedOmics | http://www.linkedomics.org/ | Open |
| Proteomics (protein) | CPTAC-OV Proteome TMT, Gene level, 83 tumor vs 20 normal | LinkedOmics | http://www.linkedomics.org/ | Open |
| Genomics (GWAS) | Ovarian carcinoma associations (MONDO_0005140, with child traits) | GWAS Catalog | https://www.ebi.ac.uk/gwas/ | Open |

## Notes
- No matched normal RNA was available for this cohort so RNA effect is computed as deviation from cohort mean
- RNA and protein are from the same CPTAC-OV study (Zhang et al., Cell 2016) so patients are matched
- GWAS is population-level germline data, separate from the tumor cohort
- Used custom weights (RNA=0.20, Protein=0.40, GWAS=0.40) since RNA layer is weaker without normal samples

## Files
- `Part 3 Ovarian Carcinoma.ipynb` — analysis notebook
- `targets_ovarian.csv` — ranked target table
- `README.md` — this file