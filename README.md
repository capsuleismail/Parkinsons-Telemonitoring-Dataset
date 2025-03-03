# Parkinsons Telemonitoring Dataset

## Introduction  
--------------------------------------------------------------------------------------------------------------------
The Parkinson’s Telemonitoring Dataset from the UCI Machine Learning Repository is a dataset used to predict Parkinson’s disease severity based on biomedical voice measurements. The data was collected as part of a telemonitoring project for patients with Parkinson’s disease.
## Dataset Overview
--------------------------------------------------------------------------------------------------------------------
The dataset contains 5,875 voice recordings from 42 Parkinson's disease patients.
Each instance (row) in the dataset represents a voice recording taken from a patient at a specific time.
The dataset includes 16 biomedical voice measures derived from speech signals.
Two target variables indicate Parkinson’s severity:
Motor UPDRS. (Unified Parkinson’s Disease Rating Scale)
Total UPDRS.

These are the questions I've gone through on my notebooks:

1. **Target Overview.** <br/>
2. **How do Shimmer(dB)' and 'Jitter(%)' values behave on time.** <br/>
3. **Can we detect trends in voice measurements over time for individual patients?** <br/>
4. **KDE plot for all Float Columns based on Sex.** <br/>
5. **Heatmap on Target.** <br/>
6. **total_UPDRS distribution analysis.** <br/>
7. **motor_UPDRS distribution analysis.** <br/>
8. **Histogram on Age based on Sex.** <br/>
9. **Can PCA (Principal Component Analysis) reduce the dimensionality while retaining key variance?** <br/>
10. **Modeling with XGBoost and Hyperparameter tuning with Optuna.** <br/>

**Citation: [Parkinsons Telemonitoring](https://archive.ics.uci.edu/dataset/189/parkinsons+telemonitoring). (2009). UCI Machine Learning Repository.** <br/>
--------------------------------------------------------------------------------------------------------------------


### I. How to import the dataset via pip.
--------------------------------------------------------------------------------------------------------------------
```
!pip install ucimlrepo
Import the dataset into your code 
from ucimlrepo import fetch_ucirepo 
  
# fetch dataset 
parkinsons_telemonitoring = fetch_ucirepo(id=189) 
  
# data (as pandas dataframes) 
X = parkinsons_telemonitoring.data.features 
y = parkinsons_telemonitoring.data.targets
  
  
# metadata 
print(parkinsons_telemonitoring.metadata) 
  
# variable information 
print(parkinsons_telemonitoring.variables)

```
--------------------------------------------------------------------------------------------------------------------
## **Here’s a short description of each XGBoost parameter used in this notebook:** 
--------------------------------------------------------------------------------------------------------------------

1. **n_estimators – Number of boosting rounds (trees). More trees can improve learning but may lead to overfitting.** <br/>
2. **learning_rate – Shrinks the impact of each tree to make learning more gradual. Lower values require more trees.** <br/>
3. **max_depth – Maximum depth of each tree. Deeper trees capture more complexity but increase overfitting risk.** <br/>
4. **subsample – Fraction of training data used per boosting round. Helps prevent overfitting (e.g., 0.8 means 80% of data is used).** <br/>
5. **colsample_bytree – Fraction of features randomly chosen per tree. Controls feature randomness (e.g., 0.8 means 80% of features are used).** <br/>
6. **reg_lambda – L2 regularization (Ridge). Helps control model complexity and reduce overfitting.** <br/>
7. **reg_alpha – L1 regularization (Lasso). Encourages sparsity in weights, reducing complexity.** <br/>

## **Best parameters after tuning are:**
--------------------------------------------------------------------------------------------------------------------

1. **n_estimators**: 686 <br/> 
2. **learning_rate**: 0.020807222486212525 <br/> 
3. **max_depth**: 9 <br/> 
4. **subsample**: 0.974896275773738 <br/> 
5. **colsample_bytree**: 0.9649378569877631 <br/>  
6. **reg_lambda**: 1.4795813312782924 <br/>  
7. **reg_alpha**: 2.494078954328818
