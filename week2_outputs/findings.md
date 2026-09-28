## 8. Findings and interpretation

**Main result.** Cross validation selected **Elastic Net**. On 10,000 held out loans, its RMSE was
**3.801 percentage points**, MAE **2.862 points**, and R² **0.398**.
The mean baseline RMSE was 4.899 points; the selected model reduced it by 22.41%.
These are measurements of historical pricing prediction, not default detection or a causal pricing recommendation.

**Regularization and expectations.** The best regularized CV result was Elastic Net, improving mean CV RMSE over OLS by 0.00031 points. This numerical difference alone is not a statistical significance result.
At the selected penalties, ridge retained 40 coefficients and lasso retained 31.
Sparse coefficients are a compact representation; a zero coefficient does not prove a variable has no economic relationship.

**EDA connection.** The largest absolute numeric pairwise correlation was between
`open_acc` and `total_acc` (r = 0.719).
This supported comparing shrinkage approaches, while missingness and mixed scales motivated fold specific imputation and standardization.

**Overfitting check.** The selected model's development training RMSE was 3.715 points,
CV RMSE 3.722 (fold SD 0.035), and test RMSE 3.801.
This comparison describes generalization on the chosen split; it cannot prove absence of overfitting.
Convergence warnings during tuning: {'Ridge': 0, 'Lasso': 0, 'Elastic Net': 0}.
Models selecting a search grid boundary: none.
A boundary optimum means the grid may constrain the conclusion; future expansion must use development data rather than react to test scores.

**Practical implication.** The comparison quantifies the tradeoff between prediction error and coefficient sparsity.
If model differences are very small, simpler interpretation may be more valuable than the smallest numerical error.
The residual plots indicate where a linear pricing approximation is imperfect; they are diagnostic, not evidence of lending policy fairness.

**Limits and next steps.** Accepted loan selection, changing pricing policies across 2007–2018, extreme predictor values,
and unavailable/repeated borrower identifiers limit interpretation. This one-dataset notebook does not implement the planned FRED or banking-data integration.
A later analysis should evaluate a chronological holdout and investigate nonlinear or interaction terms using development data.

