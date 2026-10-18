## Week 5 findings

Training CV selected **RBF SVM** with {'kernel': 'rbf', 'C': 1.0, 'gamma': 'scale'}. Its test ROC-AUC was **0.626**, compared with **0.700** for logistic regression fitted on the same 8,000 loans. Its average precision was 0.324. At the validation-selected score threshold of -0.995, recall was **57.3%**, precision was **27.3%**, and F1 was **0.369**. That caught 1,140 charged-off loans, missed 850, and flagged 3,041 fully paid loans. Default-threshold recall was 0.0%.

The kernel search shows whether extra flexibility helped on this sample. I would not choose a nonlinear kernel just because its boundary looks more complicated. The CV spread, training-versus-test gap, convergence results, and run time all matter. The SVM scores are useful for ranking, but I cannot describe them as default probabilities.

This comparison uses a training subset and a historical test split already used in Week 4. It does not establish performance on future applicants or rejected loans. Next I will compare these results with Week 6 on matching source-row manifests, then test a time-based split and a threshold based on actual review costs.