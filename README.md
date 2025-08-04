# Complete Customer Analytics with Online Retail II Dataset

![Project Banner](images/3d_rfm_analysis.png)

## 📝 Project Summary

This project utilizes modern data science techniques to perform customer analytics, segmentation, churn prediction, customer lifetime value (CLV) analysis, and A/B testing on the Online Retail II dataset. The entire workflow is designed to transform raw transactional data into actionable business insights.

## 🎯 Project Objectives

The main objectives of this project are:

* Identify the most valuable customer segments and their common characteristics.
* Pinpoint customers at high risk of churn and understand the factors influencing this risk.
* Estimate the future value (CLV) of customers to guide marketing budget allocation.
* Determine the effectiveness of a marketing campaign (e.g., a discount) on increasing customer spending.


## 🛠️ Tech Stack

<p align="left">
    <a href="https://www.python.org" target="_blank"> <img src="https://img.shields.io/badge/Python-3.12%2B-blue?style=for-the-badge&logo=python" alt="python"/> </a>
    <a href="https://pandas.pydata.org/" target="_blank"> <img src="https://img.shields.io/badge/Pandas-2.3%2B-blue?style=for-the-badge&logo=pandas" alt="pandas"/> </a>
    <a href="https://numpy.org/" target="_blank"> <img src="https://img.shields.io/badge/Numpy-1.26%2B-blue?style=for-the-badge&logo=numpy" alt="numpy"/> </a>
    <a href="https://scikit-learn.org/" target="_blank"> <img src="https://img.shields.io/badge/scikit--learn-1.7%2B-orange?style=for-the-badge&logo=scikit-learn" alt="scikit-learn"/> </a>
    <a href="https://xgboost.ai/" target="_blank"> <img src="https://img.shields.io/badge/XGBoost-3.0%2B-orange?style=for-the-badge&logo=xgboost" alt="xgboost"/> </a>
    <a href="https://lifetimes.readthedocs.io/en/latest/" target="_blank"> <img src="https://img.shields.io/badge/Lifetimes-0.11.3-green?style=for-the-badge" alt="lifetimes"/> </a>
    <a href="https://matplotlib.org/" target="_blank"> <img src="https://img.shields.io/badge/Matplotlib-3.10%2B-blueviolet?style=for-the-badge&logo=matplotlib" alt="matplotlib"/> </a>
    <a href="https://seaborn.pydata.org/" target="_blank"> <img src="https://img.shields.io/badge/Seaborn-0.13%2B-blueviolet?style=for-the-badge&logo=seaborn" alt="seaborn"/> </a>
    <a href="https://scipy.org/" target="_blank"> <img src="https://img.shields.io/badge/SciPy-1.16%2B-lightgrey?style=for-the-badge&logo=scipy" alt="scipy"/> </a>
</p>

## 📂 Project Structure

* `data/`: Contains raw, intermediate, and final datasets.
* `images/`: Stores visual assets used in the README.
* `notebooks/`: Houses the Jupyter Notebooks for each analysis stage.

  * `01_Data_Preprocessing_EDA.ipynb`
  * `02_RFM_and_Segmentation.ipynb`
  * `03_Churn_Prediction.ipynb`
  * `04_CLV_Analysis.ipynb`
  * `05_AB_Testing.ipynb`
* `pyproject.toml`, `uv.lock`: Files for modern dependency and environment management.
* `README.md`: This project overview.

## 📊 Data Dictionary

The dataset contains transactional data from a UK-based online retail company. Key fields used in the analysis include:

| Feature       | Description                                                                   | Type         |
| ------------- | ----------------------------------------------------------------------------- | ------------ |
| `Invoice`     | A 6-digit nominal, unique for each transaction. 'C' indicates a cancellation. | `object`     |
| `StockCode`   | A unique code assigned to each distinct product.                              | `object`     |
| `Description` | The name of the product.                                                      | `object`     |
| `Quantity`    | The number of units of a product sold in a transaction.                       | `int64`      |
| `InvoiceDate` | The date and time when the transaction occurred.                              | `datetime64` |
| `Price`       | The unit price of the product in British Pounds (£).                          | `float64`    |
| `Customer ID` | A 5-digit unique identifier for each customer.                                | `float64`    |
| `Country`     | The country where the customer resides.                                       | `object`     |


## 🔄 Workflow & Notebook Summaries

This project follows a sequential workflow, with each step detailed in its respective Jupyter Notebook.

1. **Data Cleaning and EDA** (`notebooks/01_Data_Preprocessing_EDA.ipynb`)

   * Cleans and preprocesses over 1 million records, handling missing values, duplicates, and cancellations.
   * Performs feature engineering.
   * Applies `IsolationForest` for sophisticated outlier detection.
   * Conducts comprehensive exploratory data analysis (EDA) to uncover trends in sales over time, by country, and by product.

2. **RFM Analysis & Segmentation** (`notebooks/02_RFM_and_Segmentation.ipynb`)

   * Calculates Recency, Frequency, and Monetary (RFM) metrics for each customer.
   * Segments customers into actionable groups like "Best Customers," "At-Risk," and "Promising Customers."
   * Visualizes segment distributions and characteristics using 2D and 3D plots.

3. **Churn Prediction** (`notebooks/03_Churn_Prediction.ipynb`)

   * Defines churn based on a 90-day inactivity window.
   * Builds and compares `Logistic Regression`, `Random Forest`, and `XGBoost` models.
   * Evaluates models using ROC-AUC, F1-score, and confusion matrices to identify the best-performing algorithm.
   * Visualizes feature importance to understand key drivers of customer churn.

4. **CLV Analysis** (`notebooks/04_CLV_Analysis.ipynb`)

   * Implements the probabilistic **BG/NBD** model to predict future transaction frequency.
   * Uses the **Gamma-Gamma** model to estimate the average monetary value of transactions.
   * Hybrid XGBoost model using **BG/NBD** features.
   * Comparison of CLV results with RFM segments.
   * Visualization of CLV distribution and key customer groups.

5. **A/B Testing** (`notebooks/05_AB_Testing.ipynb`)

   * Simulates an A/B test scenario to measure the impact of a discount campaign.
   * Applies appropriate statistical tests (**Shapiro-Wilk** for normality, **Mann-Whitney U** for comparison) to determine statistical significance.
   * Provides clear visualizations and reporting of the test results.

## 🚀 Setup and Execution

### Environment Setup (Windows PowerShell)

1. Ensure **Python 3.12+** is installed.
2. Clone the repository:

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```
3. (Recommended) Create and activate a virtual environment:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```
4. Install the required dependencies using a modern package manager. `uv` is recommended for its speed.

   * **Using uv (Recommended):**

     ```powershell
     pip install -U uv  # Install uv if you haven't already
     uv pip install -e .
     ```
   * **Using pip:**

     ```powershell
     pip install -U pip
     pip install -e .
     ```
5. Launch Jupyter Notebook or JupyterLab and navigate to the `notebooks/` directory to explore the analyses.

   ```bash
   jupyter notebook
   ```

## 📬 Contact

Mert Afacan – [https://www.linkedin.com/in/mert-afacan/](https://www.linkedin.com/in/mert-afacan/) – [mert0afacan@gmail.com](mailto:mert0afacan@gmail.com)