# Paper Revision TODO

Note: **CRITICAL: DO NOT REMOVE ANYTHING BLUE!**

## Abstract and Text
1. [x] Emphasize that our meta-pathways are different from biological pathways.
2. [x] Clarify that single node intervention is required for identifiability.
3. [x] Formulate the method as "VAE" instead of "beta-VAE".
4. [x] Move the HPO details to the supplementary material.
5. [x] Keep Replogle2020 results in the supplementary material.
    - 5.1 [x] Ensure the main text guides the reviewer to these supplementary results.
6. [x] Create a new section in the supplementary specifically for results (currently mixed with loss functions and metrics).
7. [x] Ensure the term "Causal Meta-Pathways" is used consistently throughout the paper.
8. [x] Standardize terminology from "MK-MMD" to "MMD" (Reframing multi-kernel as implementation detail).

## Sections & Figures

### General Sections
1. [x] **Abstract:** Reduce length (~6 sentences).
2. [x] **Section 4.2:** Ensure the 2nd paragraph starts with: "For evaluation we use datasets: ".
3. [x] **New Section:** Add a new section titled "RAPTORGraph learns biological meaningful causal latent factors" and include a figure (reverted from main for now).

### Equations
1. [x] Remove Equation 3 (put it inline).
2. [x] Remove Equation 4 (move it to the supplementary).
    - 2.1 [x] Ensure the definition of $W$ is preserved.
3. [x] Resolve Overfull \hbox in total loss equation (Split across two lines).

### Figure 1
1. [x] Reduce the white space (Integrated from remote).
2. [x] Update label: Remove "Latent Space (Pathways)" or replace "Pathways" with "Causal Meta-Pathways" (Integrated from remote).

### Figure 2
1. [x] Move the dense decoder stuff up to reduce white space (Integrated from remote).
2. [x] Remove the legend (the circles) (Integrated from remote).
3. [x] Move the circle "D" to the top of the "Causal Meta-Pathways" text (Integrated from remote).
4. [x] Add "Atomic Intervention" to the figure (Integrated from remote).

### Section 3.3
1. [x] Simplify the section: use a single short sentence separated by semicolons instead of 4 distinct terms.
2. [x] Move the long explanatory paragraphs to the supplementary section on loss functions.
3. [x] Move OT (Optimal Transport) details to the supplementary section regarding data optimization.
4. [ ] If enough space, move small OT section to main paper.
5. [x] Move Figure 3 to the supplementary.

## Agent Interrupted Tasks (Remaining)
1. [ ] Move "pathway_enrichment_heatmap.png" figure back to main Results section (currently in supplementary). Only if reviewers want!
2. [ ] Finalize HPO and OT relocation to supplementary.
3. [x] Reorganize supplementary: Created a dedicated "Experimental Results" section and modularized files (A-I).
4. [ ] Finalize audit for "Causal Meta-Pathway" consistency.
5. [x] Fix Table widths (1, 2, 3) and formatting artifacts (`\%`, `hrule`).
6. [x] Fix bibliography entries and citations (Standardized and annotated via bibtexparser).

## Technical / Build Issues (Fixed)
1. [x] **siunitx:** Replace deprecated `detect-inline-weight` option in `latex/packages.tex` (Updated to v3 syntax).
2. [x] **hyperref:** Resolve "Ignoring empty anchor" warning on line 62 of `main.tex` (Silenced via silence package).
3. [x] **floats:** Update `h` float specifiers to `ht` in `supplementaries/F_extended_results.tex` to resolve LaTeX repositioning warnings.
4. [x] **glossaries:** Enable printed glossary in appendix (Nomenclature section) and silenced warnings.
5. [x] **hyphenation:** Silenced "Command \showhyphens has changed" warning in `main.tex`.
6. [x] **bib:** Resolved duplicate entries (`zhu2017maximum`, `liberzon_molecular_2015`).