# ⚡ Electric Vehicle Population Analytics & CAFV Eligibility Prediction

An end-to-end big data analytics project that analyzes electric vehicle adoption trends, predicts Clean Alternative Fuel Vehicle (CAFV) eligibility, estimates electric range, and forecasts EV demand using PySpark and machine learning.

## 📌 Overview

As electric vehicle adoption accelerates across the United States, manufacturers, policymakers, utilities, and infrastructure planners require data-driven insights to support strategic decisions.

This project leverages the Electric Vehicle Population dataset containing over **269,000 registered EV records** to:

* Analyze EV adoption trends and market dynamics
* Identify factors influencing electric range and CAFV eligibility
* Predict electric range using machine learning
* Classify vehicles based on CAFV eligibility
* Forecast EV demand by ZIP code

## 🎯 Business Objectives

* Understand key drivers of EV performance and adoption
* Predict CAFV eligibility to streamline incentive allocation
* Forecast EV demand to support charging infrastructure planning
* Identify relationships between vehicle price, range, and model characteristics
* Enable manufacturers and policymakers to make data-driven decisions

## 📊 Dataset

**Source:** Electric Vehicle Population Data

**Records:** 269,673 electric vehicles registered across the United States

### Key Features

**Vehicle Information**

* Make
* Model
* Model Year
* Electric Vehicle Type (BEV/PHEV)
* Electric Range
* Base MSRP

**Geographic Information**

* Postal Code
* County
* City
* State
* Census Tract

**Program Information**

* CAFV Eligibility
* Electric Utility Provider

## 🛠️ Technology Stack

* Python
* PySpark
* Spark MLlib
* SQL
* Power BI
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

## 🔄 Data Preparation

* Performed schema validation and data type casting using PySpark
* Imputed missing `Base MSRP` and `Electric Range` values using **median values by Make–Model combinations**
* Imputed categorical variables using mode imputation
* Treated zero-value MSRP and electric range as invalid observations
* Removed vehicles with electric range below 20 miles
* Handled outliers using group-level median imputation
* Encoded categorical variables using `StringIndexer` and `OneHotEncoder`
* Engineered lag features for ZIP code demand forecasting

## 📈 Exploratory Data Analysis

Key findings from the exploratory analysis include:

* EV registrations have increased significantly in recent model years
* BEVs consistently outperform PHEVs in electric range
* Tesla, Nissan, and Chevrolet account for the highest EV registrations
* Electric range and Base MSRP show a moderate positive relationship
* Newer vehicle models generally offer higher electric ranges
* CAFV-eligible vehicles represent the largest share of the dataset
* Strong associations exist between vehicle make and model

## 🤖 Machine Learning Models

### 1. Electric Range Prediction

**Target Variable:** Electric Range

| Model                        | RMSE     | R²        |
| ---------------------------- | -------- | --------- |
| Random Forest Regressor      | **8.08** | **0.993** |
| Gradient Boosted Trees       | 22.33    | 0.944     |
| Linear Regression (Baseline) | 49.23    | 0.727     |

**Key Insight:** Vehicle model is the strongest predictor of electric range.

---

### 2. CAFV Eligibility Classification

**Target Variable:** CAFV Eligibility

Classes:

* Clean Alternative Fuel Vehicle Eligible
* Eligibility Unknown as Battery Range Has Not Been Researched
* Not Eligible Due to Low Battery Range

#### Random Forest Classifier

| Metric    | Score      |
| --------- | ---------- |
| Accuracy  | **99.59%** |
| Precision | **99.59%** |
| Recall    | **99.59%** |
| F1 Score  | **99.59%** |

**Top Features:**

1. Electric Range (43.87%)
2. Model Year (28.04%)
3. Model (14.58%)
4. Vehicle Type (8.45%)
5. Make (5.05%)

#### Logistic Regression (Baseline)

| Metric    | Score  |
| --------- | ------ |
| Accuracy  | 75.38% |
| Precision | 73.31% |
| Recall    | 75.38% |
| F1 Score  | 69.20% |

**Key Insight:** Random Forest significantly outperformed Logistic Regression by capturing non-linear relationships among vehicle characteristics.

---

### 3. EV Demand Forecasting

**Target Variable:** EV registration count by ZIP code

**Features:**

* Model Year
* Lagged EV counts
* Rolling average demand

**Approach:**

* Aggregated registrations by ZIP code and year
* Engineered lag features using window functions
* Built a baseline forecasting model using linear regression

## 💡 Key Insights

* Electric range is the strongest driver of CAFV eligibility.
* Vehicle model is the most important predictor of electric range.
* Demand for higher-range BEVs continues to grow.
* Newer EV models are more likely to qualify for clean-fuel incentives.
* BEV adoption highlights the need for expanded charging infrastructure.
* Higher-priced vehicles generally offer greater electric range.

## 🚀 Business Impact

This project demonstrates how machine learning can support:

* Incentive eligibility automation
* EV product strategy and pricing decisions
* Charging infrastructure planning
* Inventory optimization for dealerships
* Policy design and clean transportation initiatives

## 📂 Repository Structure

```text
├── data/
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_electric_range_prediction.ipynb
│   ├── 04_cafv_eligibility_prediction.ipynb
│   └── 05_ev_demand_forecasting.ipynb
├── dashboards/
├── images/
├── src/
├── requirements.txt
└── README.md
```

## ▶️ Getting Started

```bash
git clone https://github.com/yourusername/ev-analytics.git

cd ev-analytics

pip install -r requirements.txt
```

Run the notebooks in sequence:

1. Data Preparation
2. Exploratory Data Analysis
3. Electric Range Prediction
4. CAFV Eligibility Prediction
5. EV Demand Forecasting

## 🔮 Future Enhancements

* Implement XGBoost for model benchmarking
* Integrate charging station and demographic datasets
* Deploy models using Azure Databricks
* Build interactive Power BI dashboards
* Develop real-time EV demand forecasting pipelines

## 👤 Author

**Sushmitha Manoharan**

Master's in Business Analytics | University of North Texas

LinkedIn: *Add your profile link here*
