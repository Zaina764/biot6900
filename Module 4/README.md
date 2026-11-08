# Module 4: Structure-based druggability

**Name:** Zaina Akhtar
**Disease:** Ovarian carcinoma
**Targets:** FGFR2 (P21802, compared with PDB 1OEC chain A) and DCLK1 (O15075, compared with PDB 7KXW chain A)

## Files
- `BIOT6900_Module4_Assignment.ipynb`: analysis notebook with outputs
- `structure_assessment_ovarian.csv`: summary table
- `REPORT.pdf`: written report

## How it was run
Run on the Northeastern Explorer cluster (JupyterLab, conda environment `biot6900`
with fpocket 4.0), because fpocket does not run on Windows. Kernel -> Restart & Run All
completed with no errors. One line was added at the top of the notebook so that the
kernel can find fpocket on the cluster.

## Results
- FGFR2: RMSD 0.76 A to 1OEC over 250 confident residues; top pocket (score 0.864,
  verdict keep) covers 100% of the inhibitor site. Call: structure supports a
  small-molecule pocket.
- DCLK1: RMSD 1.59 A to 7KXW over 242 confident residues; best kept pocket (score 0.471)
  does not overlap the inhibitor site, and the pocket that does ranks 16th. Call:
  possible but uncertain.

## Notes
- The `structures/` folder (downloaded AlphaFold and PDB files) is not committed.
- The ligand-site check also listed TPO A484 in 7KXW. This is a phosphothreonine,
  a modified residue of the protein chain rather than a drug, so XBD (DCLK1-IN-1)
  is the ligand analysed in the report.
- Two extra cells were added at the end of the notebook to print the residue ranges
  lining the key pockets, used in report questions 3, 5 and 6.
