# `Loan-Prediction-Analysis`
**Project Summary**: Loan Amount Prediction for Personalized Offers
**Problem Statement**
Banks need to forecast personalized loan amounts to increase approval rates while minimizing default risk. Traditional rule‑based methods fail to capture individual circumstances.

**Objective**
Build a regression model using applicant features (income, dependents, credit history, employment type, property area) to predict the optimal loan amount for each customer.

**Dataset**
1,000 loan applications, 12 columns (Loan_ID, Gender, Married, Dependents, Education, Employment_Type, ApplicantIncome, LoanAmount, Loan_Amount_Term, Credit_History, Property_Area, Loan_Status)

3.5% missing values in LoanAmount, 2.5% in Credit_History – cleaned with median/mode imputation.

**Methodology**
*Data Cleaning*: Filled numeric missing values with median, categorical with mode; converted Credit_History to binary (0/1).

*Feature Engineering*: Created 9 new features (e.g., Income_per_Dependent, Credit_Income_Score, Monthly_Income, High_Income_Flag).

*Exploratory Data Analysis (EDA)*: 7 visualizations – distributions, scatter plots, box plots, correlation matrix. Found very weak linear correlations (all <0.15).

*Models*: Linear Regression and Random Forest Regressor (100 trees).

*Train/Test Split*: 80% train, 20% test (adjustable).

**Key Results**
Model	Test R²	Test RMSE	Test MAE
Linear Regression	0.001	132,963	113,886
Random Forest	-0.054	136,604	117,831
Random Forest overfits (train R² = 0.841, test negative).

Linear Regression explains virtually no variance (R² ≈ 0).

Feature Importance (Random Forest)
Income_per_Dependent (0.277)
Credit_Income_Score (0.137)
Monthly_Income (0.135)
ApplicantIncome (0.131)

**Business Insights & Recommendations**
Current features have extremely weak linear relationships with loan amount → linear models are unsuitable.

Need richer data (existing debt, monthly expenses, collateral).

Use non‑linear models (XGBoost, neural networks) and hybrid rule‑based caps.

Segment applicants by employment type and property area.

**Conclusion**
While the pipeline successfully cleans, engineers features, and trains two regression models, the predictive performance is poor (R² near zero). The dataset lacks strong signals, and the target variable shows almost no linear correlation with the given attributes. For production use, banks must collect more informative features and adopt advanced non‑linear algorithms.
