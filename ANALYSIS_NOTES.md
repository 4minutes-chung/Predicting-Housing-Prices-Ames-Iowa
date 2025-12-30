### 80/20 train-test baseline + residuals (OLS)
Validation RMSE (log scale): 0.13222726287064454
That’s not terrible for a dumb baseline linear model with lots of dummies.

Interpretation :
- Confirmed there exist relationship/ correlation of the features with house prices.
- 

Residual table with mean near 0 is good (no big bias)
- Linear regression assumption fulfiled: iid errors mean zero.
- std around 0.13 matches RMSE scale.

Here above focus on predictive power rather than RMSE. Therefore, ignoring coefficient's bias.
For plain LinearRegression, it can cause unstable coefficients, but prediction can still work.


###  OLS KFold Interpretation: 
We trained the same OLS model 10 times. Each time, a different 10% of the data was held out. 
We measured prediction error on log(SalePrice).

Mean RMSE: 0.148, which is larger than the 80/20 split: 0.1322.
Std RMSE: 0.045, reflect model is unstable. 	


* After get_dummies, there is ~300 regressors, which many of them are highly correlated, redundant, and mutually exclusive (dummy variables). This violates the “well-conditioned X′X” assumption.If X'X is nearly singular (non-invertible):	•	coefficients explode	•	small data changes → big prediction swings	•	CV variance increases--> Therefore, OLS is unbiased but OLS is high-variance. This is textbook bias–variance tradeoff.

More Reasons:
1. Different data split difficulty
The single 80/20 split might have been “easy” (validation set similar to training).
K-fold averages across many splits, including harder ones → usually more honest about the true model performance.
2.	High variance model
OLS with tons of dummies is unstable. One lucky split (80/20 one) gives a good score, but some folds blow up (you saw 0.25-ish folds). K-fold exposes the true color.
3.	Evaluation noise
80/20 uses only 20% for validation once → noisy estimate for validation.
K-fold uses all points as validation across folds → less luck-driven.

Therefore, while higher, K-fold is the better estimate of true performance of the OLS model.


