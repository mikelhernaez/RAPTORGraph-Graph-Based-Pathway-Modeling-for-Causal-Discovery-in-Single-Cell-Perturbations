# Technical Audit — broken citations / formulas / references

Blind audit of `main.tex` (the flattened PLOS submission) using static checks
plus the `gunz-style` (GS) and `gunz-prose` (GP) audit libraries.
Generated 2026-11-02.

## 1. Citations (static check, main.tex vs references.bib)

- Cited keys: **37**
- Bib entries: **55**
- **CITED BUT MISSING FROM BIB: none** ✅
- In bib but never cited (18): `Hinton06, ahuja2023interventional,
  elfwing2018sigmoid, elhage2021framework, goodfellow2016deep,
  higgins2017beta, jaeger1998confirmatory, jiang2024scpram,
  kanehisa_kegg_2010, kingma2013auto, olah_single_2020,
  ramachandran2017searching, ren2010multiple, thegeneontologyconsortium_gene_2019,
  tran_benchmark_2020, wang_how_2024, yang2020causalvae, zhu2017maximum`
  → harmless dead entries (some are the pending theorem keys).

## 2. References / labels (static check)

- Labels: 21 | Refs used: 15
- **REFS WITHOUT LABEL (broken): none** ✅ (`#1..#4` are macro-parameter
  false positives from `\def` helpers).
- Unreferenced labels (GS017, 10): all equations + `thm:zhang_full_dag`.
  Equations unreferenced is normal; `thm:zhang_full_dag` (the main
  identifiability theorem) is worth citing from the text if the theorem is
  meant to be the formal anchor.

## 3. gunz-style tex rules (structural)

Selected `GS017,GS018,GS019,GS080,GS081,GS082,GS083,GS084,GS085,GS086`.

- **GS080 unclosed math/verbatim: 0** ✅
- **GS085/GS086 env/brace balance: 0** ✅ (10 eq, 4 table, 4 figure, 2
  itemize, 1 theorem all balanced)
- **GS018 unbackslashed math operator: 0** ✅
- GS017 unreferenced labels: 10 (informational; see §2)
- GS019 missing non-breaking tie: real ones **fixed** (lines 781, 847, 1013);
  remaining are inside `\def` macro templates (false positives)
- GS083 space before punctuation: **fixed** (my metric equations)
- GS081: only the `Bildschirmfoto` filename (false positive)

### Fixes applied this round
- `main.tex:847` `and \Cref{tab:hit_rate}` → `and~\Cref{tab:hit_rate}`
- `main.tex:1013` `(see \cref{eq:dagma_loss_full})` → `(see~\cref{...})`
- `main.tex:1089` MSE equation trailing ` ,` → `,`
- `main.tex:1107` MMD equation trailing ` .` → `.`
- mirrored in `sections/03_methods.tex` (tie + MSE comma) and
  `sections/05_results.tex` (tie)

## 4. gunz-prose (style/register, advisory only — NOT errors)

Total 95 lines; no broken references. Finding distribution:
- GP331 long sentence / nominalizations: 49
- GP101 word repetition: 17
- GP330 dense noun cluster: 12
- GP322 prestige vocabulary: 5
- GP321 agent jargon: 3
- GP103 informal register: 3 (`'black box'`, `'simply'`)
- others (GS304, GS309, GP326, GP324, GP320, GP102): 1 each

These are style suggestions for a scientific audience, not correctness
errors. Notable: `'black box'` (GP103) — the manuscript uses this deliberately
to describe baselines; acceptable but could be `'opaque'`. `'simply'` at
line 1110 → `'only'` is a trivial recommended change.

## 5. Structural divergence (main.tex vs sections/)

- `main.tex` (flattened submission) is **clean**: 0 `app:*` references.
- `sections/03_methods.tex` (3), `05_results.tex` (13), `06_conclusion.tex`
  (2) still contain **stale `app:*` references** (e.g. `app:metrics`,
  `app:ot`, `app:dagma`, `fig:app:hit_rate_exact`) pointing at an appendix
  that does not exist in this manuscript.
- These section files are out of sync with the authoritative `main.tex`.
  They are not part of the compiled submission, but should either be
  re-flattened into main.tex or updated to match, to avoid confusion.
