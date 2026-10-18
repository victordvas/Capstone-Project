## Week 1 findings from this run

CV selected **Cubic**. Its test RMSE was **3.749 percentage points**, MAE was **2.806**, and R² was **0.414**. The main-effects model's test RMSE was **3.802**. The main-effects-minus-selected RMSE difference was **+0.0527 points**; positive means lower error for the selected specification.

CV favored additional terms. I still need to compare the size of the gain with fold variation and the added interpretation cost. I expected curved terms might help, but they do not have to improve prediction. The selected model used **56 encoded terms**, so the gain should be weighed against the extra complexity.

Training RMSE was **3.642**, compared with **3.660 in CV** and **3.749 on the test split**. These gaps show whether the extra fit carries beyond the training observations; they do not establish future performance.

The VIF comparison separates a numerical issue caused by powers from genuine overlap among predictors. The interaction curves explain what the model has fitted, but they cannot show that changing FICO or DTI would cause a different interest rate. This remains a pricing companion to my default-risk project.
