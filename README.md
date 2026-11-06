**[Read the Full Report (PDF)](https://github.com/libryan1/ames_housing_prices_libryan1/blob/main/ames_housing_prices_report.pdf)**

# Overview
This project is based on Kaggle's [House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) competition. The objective is to predict the sale price of a house using its characteristics. Two datasets are provided, the training data and the testing data. Only the training data has the actual sale prices of the houses included. Models are created using the training data, and made to predict the prices of the houses in the testing data. The predicted prices are then submitted to Kaggle, which returns the root mean square logarithmic error (RMSLE) of the predictions. 

# Methods
The analysis was conducted in R. A transformed version of the training data was created, henceforth referred to as the refined data. The same transformations, excepting the removal of any houses, were also performed to create a transformed version of the testing data. These transformations were conducted to address multicollinearity, existence of nonlinear relationships between the response and predictors, and the presence of a high-leverage point. Root mean square error was used as the evaluation metric.  OLS regression, shrinkage, smoothing splines, KNN, and decision-tree based models were created, with their performance evaluated via cross-validation. 

# Results
![CV RMSE by Model](Figures/cv_rmse_by_model_graph.png)

Though smoothing splines on the refined data could outperform ridge regression on the refined data, it was deemed too unreliable due to its significantly higher variability, thus ridge regression was selected. It achieved a RMSLE of 0.1294 on Kaggle. 

While ridge regression on the refined data achieved the best cross-validation performance, 3 other models achieved similar results. All were built on the refined data. They were the LASSO, elastic net, and boosting models. Their predictions on the testing data were also submitted to Kaggle, achieving RMSLE's of 0.1291, 0.1289, and 0.1295 respectively. In addition, it can be seen that using the refined data greatly improved the performance of OLS regression and shrinkage models. This suggests two things. One, that the issues identified in the training data likely did exist and were, to a degree, successfully addressed by the transformations. Two, that through appropriate data transformations, relatively simple linear models can achieve predictive accuracy comparable to more flexible nonlinear approaches to this problem.

# Repository Contents
## Reports
[`ames_housing_prices_report.pdf`](https://github.com/libryan1/ames_housing_prices_libryan1/blob/main/ames_housing_prices_report.pdf): Full report, viewable on GitHub

[`ames_housing_prices_report.html`](https://github.com/libryan1/ames_housing_prices_libryan1/blob/main/ames_housing_prices_report.html): Full report, HTML version, download only

[`ames_housing_prices_report.qmd`](https://github.com/libryan1/ames_housing_prices_libryan1/blob/main/ames_housing_prices_report.qmd): Source document for both report formats

## Code
[`\Code\ames_housing_prices.qmd`](https://github.com/libryan1/ames_housing_prices_libryan1/blob/main/Code/ames_housing_prices.qmd): Quarto document containing all statistical analyses

`Code\final_test_preds.csv`: Ridge regression predictions

`Code\lasso_preds_df.csv`: LASSO predictions

`Code\elastic_preds_df.csv`: Elastic net predictions

`Code\boost_preds_df.csv`: Boosting predictions

## Other Files

`\Figures`: Figures used in the report.

`Code\Data`: Kaggle datasets and saved cross-validation results
