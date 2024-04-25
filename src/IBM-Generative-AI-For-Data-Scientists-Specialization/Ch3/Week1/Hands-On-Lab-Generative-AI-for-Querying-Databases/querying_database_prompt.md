# Prompt instructions 1
We have a Heart Disease prediction dataset with a single table which has the following attributes.
1. age - age in years
2. gender- gender (1 = male; 0 = female)
3. cp - chest pain type
        -- Value 1: typical angina
        -- Value 2: atypical angina
        -- Value 3: non-anginal pain
        -- Value 4: asymptomatic
4. trestbps - resting blood pressure (in mm Hg on admission to the hospital)
5. chol - serum cholestoral in mg/dl
6. fbs - (fasting blood sugar > 120 mg/dl)  (1 = true; 0 = false)
7. restecg - resting electrocardiographic results
        -- Value 0: normal
        -- Value 1: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV)
        -- Value 2: showing probable or definite left ventricular hypertrophy by Estes' criteria
8. thalach - maximum heart rate achieved
9. exang - exercise induced angina (1 = yes; 0 = no)
10. oldpeak - ST depression induced by exercise relative to rest
11. slope - the slope of the peak exercise ST segment
        -- Value 1: upsloping
        -- Value 2: flat
        -- Value 3: downsloping
12. ca - number of major vessels (0-3) colored by flourosopy
13. thal - 3 = normal; 6 = fixed defect; 7 = reversable defect
14. num (the predicted attribute) - diagnosis of heart disease (angiographic disease status)
        -- Value 0: < 50% diameter narrowing
        -- Value 1: > 50% diameter narrowing


# Prompt 1 Age Distribution
Write an SQL query to find the minimum, maximum, and average age of patients in the dataset.


# Response 
SELECT 
    MIN(age) AS min_age,
    MAX(age) AS max_age,
    AVG(age) AS avg_age
FROM 
    heart_disease_prediction_dataset;


# Prompt 2 Gender Analysis
Write and SQL query to count the number of male and female patients in the dataset.


# Response 

SELECT 
    gender,
    COUNT(*) AS patient_count
FROM 
    heart_disease_prediction_dataset
GROUP BY 
    gender;


# Prompt 3 Chest Pain Type Frequency
Write an SQL query to determine the frequency of each type of chest pain (typical angina, atypical angina, non-anginal pain, asymptomatic) among patients."

# Response
SELECT 
    cp,
    COUNT(*) AS pain_frequency
FROM 
    heart_disease_prediction_dataset
GROUP BY 
    cp;



# Prompt 4 Age Group Analysis and Target Variable
Write an SQL query to investigate the distribution of the target variable (presence or absence of heart disease) within different age groups (e.g., 20-30, 30-40, etc.).


# Response
SELECT 
    CASE
        WHEN age BETWEEN 20 AND 30 THEN '20-30'
        WHEN age BETWEEN 31 AND 40 THEN '31-40'
        WHEN age BETWEEN 41 AND 50 THEN '41-50'
        WHEN age BETWEEN 51 AND 60 THEN '51-60'
        WHEN age BETWEEN 61 AND 70 THEN '61-70'
        ELSE 'Above 70'
    END AS age_group,
    SUM(CASE WHEN num = 1 THEN 1 ELSE 0 END) AS heart_disease_count,
    SUM(CASE WHEN num = 0 THEN 1 ELSE 0 END) AS no_heart_disease_count
FROM 
    heart_disease_prediction_dataset
GROUP BY 
    age_group
ORDER BY 
    age_group;


# Practice Prompts 

# Prompt 5 Cholesterol Range:
Find the range of cholesterol levels among patients (minimum, maximum).

# Response
SELECT 
    MIN(chol) AS min_chol,
    MAX(chol) AS max_chol
FROM 
    heart_disease_prediction_dataset;


# Prompt 6 Age Range and Gender Analysis:
Determine the age range (youngest and oldest) for male and female patients separately.


# Response
Certainly! You can use the following SQL query to determine the age range (youngest and oldest) for male and female patients separately:

For Male Patients:
```sql
SELECT 
    'Male' AS gender,
    MIN(age) AS youngest_age,
    MAX(age) AS oldest_age
FROM 
    heart_disease_prediction_dataset
WHERE 
    gender = 1;
```

For Female Patients:
```sql
SELECT 
    'Female' AS gender,
    MIN(age) AS youngest_age,
    MAX(age) AS oldest_age
FROM 
    heart_disease_prediction_dataset
WHERE 
    gender = 0;
```

These queries will provide you with the age range (youngest and oldest) for male and female patients separately in the dataset. You can run these queries on your database to get the desired results.

# Prompt 7 Age Group Analysis and Target Variable:
Investigate the distribution of the target variable (presence or absence of heart disease) within different age groups (e.g., 20-30, 30-40, etc.).


# Response
Certainly! You can use the following SQL query to investigate the distribution of the target variable (presence or absence of heart disease) within different age groups:

```sql
SELECT 
    CASE
        WHEN age BETWEEN 20 AND 30 THEN '20-30'
        WHEN age BETWEEN 31 AND 40 THEN '31-40'
        WHEN age BETWEEN 41 AND 50 THEN '41-50'
        WHEN age BETWEEN 51 AND 60 THEN '51-60'
        WHEN age BETWEEN 61 AND 70 THEN '61-70'
        WHEN age BETWEEN 71 AND 80 THEN '71-80'
        ELSE 'Above 80'
    END AS age_group,
    SUM(CASE WHEN num = 1 THEN 1 ELSE 0 END) AS heart_disease_count,
    SUM(CASE WHEN num = 0 THEN 1 ELSE 0 END) AS no_heart_disease_count
FROM 
    heart_disease_prediction_dataset
GROUP BY 
    age_group
ORDER BY 
    age_group;
```

This query will categorize the patients into different age groups and calculate the count of patients with and without heart disease within each age group. It will provide you with the distribution of the target variable (presence or absence of heart disease) within different age groups. You can run this query on your database to get the desired results.


# Prompt 8 Maximum Heart Rate by Age Group:
Find the maximum heart rate achieved during exercise for different age groups (e.g., 30-40, 40-50, etc.).


# response
Certainly! You can use the following SQL query to find the maximum heart rate achieved during exercise for different age groups:

```sql
SELECT 
    CASE
        WHEN age BETWEEN 20 AND 30 THEN '20-30'
        WHEN age BETWEEN 31 AND 40 THEN '31-40'
        WHEN age BETWEEN 41 AND 50 THEN '41-50'
        WHEN age BETWEEN 51 AND 60 THEN '51-60'
        WHEN age BETWEEN 61 AND 70 THEN '61-70'
        WHEN age BETWEEN 71 AND 80 THEN '71-80'
        ELSE 'Above 80'
    END AS age_group,
    MAX(thalach) AS max_heart_rate
FROM 
    heart_disease_prediction_dataset
GROUP BY 
    age_group
ORDER BY 
    age_group;
```

This query will categorize the patients into different age groups and calculate the maximum heart rate achieved during exercise for each age group. It will provide you with the maximum heart rate achieved for different age groups. You can run this query on your database to get the desired results.


# Prompt 9 Percentage of Patients with High Blood Sugar:
Calculate the percentage of patients with fasting blood sugar greater than 120 mg/dl.

# Response
Certainly! You can use the following SQL query to calculate the percentage of patients with fasting blood sugar greater than 120 mg/dl:

```sql
SELECT 
    (COUNT(CASE WHEN fbs = 1 THEN 1 END) * 100.0 / COUNT(*)) AS percentage_high_fbs
FROM 
    heart_disease_prediction_dataset;
```

This query will calculate the percentage of patients with fasting blood sugar greater than 120 mg/dl in the dataset. You can run this query on your database to get the desired percentage.




# Prompt 10 Ratio of Patients with Resting Electrocardiographic Abnormality:
Find the ratio of patients with abnormal resting electrocardiographic results to those with normal results.



# Response
Certainly! You can use the following SQL query to find the ratio of patients with abnormal resting electrocardiographic results to those with normal results:

```sql
SELECT 
    (COUNT(CASE WHEN restecg != 0 THEN 1 END) * 1.0 / COUNT(CASE WHEN restecg = 0 THEN 1 END)) AS abnormal_to_normal_ratio
FROM 
    heart_disease_prediction_dataset;
```

This query will calculate the ratio of patients with abnormal resting electrocardiographic results to those with normal results in the dataset. You can run this query on your database to get the desired ratio.


# Prompt 11 Number of Patients with Reversible Thalassemia:
Count the number of patients with reversible thalassemia detected by thallium stress testing.


# Response
Certainly! You can use the following SQL query to count the number of patients with reversible thalassemia detected by thallium stress testing:

```sql
SELECT 
    COUNT(*) AS reversible_thalassemia_count
FROM 
    heart_disease_prediction_dataset
WHERE 
    thal = 7;
```

This query will count the number of patients with reversible thalassemia (thal = 7) detected by thallium stress testing in the dataset. You can run this query on your database to get the desired count.


# Prompt 12 Average Age of Patients with Chest Pain:
Calculate the average age of patients who experienced chest pain during diagnosis.


# Response
Certainly! You can use the following SQL query to calculate the average age of patients who experienced chest pain during diagnosis:



# Prompt 12 Distribution of Patients by Number of Major Vessels:
Investigate the distribution of patients based on the number of major vessels colored by fluoroscopy (0-3).

# Response
Certainly! You can use the following SQL query to investigate the distribution of patients based on the number of major vessels colored by fluoroscopy (0-3):

```sql
SELECT 
    ca,
    COUNT(*) AS vessel_count
FROM 
    heart_disease_prediction_dataset
GROUP BY 
    ca;
```

This query will group the patients based on the number of major vessels colored by fluoroscopy (0-3) and provide you with the count of patients for each category. It will help you understand the distribution of patients based on the number of major vessels colored by fluoroscopy. You can run this query on your database to get the desired distribution.