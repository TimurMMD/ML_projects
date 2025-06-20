# 🌞 Zelestra Hackathon - Predictive Maintenance for Solar Panels
This project was developed as part of the Zelestra Hackathon, where the primary goal was to develop a machine learning model that predicts performance degradation and potential failures in solar panels using historical and real-time sensor data. The aim is to enable predictive maintenance for solar infrastructure, reducing downtime and optimizing energy output.

# 🔍 Problem Statement
As solar energy systems are integrated into more infrastructures globally, ensuring their uptime and efficiency is crucial. Traditional maintenance approaches are reactive and inefficient. This hackathon tasked participants with designing a predictive model that enables proactive, data-driven maintenance.

# 🧠 ML Approach and Strategy
The full pipeline consists of several key stages:

1. 📊 Data Loading and Exploration
Loaded train.csv and test.csv from Google Drive.

Examined structure with .info(), .describe(), and .head().

Detected column types and distribution anomalies.

2. 🧼 Preprocessing
Dropped unnecessary or constant columns.

Filled missing values.

Removed boolean columns where necessary.

Engineered features based on domain knowledge.

Applied standardization using StandardScaler.

3. 🔧 Model Development
Several models were implemented and fine-tuned using Optuna, a state-of-the-art hyperparameter optimization library:

✅ XGBoost
Tuned parameters: n_estimators, max_depth, learning_rate, subsample, colsample_bytree, reg_alpha, reg_lambda

Used custom_score as the evaluation metric.

🐱 CatBoost
Parameters: iterations, depth, learning_rate, l2_leaf_reg, bagging_temperature, random_strength, border_count

K-Fold cross-validation used for robust scoring.

Standardization was included after initial trials.

🌲 RandomForest
Trained as a baseline ensemble model.

💡 LightGBM
Used early_stopping to avoid overfitting.

Tuned using:

learning_rate, num_leaves, max_depth, min_data_in_leaf

feature_fraction, bagging_fraction, bagging_freq

lambda_l1, lambda_l2

Retrained best parameters for feature importance.

🔥 TabNet
Deep tabular learning model using attention.

Trained with Optuna-optimized parameters.

📈 Evaluation
A custom metric based on RMSE and scaled output was used to evaluate all models. The models were trained using K-Fold cross-validation to ensure robustness and prevent overfitting.

🧠 Feature Importance
Feature importances were computed using model-specific methods:

model.feature_importances_ for LightGBM, XGBoost, and CatBoost

Visualized to understand which sensor readings most affect performance degradation

🏆 Results
The best model achieved a final score of 89.86

Ranked in the Top 100 out of 8000 submissions

The ensemble of LightGBM and CatBoost models contributed most to the final solution

🚀 Conclusion
This project demonstrated how combining powerful models like LightGBM and CatBoost with thorough preprocessing and hyperparameter tuning using Optuna can deliver high-accuracy predictive systems. With a rank in the top 1.25% of all teams, this solution serves as a strong baseline for solar panel maintenance prediction systems.


