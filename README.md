# Data Science Project: Loan Defaulting Prediction.

## Project Overview
**Problem Statement**

This project aims to predict loan applicant defaulting for a company using machine learning techniques.
Problem statement: Financial institutions face significant risks due to loan defaults. Accurately predicting probability of default on loans is criticalfor risk management and strategic planning.

## Data
  - Data cleaning,
    1. Currency has been cleaned as data entry may have caused the currency to appear as 2 currencies being offered as loans, but only the difference has been insertion of a $ sign before USD , leading to biased intepretation as two currencies.
    2. Marital status showed a bit of missing information where replacement of empty data points with "other", so that no problems with representing those who didn't disclose their status but still the models need a representation even the problem was on data entry, the models need full representation of information.
    3. Date changed to datetime for full presentation and exploratory reasons.
    4. Remaining term of the loan set upto to 80, if it exceeds this value it is considered an outlier, though the term was not mentioned that they are years or months.
    5. Considering outliers on other numerical features, the values between first 1% and last 1% on all features are removed as extreme values, and this leads to use of tree based models to address this as a potential to overfitting.
    6. Dropped any null entry , done so to avoid insertion of dummies unecessarily as they are few as well comparing to the dataframe.
  - Preprocessing,
    1. Use of LabelEncoder, on gender so that the feature will have full representation on probability of applicant.
    2. Use of OneHotEncoder, on Loan Status so that the target feature will be readable and model will only train with numerical values.
    3. Use of OneHotEncoder, on 'job', 'location' and 'marital_status' for same reasons, full representation of each factor.
    
  - Exploratory data analysis (EDA)
    1. Looking on histogram for normal distribution on numerical features, this leads to realisation of right skewed data, this was later dealt with.
    2. The missing values where seen on this stage on country, job and location. And these values missing where addressed on the cleaning and dropping of outliers that liers in top 1% and down 1%.
    3. Data imbalance in Loan Status reviewed on this stage showing Deafulting applicants where few, leading to minority bias which later corrected by sampling techniques to be discussed below.

  
* Loan applicant demographics.
  
**Top 20 cities and locations applicants come from  (arranged by number of applicants)**
  
- Harare---------8338
- Bulawayo-------8078
- Mutare---------8062
- Gweru----------7803
- Masvingo-------7476
- Marondera------7343
- Rusape---------6378
- Chivhu---------6257
- Plumtree-------5431
- Beitbridge-----5181
- Chipinge-------4358
- Chimanimani----4296
- Kwekwe---------3401
- Chiredzi-------3123
- Kadoma---------3049
- Nyanga---------2099
- Karoi----------1850
- Shurugwi-------1322
- Zvishavane-----1276
- Gokwe----------901

## Methodology
* Data analysis.
  The approach used for this problem is "supervised learning", labeling features that machine will learn on structured data to classify entries accordingly.
  
* Historical Loan applicants information.
  
0.    loan_id ------------90691 non-null  object,        
1.   gender---------------90691 non-null  object ,       
2.   disbursemet_date-----90691 non-null  datetime64[ns],
3.   currency-------------90691 non-null  object ,       
4.   country--------------90691 non-null  object ,       
5.   is_employed----------90691 non-null  bool  ,        
6.   job------------------90691 non-null  object,        
7.   location-------------90691 non-null  object,        
8.   loan_amount----------90691 non-null  float64,       
9.   number_of_defaults---90691 non-null  int64 ,        
10.  outstanding_balance--90691 non-null  float64,       
11.  interest_rate--------90691 non-null  float64,       
12.  age------------------90691 non-null  int64 ,        
13.  remaining_term-------90691 non-null  float64,       
14.  salary---------------90691 non-null  float64,       
15.  marital_status-------90691 non-null  object,        
16.  Loan_Status----------90691 non-null  object,
    
* Data Imbalance was addressed by means of :
1. Oversampling,
2. Synthetic Minority Oversampling Technique(SMOTE),
3. Undersampling (all models trained on all samples to see the best technique)  

## Feature engineering
  Use of OneHotEncoder and LabelEncoder was done on the categorical features for full data representation.
  
* Model training was done on these
  1. XGBoost.
     - Faster to learn and perfom better from literature on categorical features dataset.
  2. Random Forest.
     - Its ability to go deep in learning many aspects by means of forests
  3. KNN.
     - Doesn't make strong assumptions about data distribution
  4. Multilayer Perceptron.
     - Good at processing and learning from large amounts of data.
  5. Decision Tree.
      - The algorithm can help identify the most important features influencing loan default.
  6. Stacking of XGBoost and Random Forest.(Using Logistic Regression as final estimator.)
      - Combining multiple models to reduce overfitting and improve generalization.
     
* Model evaluation.
  - ROC AUC.
  - F1_Score.
  - Precission.
  - Accuracy(though not a basis to perfomance).
## Assumptions.
1. **Data Quality**:
- Data is accurate, complete, and consistent without significant errors or missing values.
- Data is representative of the target population.
- Features are relevant to the prediction of loan default.
2. **Stationarity**:
- The underlying patterns and relationships in the data remain relatively stable over time.
3. **Independence**:
- Observations in the dataset are independent of each other.
4. **Normality**:
- Assumption is relaxed here.
5. **Feature Scaling**:
- Features are on a comparable scale to avoid bias in model performance, done by StandardScaler.

# Results:
* XGBoost	achieved ROC AUC :0.859028, Accuracy: 0.923000, Precision:	0.902585 and F1_Score:	0.894066.
* Identified key factors influencing Defaulting which are as follows in terms of column names:
  - number_of_defaults(previous defaults),
  -  interest_rate,
  -   gender,
  -   age,
  -   loan_amount,
  -   location_Redcliff,
  -   location_Zvishavane,
  -   job_Software_Developer,
  -  location_Nyanga,
  -  remaining_term,
  -  salary,
  -   marital_status_other and in short Location contributed much to the defaulting of the applicant.


## Limitations and Future Work.
- Limitations
  
  **1. Computational resources**: Models from observations made they only need strong Computers and resource maximisation techniques these improving overall perfomance.
- Future Work.
  
  **1. Use of Ensemble Methods**: combining our XGBoost model with other well-performing models using ensemble techniques like stacking or bagging. With the above presentation, future work will  combine models to yield their strengths.
  
  **2. Bayesian Optimization**:Bayesian optimization techniques, like Hyperopt or Optuna, intelligently explore the hyperparameter space, focusing on areas that are more likely to yield better results.

