# Data Science Project: Loan Defaulting Prediction.

**Project Overview:**
This project aims to predict loan applicant defaulting for a company using machine learning techniques.

**Data:**
* Loan applicant demographics
**Top 20 cities and locations applicants come from  (arranged by number of applicants)**
- Harare         8338
- Bulawayo       8078
- Mutare         8062
- Gweru          7803
- Masvingo       7476
- Marondera      7343
- Rusape         6378
- Chivhu         6257
- Plumtree       5431
- Beitbridge     5181
- Chipinge       4358
- Chimanimani    4296
- Kwekwe         3401
- Chiredzi       3123
- Kadoma         3049
- Nyanga         2099
- Karoi          1850
- Shurugwi       1322
- Zvishavane     1276
- Gokwe           901

**Methodology:**
* Exploratory data analysis
* Our historical Loan applicants information as follows.
0   loan_id              90691 non-null  object,        
1   gender               90691 non-null  object ,       
2   disbursemet_date     90691 non-null  datetime64[ns],
3   currency             90691 non-null  object ,       
4   country              90691 non-null  object ,       
5   is_employed          90691 non-null  bool  ,        
6   job                  90691 non-null  object,        
7   location             90691 non-null  object,        
8   loan_amount          90691 non-null  float64,       
9   number_of_defaults   90691 non-null  int64 ,        
10  outstanding_balance  90691 non-null  float64,       
11  interest_rate        90691 non-null  float64,       
12  age                  90691 non-null  int64 ,        
13  remaining_term       90691 non-null  float64,       
14  salary               90691 non-null  float64,       
15  marital_status       90691 non-null  object,        
16  Loan_Status          90691 non-null  object,
*Data Imbalance was addressed by means of : Oversampling, Synthetic Minority Oversampling Technique(SMOTE) and undersampling (all models trained on all samples to see the best technique)    
* Feature engineering
  Use of OneHotEncoder and LabelEncoder was done on the categorical features for full data representation.
* Model training was done on these
  1. XGBoost.
  2, Random Forest.
  3. KNN.
  4. Multilayer Perceptron.
  5. Decision Tree.
  6. Stacking of XGBoost and Random Forest.
* Model evaluation
  -ROC AUC
  -F1_Score
  -Precission
  -Accuracy(though not a basis to perfomance)

**Results:**
* XGBoost	achieved ROC AUC :0.859028, Accuracy: 0.923000, Precision:	0.902585 and F1_Score:	0.894066.
* Identified key factors influencing Defaulting which are as follows in terms of column names:
  -number_of_defaults(previous defaults), interest_rate, gender, age, loan_amount,location_Redcliff, location_Zvishavane, job_Software_Developer, location_Nyanga,remaining_term, salary, marital_status_other and in short Location contributed much to the defaulting of the applicant.

**License:**
MIT License
