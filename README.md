# <center> Predicting Survivability of Coronary Artery Disease (CAD) Patients </center>

![](https://img.shields.io/badge/Status-Completed-green)
![](https://img.shields.io/badge/Domain-Health%20Care-blue)
![](https://img.shields.io/badge/Language-Python-lightgreen)
![](https://img.shields.io/badge/Package-Scikit--Learn-orange)
![](https://img.shields.io/badge/Package-TensorFlow-orange)
![](https://img.shields.io/badge/Package-Numpy-orange)
![](https://img.shields.io/badge/Package-Pandas-orange)

<img src="https://user-images.githubusercontent.com/99384454/188098165-46d0c721-190f-4854-80e4-6d24eb6d700b.png" width="950">

# <center> TABLE OF CONTENTS </center>
  - [Business Objectives](#business-objectives)
  - [Explanatory Data Analysis (EDA)](#explanatory-data-analysis-eda)
  - [Feature Engineering](#feature-engineering)
  - [Model Training and Optimization](#model-training-and-optimization)
  - [Results and Discussion](#results-and-discussion)
<br><br>

# Business Objectives

The objective of this project is to build a model to predict the survival of CAD patients to help doctors formulate pre-emptive medical treatment using Machine Learning based on patient particulars (age, gender) and their medical records (smoking/diabete status

# Pipeline
<img src="https://user-images.githubusercontent.com/99384454/188110550-1c45f258-73e8-4752-8916-b88b37a8d3b9.png" width="900">

<br>

# Explanatory Data Analysis (EDA)

## 1. Target Variable
After label standardization and cleaning, there are **9977** samples with "Not-Survived" labels, **5023** "Survived" labels, approximately a **2/1 Non-Survived/Survived ratio**. <br>

<img src="https://user-images.githubusercontent.com/99384454/188106741-0022e79d-e856-4bde-add1-d07b9e7b5004.png" width="500">

## 2. Continuous Variables
### 2.1. Univariate Distributions
![image](https://user-images.githubusercontent.com/99384454/188107983-9a3d108e-3f7c-4ea7-93a7-b829038bead1.png)<br>
Univariate Analysis of continuous variables show that Creatinine and Creatinine Phosphokinase has high degree of right skewness, which will be handled by log-transformation to generate more normal distributions.

### 2.2. Multivariate Analysis
![image](https://user-images.githubusercontent.com/99384454/188108711-92b93bf3-ec1b-425c-b60f-f2094d9d7683.png) <br>
Multivariate Analysis using Pearson Correlation between continuous variables show that most features have low degree of correlation pairwise. Only Height and Weight have moderate degree of correlation (**0.59**). We hence do not eliminate any features at this stage.

## 3. Categorical Variables
### 3.1. Univariate Distributions
![image](https://user-images.githubusercontent.com/99384454/188109334-9e056f76-aa12-4f60-a0cf-7dd6744d5084.png) <br>
No complete separation / quasi complete separation observed from the 4 categorical variables with respect to the target variable.

### 3.2. Multivariate Analysis
![image](https://user-images.githubusercontent.com/99384454/188109648-e9561b50-d05c-44cc-b898-0feda7075aa1.png) <br>
Multivariate Analysis of association between categorical variables with cramer's V correlation and Chi-Square statistics show no pair with significantly high degree association between any pair of categorical features. The pair with highest degree of association is between *8Smoking Status** and **Gender**. No categorical features are eliminated at this stage.

<br>

# Feature Engineering

## 1. Missing Data Imputation
In this project, we evaluate the performance of several different imputations methods from simple method such as mean imputation to more sophiscated methods such as KNN imputation and RandomForest imputation. <br>

To evaluate the performance of the imputation method, we use 2 different base models: Logistic Regression and Support Vector Classification. We will then test the performance of different methods of imputation on the chosen performance parameter (Accuracy) of the base models and choose the imputation method which gives the highest score. <br>

![Imputation](https://user-images.githubusercontent.com/99384454/188111239-c87cec06-4bb7-4223-8477-32c919c2bf8e.png)

We choose to use MissForest for this project with highest CV score.

## 2. Feature Creation
![image](https://user-images.githubusercontent.com/99384454/188111764-fd398301-1436-423a-9709-191e932f98f6.png) <br>
We created 715 polynomial features up to degree 4 followed by greedily remove feature stepwise using RFECV to generate the set of features which result in the highest cross validation score. The final set of features consists of 276 features giving the highest CV score. 
<br>

# Model Training and Optimization
Several family of models were built and optimized using GridSearchCV to find the best model hyperparameters which give the highest cross-validation scores.
The families of models built: KNN, Logistic Regression, SVM, Decision Tree, Bagging and Boosting Ensemble (RandomForest, GradientBoostClassifier, XgBoost, ExtraTreesClassifier, Artificial Neural Network. Ensembles of models are also built and optimized to improve the ability to fit to training data as well as generalize to new unseen data from test dataset.

# Results and Discussion
## 1. Models Performance
<img src="https://user-images.githubusercontent.com/99384454/188113795-4f8aca3c-7571-40a7-b10e-c6ea31a6e8fb.png" width="750">
 
GradientBoostingClassifier give the highest performance across all the models (**Accuracy = 98.6%** and **Fbeta = 99.1%**). <br>
Performance of Tree-based models are generally better compared to linear models (Logistic Regression and SVC) indicating that the decision boundary of the data is in general non-linear, thus recursive partitioning algorithm performs better compared to models which tries to fit linear boundaries. The decision boundary can be observed as the figure below.
![image](https://user-images.githubusercontent.com/99384454/188114620-0cf3abc3-d77f-4b03-b2e3-4795f1612375.png)

## 2. Feature Importance
Based on the analysis of feature importance using both weights of linear model and entropy information gain quantity from Tree-based method, the top 5 important feature contributing to the probablity of a patient dying from CAD are:
  1. Creatinine
  2. Creatinine Phosphokinase
  3. Weight
  4. Age
  5. Platelets
<img src="https://user-images.githubusercontent.com/99384454/188114785-499bad10-f6ab-46c7-b2a7-b18132fc0368.png" width="800">

<br>

# Conclusion
Several models were built to predict the survival chance of CAD patients based on demographics information, health metrics and historical data. Data was ingested, imputed, preprocessed and new features generated before fitting into multiple models for optimization. The model giving best accuracy on the test dataset is GradientBoostingClassifer (**Accuracy = 98.6%** and **Fbeta = 99.1%**). 

