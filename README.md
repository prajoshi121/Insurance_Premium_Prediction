# Insurance Premium Prediction Project

## Project Overview
This project focuses on predicting **annual insurance premium amounts** based on customer demographic, medical, and financial data. The dataset includes the following columns:  

`Age`, `Gender`, `Region`, `Marital_status`, `Number Of Dependants`, `BMI_Category`, `Smoking_Status`, `Employment_Status`, `Income_Level`, `Income_Lakhs`, `Medical History`, `Insurance_Plan`, `Annual_Premium_Amount`.  

Our goal was to build an accurate predictive model while handling outliers, feature engineering, and potential model segmentation based on age.

---

## Data Analysis & Visualization
- **Outlier Detection:** Used **boxplots** on numeric features (`Age`, `Number Of Dependants`, `Income_Lakhs`) to detect and remove outliers.  
- **Scatter Plots:** Analyzed relationships between numeric features and `Annual_Premium_Amount`.  
- **Categorical Analysis:** Created **percentage plots** and **heatmaps** to examine distributions and relationships between categorical features.  
- **Correlation Analysis:** Generated a **correlation matrix heatmap** to study interdependencies between features.

---

## Feature Engineering
- **Medical Risk Scoring:** Split `Medical History` into `disease1` and `disease2` columns, assigned risk scores for each disease, and calculated a **normalized total risk score**.  
- **Encoding Categorical Variables:** Converted nominal columns (`Gender`, `Region`, `Marital_status`, `BMI_Category`, `Smoking_Status`, `Employment_Status`) into **dummy variables**.  
- **Scaling:** Applied **MinMaxScaler** on selected numeric features and ordinal variables (`Age`, `Number Of Dependants`, `Income_Level`, `Income_Lakhs`, `Insurance_Plan`).  

---

## Modeling Approach
During **error analysis**, we observed that errors were higher for the **age group 25 and below**, whereas predictions for ages above 25 were more accurate. To improve overall performance, we adopted **model segmentation**:

### Age > 25
- **Model:** XGB Regressor with **RandomizedSearchCV** for hyperparameter tuning.  
- **Best Score:** 0.997  
- **Error Percentage:** 0.50%  

### Age ≤ 25
- **Model:** Linear Regression  
- **Train Score:** 0.99  
- **Test Score:** 0.99  
- **Error Percentage:** 2.04%  

By splitting the data into these segments and training separate models, we were able to reduce prediction errors significantly for the younger age group.

---

## Key Takeaways
- Model segmentation based on age improved prediction accuracy.  
- XGB Regressor is highly effective for the age group above 25.  
- Linear Regression is sufficient for younger clients with slightly higher error tolerance.  
- Feature engineering, including risk scoring and categorical encoding, played a crucial role in improving model performance.
