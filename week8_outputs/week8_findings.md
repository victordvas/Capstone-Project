### What I learned from this run

I first checked scaling while keeping Euclidean distance, k = 31, and uniform weights the same. Standardization changed mean CV ROC-AUC from 0.5610 to 0.6474, a difference of +0.0864. Robust scaling reached 0.6437. That supports my expectation that scaling would help here. The distance plot helps me understand what the units are doing to the comparison. The outlier table is also a reminder that scaling does not remove extreme values.

The best result in my training CV search used Manhattan distance, standardized numeric features, k = 61, and uniform weights. Its mean CV ROC-AUC was 0.6627, with fold SD 0.0085. The difference between the top two candidates was 0.0016. I would compare that difference with the fold variation before saying the top model has a meaningful advantage.

To check the effect of the number of neighbors, I kept standardized Euclidean distance and uniform weights fixed. Moving from k = 5 to k = 61 changed CV ROC-AUC by +0.0628. Using more neighbors helped the ranking in this comparison. I used held-out training folds to choose k and kept the test set out of that decision. The selected KNN's training ROC-AUC was 0.7093; removing each training loan from its own neighborhood gave 0.6650. That second score is an extra check. Preprocessing still used the whole training subset, so it does not replace cross-validation. Validation ROC-AUC was 0.6587, and test ROC-AUC was 0.6676.

On the test loans, KNN reached test ROC-AUC 0.6676 and average precision 0.3362. Logistic regression reached 0.6996 and 0.3769, respectively. The charge-off share in the test data was 19.9%. KNN did not beat logistic regression on test ROC-AUC in this run. Both models use the same loans in this notebook.

The cutoff is where I can see the effect on loan reviews. At 0.50, KNN recall was 3.4% and precision was 56.8%. At the validation-selected cutoff of 0.1967, it caught 1,255 of 1,990 charge-offs, missed 735, and flagged 3,102 fully paid loans. Recall was 63.1%, precision was 28.8%, and 43.6% of test loans were flagged. Compared with logistic regression at its own validation-selected cutoff, KNN caught 39 fewer charge-offs and flagged 248 more fully paid loans.

For my project, I would pay close attention to those review counts. Finding more charge-offs could be useful, but I also need to account for the borrowers who would repay and still get flagged. Before choosing a cutoff for practical use, I would check the costs of both errors, the number of reviews the team can handle, and whether the results hold on later loans.
