# Diabetes-Reamission Prediction using ML
* ML project to predict the potential diabetes patients who are prone to get readmitted within 30 days of discharge.
* **Objective:** To help hospitals filter out patients and provide them with better post discharge care, monitoring and education.
* Use Statistics and Visualization techniques to understand the important factors which affect the target class and get business inferences.
* Final Model building - Use ensemble techniques to design a custom voting classifier model.

## Code and Resources Used
**Python Version:** 3.7  
**Packages:** pandas, numpy, statsmodel, scipy, matplotlib, seaborn, sklearn, imblearn
**Tableau Public**

## Dataset Features and Description
* The data set is chosen from UCI machine learning repository and is a 10-years (from 1999 to 2008) historical data set of clinical care at 130 US hospitals and integrated delivery networks. 
* It contains 101766 records and includes 50 features 
* Features represent patient demographic details, data collected during the admission and discharge, and medications given during the encounter.

## Data Cleaning steps
* Redundant Columns removal
* Data Type casting
*	Missing values handling
*	Data Encoding

## EDA steps
* **Five point Descriptive Statistics** - Univariate description of both the numerical and categorical variables
* **Correlation and Pair plot** - Distribution and the relation between the numerial variables
* **Univariate, Bivariate and Multivariate Analysis** - Plotting Countplots, Barplots and 100% stacked barplots to visualize and infer the importance of the features

# Important EDA Questions
1. **What is the age group distribution of patients getting admitted for diabetes?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/81979c6ac696d6ec2b9d12e78e9dcae3aa8853f8/Age.jpg "Diabetes patients Age group distribution")
The 81% of the Diabetes patients belong to the age groups between 50 and 90
2. **What are the major primary and secondary diagnoses provided for the diabetes patients after admission?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/1db2b83db39b6dbe056e703c294f394cd9e52e67/Diag1.jpg "Primary Diagnosis during admission")
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/1db2b83db39b6dbe056e703c294f394cd9e52e67/Diag2.jpg "Secondary Diagnosis during admission")
Diagnoses related to Circulatory System, Endocrine and Respiratory sytem are given to majority of the patient as primary and secondary diagnoses
3. **Which medications are commonly prescribed for diabetes patients?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/938b398e21c281680227b6bd339136af4c4d2b8e/DiabetesMedications.jpg "Most common diabetes medications")
Remaining all the medications are rarely used
4. **Does medications changed during the encounter?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/81979c6ac696d6ec2b9d12e78e9dcae3aa8853f8/Medications%20change.jpg "Countplot change in medications")
For 53% of the patients, medications were not changed.
5. **Does Age have an effect in readmission?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/b3bacf56a41d25ee397ff713b715dd4556aa37e9/AgeVsReadmission.jpg "Age vs Readmission")
- Patients in the age group of 20-30 has the highest chance of readmission
- Patients in the age group < 20 has minimal chance
- There is no significant difference observed for patients in the age group above 30
6. **Does patients belonging to a particular race are prone to readmission within 30 days?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/7d442822c1459ba48e9289e43e1842625a453127/RaceVsReadmission.jpg "Race vs Readmission")
Patients belonging to all the race groups have similar rate of readmission
7. **Can the state of the patient during admission or discharge indicate readmission?**
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/401e3a998cb3292612975e41c7f645932e9235db/admission_source_idVsReadmission.jpg "Admission_source_id vs Readmission")
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/401e3a998cb3292612975e41c7f645932e9235db/discharge_disposition_idVsReadmission.jpg "Discharge_disposition_id vs Readmission")
Yes, Patients noted with the followint admission and discharge states have higher chances of readmission
- Admission source id as Court/Law Inforcement and Emergency
- Discharge disposition id as Patient 

## Complexity observed
- Class imbalance
- Huge overlap between class based on the features
- Ouliers influence

## Feature Selection
* VIF Factor for multi collinearity
* Mann Whitney statistical Test for numerical features
* Chi-Square Yate's Correction statistical Test for categorical features
* Reverse Backward Elimation method

## Final Model building Approach
* Model building – 126 models each for both Outliers and Non Outliers dataset
* Model performance metrics – Precision, Recall, Accuracy, ROC_AUC
* Model selection – Precison and Recall Ranks
* Hyper parameter tuning - GridSearchCV
* Final model – Custom voting classifier, Voting method

## Final Model Performance
### Non Outliers
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/840929d0e6b75b9c2acffa02c82516e826abb8c6/Non%20outliers.jpg "Non Outliers model classification report")
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/840929d0e6b75b9c2acffa02c82516e826abb8c6/Crosstab%20Non%20Outliers.jpg "Non Outliers crosstab")
-	The model predicts approximately 49% of the total diabetes patients as potential for readmission in 30 days which is 4.4 times more than the actual that got readmitted
-	The model is able to capture 69% of the people who actually got readmitted 
-	If the model predict as potential for readmission, there is 16% chance that the patient will get actually readmitted. On the other hand, if the model predict someone not potential for readmission, there is only 7% chance that the patient will get readmitted
### Outliers
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/840929d0e6b75b9c2acffa02c82516e826abb8c6/Outliers.jpg "Outliers model classification report")
![alt text](https://github.com/kihtrakinam/Diabetes-Reamission/blob/840929d0e6b75b9c2acffa02c82516e826abb8c6/Crostab%20Outliers.jpg "Outliers crosstab")
-	The model predicts approximately 55% of the diabetes patients as potential for readmission in 30 days which is 3.67 times more than the actual that got readmitted 
-	The model is able to capture 71% of the people who actually got readmitted 
-	If the model predict as potential for readmission, there is 20% chance that the patient will get actually readmitted. On the other hand, if the model predict someone not potential for readmission, there is only 9% chance that the patient will get readmitted

## Business Conclusion
The ideal solution when we have infinite or enough resources is to provide post discharge care for all the patients to reduce readmission. But in a real world, it is not possible to provide care for all the patients. Hence, the hospital should filter out patients who are potential to get readmitted and can be potentially prevented. Then, they can focus their resources and help them recover without readmission in 30 days. 
