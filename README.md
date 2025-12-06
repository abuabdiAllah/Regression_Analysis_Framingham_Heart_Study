# Regression Analysis on the Framingham Heart Study  
**A Jupyter Notebook–based Statistical Exploration of Cardiovascular Risk Factors**

## Overview  
This project explores a subset of data from the **Framingham Heart Study**, a landmark cardiovascular study that began in 1948. The original study followed 5,209 men and women aged 30–62 from Framingham, Massachusetts, collecting detailed health, lifestyle, and physiological measurements every two years. The overarching goal of the study has always been to identify the common factors and characteristics that contribute to cardiovascular disease (CVD).

In this project, I perform regression analysis using Python to understand how different physiological variables relate to one another—especially those connected to cardiovascular risk, such as blood pressure, weight, cholesterol, and smoking habits.

All work for this project is performed inside a Jupyter Notebook, using Python's scientific computing stack. I completed this project as the final project for the Data Science with Python Course at the University of Helsinki

---

## Project Structure  
```
Regression_Analysis_Framingham_Heart_Study/
│
├── src/
│   └── fram.txt                    # Tab-delimited dataset (subset of Framingham Heart Study)
│
├── notebooks/
│   └── regression_analysis.ipynb   # Main Jupyter Notebook with all analysis
│
└── README.md
```

---

## Technologies & Libraries Used  
This analysis is carried out entirely in a **Jupyter Notebook**, using the following Python libraries:

- **NumPy** – numerical computing  
- **Pandas** – data manipulation and cleaning  
- **Matplotlib** – data visualization  
- **Statsmodels** – statistical modeling & linear regression  
- **Statsmodels Regression Plots** – visual diagnostics  
- **Python Functions** – custom preprocessing and normalization  

---

## What This Project Does  

### **1. Data Loading & Inspection**  
The dataset `fram.txt` is loaded using Pandas, and descriptive statistics are examined using:  
```python
fram.describe()
```

### **2. Feature Scaling (Standardization)**  
A custom function `rescale()` is created to normalize continuous variables by centering them and dividing by 2σ (a common scaling technique for regression).  
Example:
```python
fram["sAGE"] = rescale(fram.AGE)
fram["sFRW"] = rescale(fram.FRW)
```

### **3. Building Regression Models**  
A multiple linear regression model is created using `statsmodels`, predicting systolic blood pressure (SBP) using:
- Weight (FRW)
- Gender (SEX)
- Cholesterol (CHOL)

The model is fitted using:
```python
fit = smf.ols("SBP ~ FRW + SEX + CHOL", data=fram).fit()
```

### **4. Data Exploration & Interpretation**  
Using regression outputs and diagnostic plots, the notebook investigates relationships between key risk factors and blood pressure.

---

## Dataset Description  
The dataset includes variables such as:

| Variable | Description |
|----------|-------------|
| AGE | Participant age |
| FRW | Body weight |
| SBP/DBP | Systolic/Diastolic blood pressure |
| CHOL | Cholesterol level |
| CIG | Cigarettes smoked per day |
| CHD | Coronary heart disease indicator |
| DEATH | Death indicator |
| YRS_DTH | Years until death |
| SEX | Gender |

This is a simplified subset derived from the original Framingham Heart Study dataset.

---

## Purpose of the Analysis  
The goal is to develop a deeper understanding of:
- How physiological variables relate to each other
- Which factors may explain variations in blood pressure
- How preprocessing (like scaling) affects statistical modeling
- How classical linear regression can be applied to real epidemiological data

This project serves as both an educational exercise in regression modeling and a practical application of Python's statistical tools.

---

## Notes  
- The analysis must be viewed through the Jupyter Notebook, as the project is built entirely within it.
- The dataset is pre-cleaned, but some variables contain missing values (e.g., SBP10), which should be considered when performing additional analysis.

---

## Acknowledgment  
This project is inspired by the original Framingham Heart Study, one of the most influential epidemiological studies in medical history.
