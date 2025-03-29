# FrankPracticalApplication3
This is the third Practical Application for Berkeley Machine Learning Certificate Program



## Overview:

In this practical application, we compare the performance of the classifiers we encountered in this section, namely K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines. We will utilize a dataset related to marketing bank products over the telephone.



## Data:

Our dataset comes from the UCI Machine Learning repository. The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns. We will make use of the article accompanying the dataset for more information on the data and features.

### Input variables:

#### bank client data:
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
#### related with the last contact of the current campaign:
8 - contact: contact communication type (categorical: 'cellular','telephone')
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.

#### other attributes:
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
#### social and economic context attributes
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

### Output variable (desired target):

21 - y - has the client subscribed a term deposit? (binary: 'yes','no')



## Notebook:

[Frank_Practical_Application_III_Comparing_Classifiers.ipynb](Frank_Practical_Application_III_Comparing_Classifiers.ipynb)



## Conclusion:

### Base model performance:

Much fast to train and test with good results. 

|      |          Model Name | Training Time (Seconds) | Training Accuracy (%) | Test Accuracy (%) |
| ---: | ------------------: | ----------------------: | --------------------: | ----------------- |
|    0 | Logistic Regression |                  0.6393 |               91.0256 | 91.1233           |
|    1 |                 KNN |                  0.0197 |               92.9079 | 89.8968           |
|    2 |       Decision Tree |                  0.2531 |              100.0000 | 88.8160           |
|    3 |       Random Forest |                  5.0980 |               99.9939 | 91.7547           |
|    4 |                 SVM |                 17.9277 |               91.0073 | 91.1111           |

### Improved model performance:

The improved models take significant more time to run and do not seem achieving much more test accuracy 

|      |          Model Name | Training Time (Seconds) | Training Score | Training Accuracy (%) | Test Score | Test Accuracy (%) | Precision |   Recall | F1 Score | ROC AUC  |
| ---: | ------------------: | ----------------------: | -------------: | --------------------: | ---------: | ----------------: | --------: | -------: | -------: | -------- |
|    0 | Logistic Regression |                111.7884 |       0.910286 |               91.0559 |   0.911233 |           91.1233 |  0.651000 | 0.425900 | 0.514900 | 0.698800 |
|    1 |                 KNN |                420.7560 |       0.902726 |              100.0000 |   0.906011 |           90.6011 |  0.618307 | 0.392975 | 0.480537 | 0.681400 |
|    2 |       Decision Tree |                 71.8473 |       0.912958 |               91.5235 |   0.915118 |           91.5118 |  0.623832 | 0.586169 | 0.604414 | 0.771102 |
|    3 |       Random Forest |               3198.1703 |       0.915508 |               97.4983 |   0.917668 |           91.7668 |  0.669578 | 0.504940 | 0.575720 | 0.736973 |
|    4 |                 SVM |                 94.1014 |       0.900783 |               90.2119 |   0.903825 |           90.3825 |  0.652956 | 0.278814 | 0.390769 | 0.630191 |

### Feature Importance for the best-performing model -- optimized decision tree:

"duration" and "nr.employed" are the top two most important features. 

|      |             Features | Importance (%) |
| ---: | -------------------: | -------------- |
|    7 |             duration | 52.32          |
|   15 |          nr.employed | 31.00          |
|   13 |        cons.conf.idx | 8.86           |
|    9 |                pdays | 2.49           |
|   14 |            euribor3m | 2.00           |
|   12 |       cons.price.idx | 1.59           |
|    5 |                month | 1.37           |
|    6 |          day_of_week | 0.20           |
|   28 |    contact_telephone | 0.11           |
|    8 |             campaign | 0.05           |
|    3 |              housing | 0.00           |
|    0 |                  age | 0.00           |
|    4 |                 loan | 0.00           |
|    1 |            education | 0.00           |
|    2 |              default | 0.00           |
|   11 |         emp.var.rate | 0.00           |
|   10 |             previous | 0.00           |
|   17 |     job_entrepreneur | 0.00           |
|   16 |      job_blue-collar | 0.00           |
|   19 |       job_management | 0.00           |
|   20 |          job_retired | 0.00           |
|   21 |    job_self-employed | 0.00           |
|   18 |        job_housemaid | 0.00           |
|   22 |         job_services | 0.00           |
|   23 |          job_student | 0.00           |
|   25 |       job_unemployed | 0.00           |
|   24 |       job_technician | 0.00           |
|   26 |      marital_married | 0.00           |
|   27 |       marital_single | 0.00           |
|   29 | poutcome_nonexistent | 0.00           |
|   30 |     poutcome_success | 0.00           |
