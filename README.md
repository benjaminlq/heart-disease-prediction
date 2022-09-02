# <center> Predicting Survivability of Coronary Artery Disease (CAD) Patients </center>

![](https://img.shields.io/badge/Status-Completed-red)
![](https://img.shields.io/badge/Domain-Health%20Care-blue)
![](https://img.shields.io/badge/Language-Python-green)
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

![image](https://user-images.githubusercontent.com/99384454/188110550-1c45f258-73e8-4752-8916-b88b37a8d3b9.png)

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
## 2. Feature Creation

<br>

# Model Training and Optimization

<br>

# Results and Discussion

<br>

# Conclusion


### Test push

