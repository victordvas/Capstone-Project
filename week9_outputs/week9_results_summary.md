### What I learned from these results

**Dataset reference:** https://www.kaggle.com/datasets/wordsforthewise/lending-club (accepted loans, version 3; data read from a local or KaggleHub-cached CSV/CSV.GZ).

The cross-validation search selected **200 trees**, with a learning rate of **0.05**, maximum depth **2**, minimum leaf size **50**, and subsample **0.80**. Its mean training ROC-AUC was **0.746**, compared with **0.687** in cross-validation. That gap is useful because it tells me whether the model seems to be learning the training data more easily than new folds.

On the test split, gradient boosting reached **ROC-AUC 0.697** and **average precision 0.380**. That ROC-AUC was **lower than logistic regression's 0.700** and **higher than the random forest's 0.688** on the same loans. A difference this small should not automatically be treated as meaningful without a stability check.

With the validation-selected cutoff of **0.188**, boosting caught **1,330 charged-off loans** and missed **660**. It also flagged **3,135 fully paid loans**. That gave it **66.8% recall** and **29.8% precision**. Compared with the matched logistic model, boosting flagged **+281 more fully paid loans** and detected **+36 more charge-offs**. For me, that trade-off matters at least as much as a change in ROC-AUC.

**What changed in the hyperparameter tests:** Starting with the reference setting (CV ROC-AUC **0.686**), the controlled comparisons gave: smaller learning rate (0.683; difference from reference -0.003); larger learning rate (0.682; difference from reference -0.004); fewer trees (0.683; difference from reference -0.003); more trees (0.683; difference from reference -0.003); shallower trees (0.680; difference from reference -0.006); deeper trees (0.680; difference from reference -0.006); smaller leaves (0.684; difference from reference -0.002); larger leaves (0.687; difference from reference +0.001); no row subsampling (0.684; difference from reference -0.002). These are differences observed on three training CV folds, not guarantees of future improvement. In particular, the learning-rate comparisons held the number of trees constant, so they do not tell me which learning-rate/tree-count combination would win a broader search.

**Did the extra complexity generalize?** The final boosting model's test ROC-AUC minus CV ROC-AUC was **+0.010**. I interpret that difference alongside the training–CV gap, the fold variation, and both baseline models rather than treating one test result as conclusive. If a change in ranking comes with many more fully paid loans flagged, its usefulness depends on whether the extra reviews are justified.

The two strongest features in this fitted boosting model by permutation importance were **term** and **fico_range_low**. That is a description of how the model uses this sample, not proof that changing those features would change repayment behavior.
