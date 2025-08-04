# Complete Customer Analytics with Online Retail II Dataset

## Project Summary

This project utilizes modern data science techniques to perform customer analytics, segmentation, churn prediction, customer lifetime value (CLV) analysis, and A/B testing on the Online Retail II dataset. All analyses are conducted in a Jupyter Notebook environment with a focus on visualization and modeling.

## Project Objectives

The main objectives of this project are:

* Which are the most valuable customer segments and what are their common characteristics?
* Which customers are at high risk of churn, and what factors influence this risk?
* What is the estimated future value (CLV) of customers, and which segments should the marketing budget focus on?
* Is a particular marketing campaign (e.g., discount) effective in increasing customer spending?

## Folder and File Structure

* `data/`

  * `online_retail_II.csv`: Raw dataset
  * `cleaned_online_retail_II.csv`: Cleaned dataset
  * `rfm_analysis.csv`: RFM scores and segments
* `01_Data_Preprocessing_EDA.ipynb`: Data preprocessing and exploratory data analysis
* `02_RFM_and_Segmentation.ipynb`: RFM analysis and customer segmentation
* `03_Churn_Prediction.ipynb`: Churn prediction modeling
* `04_CLV_Analysis.ipynb`: Customer lifetime value (CLV) analysis
* `05_AB_Testing.ipynb`: A/B testing and result analysis
* `pyproject.toml`, `uv.lock`: Project dependencies and environment management

## Data Dictionary

The following fields summarize the columns and their meanings in the Online Retail II dataset:

* `Invoice`: Invoice number (nominal). A unique 6-digit identifier for each transaction. If it starts with `C`, it indicates a cancellation invoice.
* `StockCode`: Product (item) code (nominal). A unique code assigned to each product.
* `Description`: Product name/description (nominal).
* `Quantity`: Number of items sold per transaction (numeric, int64).
* `InvoiceDate`: Date and time of the invoice (datetime).
* `Price`: Unit price (numeric, float64). Price per unit, in £ (GBP).
* `Customer ID`: Customer number (nominal). A unique 5-digit code assigned to each customer.
* `Country`: Country name of the customer (nominal).

## Libraries Used

* Python 3.12+
* pandas, numpy
* matplotlib, seaborn
* scikit-learn
* xgboost
* lifetimes
* scipy

## Workflow

1. **Data Cleaning and EDA**: Cleaning of missing/erroneous records, detection of outliers (IsolationForest), basic statistics and visualizations.
2. **RFM Analysis & Segmentation**: Segmenting customers based on Recency, Frequency, Monetary scores and visualizing the results.
3. **Churn Prediction**: Modeling and evaluating customer churn risk using machine learning models (XGBoost, scikit-learn models).
4. **CLV Analysis**: CLV prediction using BetaGeoFitter, GammaGammaFitter, XGBoost; reporting and visualization of segment-based outputs.
5. **A/B Testing**: Statistical tests (Shapiro, Mann-Whitney U) on segment-based groups and visualization of results.

## Table of Contents

* [Project Summary](#project-summary)
* [Project Objectives](#project-objectives)
* [Folder and File Structure](#folder-and-file-structure)
* [Data Dictionary](#data-dictionary)
* [Libraries Used](#libraries-used)
* [Workflow](#workflow)
* [Notebook Summaries](#notebook-summaries)
* [Setup and Execution](#setup-and-execution)

## Notebook Summaries

1. **Data Preprocessing & EDA** (`01_Data_Preprocessing_EDA.ipynb`)

   * Loading and summarizing the raw dataset (`pandas`)
   * Checking for and cleaning missing/duplicate records
   * Type conversions and calculation of `TotalPrice = Quantity * Price`
   * Outlier detection with IsolationForest (`scikit-learn`)
   * Time series analyses: daily, monthly, hourly trends
   * Sales analysis by country and product with interactive visualizations (`plotly`)

2. **RFM Analysis & Segmentation** (`02_RFM_and_Segmentation.ipynb`)

   * Calculation of Recency, Frequency, Monetary scores
   * Creation and naming of customer segments
   * KPI comparisons and distribution plots per segment (`seaborn`, `matplotlib`)
   * Geographic visualization of segments on maps

3. **Churn Prediction** (`03_Churn_Prediction.ipynb`)

   * Feature engineering: RFM, time-based and demographic features
   * Train/validation split, scaling, and handling imbalanced data (`SMOTE`)
   * Models: Comparison of XGBoost, RandomForest, Logistic Regression
   * Evaluation metrics: ROC-AUC, F1, Precision-Recall curves
   * Visualization of feature importance

4. **CLV Analysis** (`04_CLV_Analysis.ipynb`)

   * Purchase frequency prediction using BG/NBD model (`lifetimes`)
   * Monetary value estimation with Gamma-Gamma model
   * Hybrid XGBoost Model: Enhanced prediction using BG/NBD features
   * 6-month CLV projections and total CLV per segment
   * Comparison of CLV results with RFM segments
   * Visualization of CLV distribution and key customer groups

5. **A/B Testing** (`05_AB_Testing.ipynb`)

   * Selection of target segments and random assignment
   * Normality tests (Shapiro-Wilk), variance homogeneity checks
   * Non-parametric tests (Mann-Whitney U) for analysis
   * Detailed visualization and statistical reporting of results

## Setup and Execution

### Environment Setup (Windows PowerShell)

1. Python 3.12+ must be installed.
2. (Optional) Create and activate a virtual environment:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```
3. Install dependencies via `pyproject.toml` (choose one of the following methods):

   * Using pip:

     ```powershell
     pip install -U pip
     pip install -e .
     ```
   * Using uv:

     ```powershell
     pip install -U uv  # if uv is not already installed
     uv pip install -e .
     ```
