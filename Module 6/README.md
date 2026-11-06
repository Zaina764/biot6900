# BIOT 6900 · Module 6 Assignment: PRS Portability Across Ancestries

**Name:** [Zaina Akhtar]
**Course:** BIOT 6900 · Computational Lab 6 · Fall 2026
**Part I disease:** Ovarian carcinoma

## What this module does
I computed a polygenic risk score (PRS) on real 1000 Genomes genotypes and tested how
well it works across five ancestry groups (EUR, AFR, EAS, SAS, AMR). The notebook
harmonizes alleles (keep / flip / drop), computes the PRS, and measures the score
distribution, a single top-10% cutoff, discrimination (AUC), calibration, and the
value the score adds to age alone.

## Which score I used, and why it is not an ovarian score
My Part I disease is ovarian carcinoma, but I ran the course-provided Alzheimer's
score **PGS000334** (22 variants; Zhang et al., 2020).

- The course genotype panel (`genotypes.csv`) contains only 23 variants, built to
  match PGS000334.
- An ovarian cancer score such as PGS000068 (15 variants; Yang et al., 2018) would
  have almost none of its SNPs in this panel, so an ovarian PRS cannot be computed on
  this data.
- The simulated phenotype was also generated from the PGS000334 variants, so an
  ovarian score would show no real signal even where SNPs overlapped.

I contacted the instructor to confirm this approach. The portability problem shown
here applies to ovarian cancer too: published ovarian scores were also built almost
entirely in women of European ancestry.

## Data
| File | Source |
|------|--------|
| `genotypes.csv`, `variants.csv`, `meta.csv` | Course `data.zip` (Canvas); genotypes from the 1000 Genomes Project (2015) |
| `score.csv` | PGS000334, PGS Catalog, provided in the course `data.zip` |

`data/` is not committed (listed in `.gitignore`). To rerun, download `data.zip`
from Canvas and unzip it so the four CSVs sit directly in `Module 6/data/`.

## How to run
1. `conda activate biot6900`
2. Open `BIOT6900_Module6_Part3_Graded.ipynb` with the `biot6900` kernel.
3. Kernel → Restart and Run All. `USE_DEMO` is `False`; Section 2 should show
   `source: REAL`.

## Files
- `BIOT6900_Module6_Part3_Graded.ipynb`: the completed notebook, run on real data
- `figures/fig_prs_by_ancestry.png`: PRS distribution per ancestry with the pooled top-10% cutoff
- `figures/fig_auc_by_ancestry.png`: AUC per ancestry
- `figures/fig_calibration.png`: calibration of a EUR-fitted model in each ancestry
- `Module6_Report.pdf`: the report

## Disclosures and what did not work
- **Phenotype is simulated.** 1000 Genomes has no disease labels, so case status is
  simulated by the course. The PRS and its distribution use real genotypes; AUC and
  calibration are illustrative only.
- **No ovarian score possible.** See above.
- **APOE caveat.** The simulation's LD proxy for APOE e4 is almost absent in the
  African-ancestry samples, so the score runs near chance in AFR. This is an
  artifact of the simulated data, not evidence that e4 is unimportant in
  African-ancestry people. Section 3.6b recomputes AUC without the APOE SNPs to
  test this.
- **Score variants not in the panel:** [0].
- **Changes to the starter:** I added saved figures, a count of score variants
  missing from the panel, a calibration summary table, and the APOE check (3.6b).

## References
- Zhang, Q., Sidorenko, J., Couvy-Duchesne, B., et al. (2020). Risk prediction of
  late-onset Alzheimer's disease implies an oligogenic architecture. *Nature
  Communications, 11*, 4799.
- Yang, X., Leslie, G., Gentry-Maharaj, A., et al. (2018). Evaluation of polygenic
  risk scores for ovarian cancer risk prediction in a prospective cohort study.
  *Journal of Medical Genetics, 55*(8), 546–554.
- The 1000 Genomes Project Consortium. (2015). A global reference for human genetic
  variation. *Nature, 526*(7571), 68–74.
- Lambert, S. A., et al. (2021). The Polygenic Score Catalog as an open database for
  reproducibility and systematic evaluation. *Nature Genetics, 53*, 420–425.