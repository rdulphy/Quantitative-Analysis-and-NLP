# Quantitative Economics & NLP Research Repository

This repository contains independent research projects applying machine learning to econometric data and computational linguistics.

---

## 1. Food Price Shock Detection System

### Project Overview
An econometric pipeline designed to identify and categorize food price anomalies using a hybrid classification-regression approach. The goal is to detect persistent shocks (Z-score >= 2.0 for 3+ months) in international agricultural markets.

### Data & Features
* **Source**: UN World Food Programme (WFP) historical price data.
* **Normalization**: Automated unit conversion (to KG/L) and currency indexing by country-product-year.
* **Feature Engineering**: 
    * Lagged variables (T-1 to T-3) for all price dynamics.
    * Statistical moments: Rolling Z-scores (12m), volatility (3m/12m), price acceleration.
    * Structural: Market clustering via K-Means to account for local risk profiles.

### Model Architecture
* **Classifier**: XGBoost optimized for F2-Score (to prioritize recall on crisis events).
* **Severity Estimator**: Quantile Regression (XGBoost `reg:quantileerror`) at q95 to estimate "Worst Case" future scenarios.
* **Inference**: A 5-level alert logic based on the convergence between probability of shock and predicted quantile severity.

### Key Technical Tools
* **Tuning**: Optuna (Hyperband Pruning).
* **Interpretability**: SHAP Values (Global/Local importance).
* **Interface**: Streamlit dashboard for historical backtesting and scenario simulation.

---

## 2. NLP: Social Graphs & Semantic Pruning in Balzac

### Project Overview
A structural analysis of Honoré de Balzac's "La Comédie Humaine" using Natural Language Processing to map character networks and quantify stylistic density.

### Core Mechanics
* **Social Graph**: Named Entity Recognition (NER) via `spaCy` to map co-occurrences and extract network centrality (NetworkX) of characters across 4 volumes.
* **Semantic Compression**: Automated dependency parsing to isolate core S-V-O structures, aggressively pruning non-essential modifiers.
* **Metrics**: Achieves ~31% text compression while calculating semantic density and Type-Token Ratio (TTR).
