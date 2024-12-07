# Model Card: Financial Time Series Classification Pipeline with Random Forest and XGBoost

## Model Description

**Input:** 
- Time series financial data
- Features include both numerical and categorical variables
- Data maintains temporal ordering
- Numerical features are standardized using StandardScaler
- Categorical features are encoded using OneHotEncoder

**Output:** 
- Classification predictions for financial time series data
- Probability scores for each class
- Model performance metrics including accuracy scores
- Cross-validation results maintaining temporal order
- Backtest of sample performace

**Model Architecture:** 
The pipeline implements two model variants:

1. Random Forest Classifier
   - Ensemble learning method using multiple decision trees
   - Configured with optimized hyperparameters:
     - n_estimators: 200
     - max_depth: 10
     - min_samples_split: 10
     - min_samples_leaf: 4
     - max_features: 'sqrt'

2. XGBoost Classifier
   - Gradient boosting implementation
   - Configured with optimized hyperparameters:
     - n_estimators: 200
     - max_depth: 3
     - learning_rate: 0.01
     - min_child_weight: 3
     - subsample: 0.8
     - colsample_bytree: 0.8
     - gamma: 0

## Performance

- Overall Accuracy: ~39% for both Random Forest and XGBoost models
- Evaluation Method: TimeSeriesSplit with 5 folds to maintain temporal ordering
- Hyperparameter Optimization: GridSearchCV with time series cross-validation
- Validation Strategy: Proper time series validation to prevent future data leakage
- Backtest of sample performace shows a sharpe ratio of 0.54 in the 2021-2024 out of sample period.

## Limitations

1. Moderate Accuracy
   - Current accuracy of 39% indicates room for improvement but better thn the 1/3 random, extremely difficult to predict future returns. 
   - May need enhanced feature engineering or alternative modeling approaches
   - Sharpe ratio of 0.54 in the 2021-2024 out of sample period, profitable but not enought.

2. Computational Resources
   - Grid search across multiple hyperparameters can be computationally intensive
   - Large number of trees and deep structures may impact inference time

3. Data Dependencies
   - Requires high-quality, consistent financial time series data
   - extremely difficult to predict future returns

## Trade-offs

1. Model Complexity vs. Performance
   - Random Forest offers better interpretability but may miss complex patterns
   - XGBoost can capture more complex relationships but requires more careful tuning to prevent overfitting

2. Feature Engineering
   - More sophisticated feature engineering could improve performance but would increase pipeline complexity

3. Temporal Considerations
   - Strict temporal ordering in cross-validation prevents data leakage but may result in lower apparent performance
  