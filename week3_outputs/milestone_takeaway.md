## Week 3 findings

My CV comparison selected **PLSR**. Its test RMSE was **3.802 percentage points**, compared with **3.802** for all-feature OLS. Its test MAE was 2.861 and its R² was 0.398. Forward selection retained 9 of the 15 original features; backward selection retained 9. PCR selected 20 components and PLSR selected 20.

What matters to me is the error I give up, if any, in return for a smaller model. A selected feature is not automatically a cause of pricing, and a dropped feature is not automatically irrelevant. Correlated predictors can substitute for each other, and a different sample may produce a different selection path. The component plots also separate two ideas: explaining predictor variation and predicting interest rate.

For Milestone One, I will compare this with Week 2's regularization results using matching split manifests. I will check selection stability and use later loan vintages before claiming the result holds over time. This analysis describes accepted-loan pricing; it does not measure default detection.