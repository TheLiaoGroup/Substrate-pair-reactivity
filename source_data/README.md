# Source Data

Substrate-pair reactivity is what yield models fail to carry to new combinations

Numerical source tables for main Figures 1–5, supplementary Figures S1–S7, Table 1, Tables S1A–S1B and S2, and Supplemental Notes 1–4. `PANEL_SOURCE_MAP.csv` lists the exact files, columns, selections and display units for each panel.

## Contents

- `data/p4_records.csv.gz`: all 406,909 retained records from 19 arrays and 17 transformations, including 378,070 numerical yields. `measurement_status` preserves the distinction between quantified yields, rule-assigned zeros and records without a numerical yield.
- `data/p4_grouped_folds.csv.gz`: new-pair split assignments by array, row UID and seed.
- `data/p4_screens.json`: array metadata, ordered condition vocabularies and five-fold protocols. The legacy field `reaction_family` contains transformation names. Suzuki and Suzuki Bpin share one transformation, as do the two Buchwald–Hartwig arrays. Ullmann etherification and C–O competitive reactions remain distinct.
- `data/benchmarks/`: 288 repeated-well measurements and experimental metadata for the three plate-repeatability comparisons.
- `output/`: original saved scientific summaries and per-seed results for random forest, identity baselines, neural networks, pretrained reaction representations and the two public datasets.
- `chemistry/`: numerical Grignard pair, reagent, partner and pair–condition summaries, including the classifications used in Supplemental Note 4.
- `figure_data/`: convenient tabular selections and aggregations used in individual panels. These come only from the supplied records and saved results.

## Units and metrics

A yield fraction of 1 means 100% yield. Multiply yield fractions and fraction-scale MAE/RMSE by 100 for percent yield or yield percentage points. Multiply fraction-scale squared errors by 10,000 for squared percentage points. Column names ending in `_percent` or `_percentage_points` are already on the displayed scale. The MAE and RMSE columns in `output/p4_unified_rf/diagnostics/rf_model_comparison.csv`, including `rf_group_rmse`, are also already in percentage points. Do not scale them again.

R², Spearman correlations, variance shares and sparsity ratios are dimensionless. Variance shares and relative gains are multiplied by 100 where a panel axis uses percent. Pairing sparsity is (n1+n2−1)/n_pairs, where n1 and n2 are the numbers of distinct substrates in their recorded roles and n_pairs is the number of measured substrate pairs. R² loss is held-out-well R² minus new-pair R². Pair-level R² evaluates each pair's mean yield, weighted by its numerical test-well count. Within-pair R² evaluates deviations from each pair's observed and predicted means. These separately normalized R² values are not additive.

`row` denotes held-out wells and `group` denotes new substrate pairs. The five split seeds are 42, 20261007, 20261008, 20261009 and 20261010. Unless a panel states otherwise, displayed array scores are means over these five seeds. Minimum-to-maximum seed ranges describe overlapping split runs. The higher-mean subset comprises the 11 arrays whose overall numerical mean yield is at least 5%; all 19 arrays remain available in the tables. Legacy JSON subset keys named `all_18` include all 19 arrays; the supplied values and keys are preserved.

For the identity baseline, gain is 1 − SSE(forest)/SSE(identity). The training-median baseline gain is 1 − MAE(forest)/MAE(training median). The matched `both_seen` cohort contains the same test wells under both evaluation protocols, with both individual substrates represented in the new-pair training set.

## Yield-table illustrations

The full Grignard and esterification cell tables preserve row and column order and distinguish `numerical_yield`, `record_without_numerical_yield` and `no_record`. Only `quantified` and `zero_by_rule` records contribute numerical yields. Missing yields and absent records are not assigned zero. Figure 4 uses 16 pairs evenly spaced in pair-mean order and 12 conditions evenly spaced among the 60% most often measured. Its row and condition margins are block means, whereas the variance shares labelled as full-table shares use the complete array. Figure 1 is a schematic illustration using the supplied Grignard block; its hidden-cell outlines describe the test design.

The Figure 4C examples are numbered in descending full-table pair-mean order. Figure 4D includes all 123 measured pairs of the 19 organomagnesium reagents that produced product with at least one partner; its group means weight pairs equally (12 amino or N–H partners and 111 others). The broader feature union in Supplemental Note 4 is separately labelled in the chemistry files.

The plate-repeatability comparison uses one repeated reaction per class, with 96 wells per plate and sample SD (ddof = 1); these measurements do not define a universal analytical noise floor. Public-dataset result tables contain the saved five-seed scores underlying the plotted values.

Data and code: https://github.com/TheLiaoGroup/Substrate-pair-reactivity

DOI: https://doi.org/10.5281/zenodo.23319287
