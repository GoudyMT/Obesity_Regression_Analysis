# Predicting Weight with Linear Regression: A Scikit-learn Project

## Overview

This project demonstrates the application of simple and multiple linear regression to predict **Weight** using the Obesity dataset, showcasing regression analysis skills with **Scikit-learn**. The goal is to build, evaluate, and refine regression models while addressing challenges like multicollinearity and outliers. The project is presented as a Jupyter notebook (`Obesity_Regression_Analysis.ipynb`), with an HTML export (`Obesity_Regression_Analysis.html`) for easy viewing, making it an ideal addition to a machine learning portfolio.

## Objectives

- Build and compare simple and multiple linear regression models to predict **Weight**.
- Evaluate model performance using metrics like **Mean Squared Error (MSE)** and **R-squared**.
- Check regression assumptions (e.g., linearity, multicollinearity).
- Address challenges such as outliers and multicollinearity to improve model stability and performance.
- Document the process thoroughly for clarity and reproducibility.

## Dataset

The dataset used is `ObesityDataSet_raw_and_data_sinthetic.csv`, which contains **2111 entries** and **17 columns** related to lifestyle and demographic factors. Key features include:

### Numerical Features
- **Height** (meters)
- **Age** (years)
- **Weight** (kg, target variable)
- **FCVC** (frequency of vegetable consumption)
- **FAF** (physical activity frequency)
- **CH2O** (water consumption)

### Categorical Features
- **Gender** (encoded as **Gender_Male**: 1 for Male, 0 for Female)
- Others (e.g., **CALC**, **MTRANS**, not used in the final model)

The dataset has **no missing values**, but some outliers in **Weight** were identified and analyzed.

## Project Structure

The project is organized in a Jupyter notebook (`Obesity_Regression_Analysis.ipynb`) with the following sections:

### Data Loading and Exploration
- Loaded the dataset using **Pandas**.
- Inspected data types, summary statistics, and visualized relationships (e.g., **Height** vs. **Weight** scatter plot).

### Simple Linear Regression
- Built a model using **Height** to predict **Weight**.
- Evaluated with **MSE** and **R-squared**.

### Multiple Linear Regression
- Expanded the model with additional features (**Age**, **Gender_Male**, **FCVC**, **FAF**, **CH2O**).
- Evaluated performance and compared to the simple model.

### Addressing Non-Linearity
- Added a polynomial term (**Height^2**) to capture potential non-linear relationships.
- Assessed impact on model performance.

### Handling Outliers
- Identified outliers in **Weight** using the **Interquartile Range (IQR)** method.
- Removed outliers and re-evaluated the model.

### Addressing Multicollinearity
- Calculated **Variance Inflation Factor (VIF)** to detect multicollinearity.
- Iteratively removed features (**Gender_Male**, **FCVC**, **CH2O**) to reduce VIF.
- Debugged issues (e.g., **TypeError** in VIF calculation due to bool type).

### Conclusion
- Summarized findings, selected the final model, and suggested next steps.

## Key Findings

### Model Performance

#### Simple Linear Regression (using **Height**)
- **MSE**: 553.02 (**RMSE** ≈ 23.52 kg)
- **R-squared**: 0.22
- **Finding**: **Height** alone explained only **22%** of the variance in **Weight**, indicating the need for additional predictors.

#### Multiple Linear Regression (Expanded Features)
- **Features**: **Height**, **Age**, **Gender_Male**, **FCVC**, **FAF**, **CH2O**
- **MSE**: 439.72 (**RMSE** ≈ 20.97 kg)
- **R-squared**: 0.38
- **Finding**: Best predictive performance, explaining **38%** of the variance, but high multicollinearity detected (**VIF** up to 54.04 for **Height**).

#### Polynomial Model
- Added **Height^2** to the Expanded Features model.
- **MSE**: 440.46 | **R-squared**: 0.38
- **Finding**: No significant improvement, suggesting the relationship is mostly linear.

#### Outlier Removal
- Removed outliers in **Weight** using IQR (exact dataset sizes not specified, estimated ~5-10 rows removed from 2111).
- **MSE**: 462.84 | **R-squared**: 0.34
- **Finding**: Performance worsened, indicating outliers contained useful information.

#### Final Model (Reduced Multicollinearity)
- **Features**: **Height**, **Age**, **FAF**
- **MSE**: 495.03 (**RMSE** ≈ 22.25 kg)
- **R-squared**: 0.30
- **VIF** reduced (e.g., **Height VIF** from 54.04 to 18.73), but performance dropped.

### Final Model Selection

- **Chosen Model**: Expanded Features model (**Height**, **Age**, **Gender_Male**, **FCVC**, **FAF**, **CH2O**)
  - **MSE**: 439.72 (**RMSE** ≈ 20.97 kg)
  - **R-squared**: 0.38
- **Reason**: Best predictive performance, explaining **38%** of the variance in **Weight**.
- **Caveat**: High multicollinearity (**VIF** up to 54.04), which may affect coefficient stability. Steps were taken to address this, but the trade-off favored performance over stability for this demonstration.

### Assumption Checks

- **Linearity**: Scatter plots (e.g., **Height** vs. **Weight**) showed a roughly linear relationship, confirmed by the lack of improvement with polynomial terms.
- **Multicollinearity**: High **VIF** values were identified and addressed, though some persisted in the final model.
- **Residuals**: Not explicitly checked, but recommended for future analysis (e.g., plotting residuals vs. predicted values).

## Installation and Usage

To run this project locally:

### Prerequisites
- **Python** 3.6+
- **Jupyter Notebook**
- Required libraries: **pandas**, **numpy**, **scikit-learn**, **matplotlib**, **seaborn**, **statsmodels**

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/Regression-Analysis-with-Scikit-Learn.git
   cd Regression-Analysis-with-Scikit-Learn

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate

3. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn statsmodels jupyter

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook

5. Open `Obesity_Regression_Analysis.ipynb` and run all cells.

## View HTML Export

Alternatively, view the static HTML version (`Obesity_Regression_Analysis.html`) directly in your browser for a quick overview of the project.

## Future Improvements

- **Feature Engineering**: Explore additional features (e.g., interaction terms, other lifestyle factors like **CALC** or **MTRANS**).
- **Residual Analysis**: Plot residuals to check for normality, homoscedasticity, and independence.
- **Alternative Models**: Try regularized models like **Ridge** or **Lasso** regression to handle multicollinearity without removing features.
- **Outlier Handling**: Revisit outliers using robust methods (e.g., winsorizing) instead of removal.


## Acknowledgments

- **Dataset**: `ObesityDataSet_raw_and_data_sinthetic.csv` (https://archive.ics.uci.edu/dataset/544/estimation+of+obesity+levels+based+on+eating+habits+and+physical+condition Fabio Mendoza Palechor, Alexis De la Hoz Manotas. 2019).
- **Tools**: **Scikit-learn**, **Pandas**, **Matplotlib**, **Seaborn**, **Statsmodels**, **Jupyter Notebook**.

**Created on**: May 18, 2025  
**Author**: Max Goudy 

Feel free to reach out for questions or collaboration opportunities!
   
