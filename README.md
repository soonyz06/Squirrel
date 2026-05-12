# Squirrel

## 1. Does a squirrel's location within Central Park influence its behavioural patterns, and can we identify distinct spatial zones in the park that correspond to specific behaviours such as foraging, running, or eating?
- Basic data cleaning and feature extraction  
- Added missing flags instead of remove/impute to find patterns in missingness
- Spatial-related plots and relationship plots (corr, MI, etc)

## 2. As a prediction component, we aim to determine whether a squirrel's observed shift (AM or PM) can be predicted from its location and behavioural features.
- K-means clustering and KNN smoothing to create new features from spatial data
- Label, one-hot, target and/or frequency encoding for categorical variables (amongst other stuff)
- Base models: Logistic Regression, Random Forest and XGBoost (TARGET="SHIFT")
- Pass 1: Use K-folds CV to get mean SHAP values and permutation importances across folds, then select the top k features based on equally-weighted ranks
- Pass 2: Use CV again to get OOF predictions and test predictions using top k features
- Majority voting which equally weights all test predictions to produce the final predictions
- Meta-model (LR): Learns relationships between the base models' OOF predictions and "SHIFT", then uses test predictions to produce the final predictions, achieving 96% ROC-AUC (+35% vs baseline RF) or 75% ROC-AUC (+15% vs baseline RF) dependent on inclusion of temporal features

## Plots
- Spatial-plots to see dominant behaviour distribution across hectares/clusters
- Correlation of behaviours with change in coordinates (X, Y, HectareSN, HectareWE)
- Mutual information between spatial-related labels and behaviours
- Heatmap to see mean behaviour across clusters (pseudo probability)
