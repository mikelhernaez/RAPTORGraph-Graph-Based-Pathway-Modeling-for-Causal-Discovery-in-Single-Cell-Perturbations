# Manuscript Audit — `latex-raptorgraph-plos_comp_bio26/main.tex`

Comprehensive audit against PLOS Computational Biology submission rules and
internal-consistency / scientific-assessment standards. Generated 2026-11-02.

## A. PLOS Formatting Rules

| # | Requirement | Status | Evidence / Note |
|---|---|---|---|
| 1 | Abstract ≤ 300 words | ✅ **161 words** | Within limit |
| 2 | No citations in Abstract | ✅ 0 `\cite` | Clean |
| 3 | No specialist abbreviations in Abstract | ✅ Fixed | Expanded CRL → "Causal representation learning", MSE → "mean squared error", MMD → "maximum mean discrepancy" in main.tex Abstract (168 words) |
| 4 | Author Summary 150–200 words | ✅ **183 words** | Within range |
| 5 | Author Summary first-person | ✅ | "We developed…" |
| 6 | **Double-spaced text** | ✅ Fixed | `\usepackage{setspace}` / `\doublespacing` now **enabled** in main.tex:75–76 and packages.tex:49–50, per the template's "Remove comment for double spacing" instruction and the PLOS guideline that manuscript text be double-spaced |
| 7 | Continuous line numbers | ✅ | `\linenumbers` (line 610); numbers disabled before refs |
| 8 | Page numbers | ⚠️ | Not explicitly verifiable; standard `article` includes them |
| 9 | No footnotes | ✅ | None found |
| 10 | Single column | ✅ | No multi-column layout |
| 11 | Vancouver (ICMJE) reference style | ✅ | `plos2025.bst` |
| 12 | ≤ 3 heading levels | ✅ | `\section` + `\subsection` only |
| 13 | Citations numbered in order of appearance | ⚠️ | `plos2025.bst` citation-sequence; order follows first citation — verify numbering matches text order |
| 14 | Equations via MathType/Editor | ⚠️ | LaTeX math used (acceptable for LaTeX submissions) |
| 15 | References: full bibliography details | ✅ | 55 entries, 37 cited keys resolve |

## B. Figures & Tables

| # | Check | Status | Evidence |
|---|---|---|---|
| 16 | Figures cited in ascending order at first appearance | ✅ Fixed | Fig 1 (`fig:single_node_intervention`) cited at main.tex:706; Fig 4 (`fig:arch:graphpathway_encoder`) cited with panels A–D at main.tex:948/974/977/981. Order now ascending: 1→2→3→4→5 |
| 17 | Every figure cited in text | ✅ Fixed | 2 of 5 figures were uncited; both now referenced in main.tex and the section sources |
| 18 | Every figure file exists | ⚠️ | Verify `gfx/results/*.png`, `Bildschirmfoto…png`, `OT.png`, `ot_comparison.png` exist |
| 19 | Figure captions: "Fig N." + descriptive title | ⚠️ | Captions present; some lack the required **bold "Fig N."** label prefix (e.g. line 694, 892) |
| 20 | Tables after first paragraph where cited | ✅ | `tab:MMD_results` cited line 781 → table 785; others adjacent |
| 21 | All tables cited | ✅ | `MMD_results`, `objective_results_replogle`, `gi_scores`, `hit_rate` all referenced |
| 22 | Table captions bold title | ✅ | Bold titles present |

## C. Structure & Sections (PLOS required order)

| # | Section | Status | Evidence |
|---|---|---|---|
| 23 | Abstract before Author Summary | ✅ | Lines 581, 593 |
| 24 | Title page / title present | ✅ | Title page block at main.tex:547–578 (full title 91 chars, authors, 7 affiliations, corresponding-author note). Short title (≤70 chars) goes in the PLOS submission form, not in the .tex |
| 25 | Introduction | ✅ | Line 617 |
| 26 | Background | ✅ | Line 653 |
| 27 | Results | ✅ | Line 766 |
| 28 | Discussion | ✅ | Line 904 |
| 29 | Conclusion | ✅ | Line 924 |
| 30 | Materials and Methods | ✅ | Line 940 (placed after Results/Discussion — acceptable, note in cover letter) |
| 31 | Acknowledgments | ✅ | Line 1101; funding properly in Acknowledgments? |
| 32 | Data Availability | ✅ | Line 1105 |
| 33 | Supporting Information captions **last** | ✅ | Line 1126, after bibliography |
| 34 | Funding NOT in Acknowledgments (PLOS: funding only in financial disclosure) | ✅ Fixed | Funding details moved out of the Acknowledgments body into a commented Financial Disclosure block (main.tex:1158–1160) for the submission-system field; Acknowledgments now holds only the general-acknowledgment note |

## D. Scientific Content & Internal Consistency

| # | Check | Status | Evidence |
|---|---|---|---|
| 35 | Every metric defined | ✅ Fixed | MSE, MMD (kernel + population eq), Precision@10 (5 interaction scores), Hit Rate @ K (Correct + Relevant) now defined with equations in Methods "Evaluation setup and metrics" (main.tex / 03_methods.tex) |
| 36 | Trivial references for reconstruction (AGENTS standard) | ⚠️ | All-zero / per-gene-mean baselines not reported in tables; §6.5 mandates these |
| 37 | GEARS excluded — justified | ✅ | Footnote * explains exclusion |
| 38 | Statistics stated (n, mean±variance, runs) | ✅ | "3 runs", mean ± variance throughout |
| 39 | Error at observed zeros vs positives separated | ⚠️ | Only overall MSE/MMD; no zero/positive split, no per-gene error |
| 40 | Biological fidelity vs. reconstruction distinguished | ⚠️ | GSEA gives program evidence; covariance/gene-variation checks absent |
| 41 | Ablation study present | ✅ | β, μ, λ₁; OT ablation |
| 42 | Limitation section | ✅ | Discussion lines 912–914 |

## E. Terminology / Claims

| # | Check | Status |
|---|---|---|
| 43 | "atomic (single-node)" clarification | ✅ Consistent (Req 2, theorem, Fig 1) |
| 44 | scGen described as "deep generative" not Transformer | ✅ Fixed |
| 45 | dVAE/SENA described as effectively β-VAEs (careful phrasing) | ✅ |

## Priority findings (actionable)

1. ~~**Two figures are never cited**~~ — **Fixed**: `fig:single_node_intervention` cited in Background (main.tex:706); `fig:arch:graphpathway_encoder` cited with panels A–D in Methods (main.tex:948/974/977/981), matching the older manuscripts' usage.
2. ~~**Double-spacing is disabled**~~ — **Fixed**: enabled in main.tex and packages.tex.
3. ~~**Abstract uses specialist abbreviations** (CRL, MSE, MMD)~~ — **Fixed**: expanded to full terms in main.tex Abstract.
4. ~~**Funding is listed in Acknowledgments**~~ — **Fixed**: moved into a commented Financial Disclosure block (main.tex:1158–1160) for the submission form; PLOS requires funding only there, not in the manuscript.
5. **§6.5 trivial-reconstruction references absent** — mean/zero baselines not in the metric tables (matters for the AGENTS scientific-assessment standard, less so for PLOS format).
