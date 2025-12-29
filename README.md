# House Prices (Ames Housing) — Model Comparison

This project benchmarks linear and tree-based models on the Ames Housing dataset.

**Target**
- log(SalePrice)

**Evaluation**
- 10-fold cross-validated RMSE (log scale)

**Models**
- OLS, Ridge, Lasso, Elastic Net
- Random Forest
- Gradient Boosting
- XGBoost

**Best result**
- XGBoost: CV RMSE ≈ 0.117 (stable across folds)

**Notes**
- Focus is on model comparison and regularization, not leaderboard optimization.
- Dataset source: Kaggle House Prices (Ames).
