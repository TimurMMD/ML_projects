# 🌞 Zelestra Hackathon - Predictive Maintenance for Solar Panels

This project was developed as part of the **Zelestra Hackathon**, where the primary goal was to build a machine learning model that predicts **performance degradation and potential failures** in solar panels using historical and real-time sensor data. The aim: enable predictive maintenance for solar infrastructure, reduce downtime, and optimize energy output.

---

## 🔍 Problem Statement

As solar energy becomes a cornerstone of sustainable infrastructure, **ensuring operational efficiency and reliability** is more critical than ever. Traditional maintenance is reactive, leading to unnecessary costs and failures. This hackathon challenged participants to build a **proactive, intelligent system** for predictive maintenance of solar systems.

---

## 🧠 Machine Learning Strategy

Our pipeline consists of several key stages:

---

### 📊 1. Data Loading & Exploration

- Loaded `train.csv` and `test.csv` from Google Drive.
- Inspected data using `.info()`, `.describe()`, `.head()`.
- Identified feature types and anomalies for further cleaning.

---

### 🧼 2. Preprocessing

- Dropped constant or redundant features.
- Removed columns with boolean types.
- Imputed missing values.
- Standardized numerical features using `StandardScaler`.
- Engineered features with domain knowledge to enhance signal.

---

### 🔧 3. Model Development & Optimization

We implemented several models, each tuned using **Optuna**, a powerful hyperparameter optimization framework.

#### ✅ XGBoost
- Parameters tuned:  
  `n_estimators`, `max_depth`, `learning_rate`, `subsample`, `colsample_bytree`, `reg_alpha`, `reg_lambda`
- Evaluation metric: `custom_score`

#### 🐱 CatBoost
- Parameters:  
  `iterations`, `depth`, `learning_rate`, `l2_leaf_reg`, `bagging_temperature`, `random_strength`, `border_count`
- Employed **K-Fold Cross-Validation**
- Scaled data after early experimentation

#### 🌲 RandomForest
- Used as a simple yet powerful ensemble baseline

#### 💡 LightGBM
- Implemented with `early_stopping` to prevent overfitting
- Tuned:
  - `learning_rate`, `num_leaves`, `max_depth`, `min_data_in_leaf`
  - `feature_fraction`, `bagging_fraction`, `bagging_freq`
  - `lambda_l1`, `lambda_l2`
- Final model retrained to extract **feature importance**

#### 🔥 TabNet
- Used for deep tabular learning with built-in attention
- Trained with **Optuna-tuned parameters**

---

### 📈 Evaluation Strategy

- Custom metric based on **Root Mean Squared Error (RMSE)** and output scaling
- Employed **3-fold cross-validation** to assess generalization

---

### 🧠 Feature Importance Analysis

- Used `.feature_importances_` attribute from:
  - **LightGBM**, **XGBoost**, **CatBoost**
- Visualizations revealed key sensor variables driving model performance

---

## 🏆 Final Results

- **Final Score**: `89.86`
- **Leaderboard Rank**: 🥇 **Top 100 out of 8000+ submissions**
- Winning strategy: **Ensemble of LightGBM and CatBoost**

---

## 🚀 Conclusion

This project highlights how **thoughtful preprocessing**, **feature engineering**, and **advanced model tuning** can produce top-tier predictive performance. The final solution is ranked in the **top 1.25% globally**, demonstrating the effectiveness of combining **gradient boosting models with optimization and validation rigor**.

---

🔗 *Thank you for checking out this project! For more details, refer to the notebook or contact the contributor.*



