# 🌍 Global Food Watch: AI Early Warning System

## 🚀 Project Overview
This project implements a **Hybrid Early Warning System** designed to predict food price shocks and potential famine risks across global markets. It transitions from a baseline Logistic Regression to a sophisticated **XGBoost-based Watchdog** model, calibrated using **Quantile Regression**.

## 🛠️ Technical Stack & Methods
* **Machine Learning**: XGBoost, Quantile Regression (Pinball Loss), Logistic Regression.
* **Optimization**: Hyperparameter tuning via **Optuna** (TPESampler & HyperbandPruner).
* **Feature Engineering**: 
    * Temporal dynamics: Rolling Z-scores (12/24m), Volatility (3/12m), Price Velocity, and Acceleration.
    * Memory: Automated generation of T-1 to T-3 lags for 15+ features.
    * Spatial: Market clustering (K-Means) to identify historical risk profiles.
* **Explainability**: SHAP (TreeExplainer) for local and global model transparency.
* **Deployment**: Interactive **Streamlit Dashboard** with real-time crisis simulation.

## 📈 Key Innovation: The V8 Hybrid Logic
The system doesn't just predict "Crisis/No Crisis". It uses a dual-scale calibration:
1.  **Relative Scale**: Position of the current shock compared to its own training history (ECDF).
2.  **Absolute Scale**: Comparison with global historical severity.
3.  **Result**: A 5-level alert system (from *Normal* to *Force Majeure*) that handles extreme market "tipping points".

## 📊 Results Summary
* **Detection Rate (Recall)**: Optimized for F2-Score to minimize false negatives (missed crises).
* **Interpretability**: Top drivers identified include price acceleration and volatility ratios, validated by SHAP dependence plots.
