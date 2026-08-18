# 🚚 Olist E-Commerce Late Delivery Prediction & Pipeline

A machine learning and data engineering project designed to predict e-commerce order shipping delays on the Olist Brazilian E-Commerce Dataset. This project handles relational database consolidation, feature engineering, and binary classification modeling to uncover key logistics bottlenecks.

---

## 📌 Project Architecture & Repository Structure

README.md                          # Project documentation
olist_late_delivery_dataset.csv    # Consolidated dataset generated from raw Olist tables
Tables_matching.ipynb              # SQL-based data aggregation & feature engineering notebook
Model.ipynb                        # EDA, model training, hyperparameter tuning & evaluation notebook

---

## 🎯 Objectives & Business Value

* Identify Logistics Bottlenecks: Pinpoint critical geographical, temporal, and product factors driving shipping delays.
* Predict High-Risk Deliveries: Build and fine-tune machine learning models to detect potentially late orders prior to fulfillment.
* Handle Real-World Data Challenges: Address class imbalance (is_late distribution) and process multi-table relational schema using embedded SQL queries.

---

## 🛠️ Data Pipeline & Methodology

### 1. Data Merging & SQL Matching (Tables_matching.ipynb)
* Relational Aggregation: Executed in-memory SQL queries via DuckDB to join multi-relational datasets (customers, orders, order_items, products, sellers, payments, reviews).
* Feature Creation: Created specialized variables including freight_ratio, combined product_volume_cm3, and delivery lag metrics.
* Output: Exported the unified, cleaned dataset as olist_late_delivery_dataset.csv.

### 2. Exploratory Data Analysis & Preprocessing (Model.ipynb)
* Class Imbalance: Analyzed target variable imbalance (is_late) to prevent model bias toward standard on-time orders.
* Regional & Category Patterns: Identified delay variance across customer/seller states (e.g., SP, RJ, MG) and specific product categories.
* Preprocessing Pipeline: Implemented scikit-learn ColumnTransformer with OneHotEncoder for high-cardinality categorical variables and feature scaling for numerical columns.

### 3. Model Training & Evaluation (Model.ipynb)
* Algorithms Evaluated:
  - Logistic Regression (Baseline model using class_weight='balanced')
  - Random Forest Classifier
  - XGBoost Classifier (Leveraging scale_pos_weight for imbalanced learning)
* Optimization: Fine-tuned hyperparameters via GridSearchCV and evaluated threshold adjustments using Precision-Recall Curves and Confusion Matrices.

---

## 🔬 Key Results & Insights

* Primary Delay Predictors: Customer geographic location (customer_state), purchasing month, and seller state are among the strongest indicators of shipping delays.
* Model Choice: Tree-based models (Random Forest and XGBoost) demonstrated superior performance in capturing complex non-linear feature interactions compared to linear baselines.

---

## 🧰 Tech Stack

* Language: Python
* Data Processing & SQL: Pandas, DuckDB
* Data Visualization: Matplotlib, Seaborn
* Machine Learning: Scikit-Learn, XGBoost
* Environment: Google Colab / Jupyter Notebook

---

## 🚀 How to Reproduce

1. Clone the repository:
   git clone https://github.com/m1deey/Late_delivery-.git
   cd Late_delivery-

2. Install required dependencies:
   pip install pandas numpy scikit-learn xgboost matplotlib seaborn duckdb jupyter

3. Run the Notebooks:
   * Run Tables_matching.ipynb to inspect data extraction, relational SQL joins, and CSV generation.
   * Run Model.ipynb to execute EDA, model pipeline training, hyperparameter grid searches, and visual evaluations.
