    # Module 4: Structure-based druggability

    **Name:** Zaina
    **Disease:** Ovarian carcinoma
    **Targets:** FGFR2 (P21802, compared with PDB 1OEC chain A) and DCLK1 (O15075, compared with PDB 7KXW chain A)

    ## Files
    - `BIOT6900_Module4_Assignment.ipynb`: analysis notebook with outputs
    - `structure_assessment_ovarian.csv`: summary table
    - `REPORT.pdf`: written report

    ## How it was run
    Run on the Northeastern Explorer cluster (JupyterLab, conda env `biot6900` with fpocket 4.0),
    because fpocket does not run on Windows. Kernel → Restart & Run All completed with no errors.
    One line was added at the top so the kernel can find fpocket.

    ## Notes
    - The `structures/` folder (downloaded AlphaFold and PDB files) is not committed.
    - The ligand-site check also listed TPO A484 in 7KXW; this is a phosphothreonine
      (a modified residue), not a drug, so XBD (DCLK1-IN-1) is the ligand analysed.