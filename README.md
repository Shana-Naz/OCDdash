# OCD Patient Diagnosis Dashboard 
# INTRODUCTION
The "OCD Patient Dataset" is a comprehensive collection of information pertaining to 1500 individuals diagnosed with Obsessive-Compulsive Disorder (OCD). This dataset encompasses a wide range of parameters, providing a detailed insight into the demographic and clinical profiles of these individuals.
Included in this dataset are key demographic details such as age, gender, ethnicity, marital status, and education level, offering a comprehensive overview of the sample population. Additionally, clinical information like the date of OCD diagnosis, duration of symptoms, and any previous psychiatric diagnoses are recorded, providing context to the patients' journeys.
The dataset also delves into the specific nature of OCD symptoms, categorizing them into obsession and compulsion types. Severity of these symptoms is assessed using the Yale-Brown Obsessive-Compulsive Scale (Y-BOCS) scores for both obsessions and compulsions. Furthermore, it documents any co-occurring mental health conditions, including depression and anxiety diagnoses.
The dataset outlines the medications prescribed to patients, offering valuable insights into the treatment approaches employed. It also records whether there is a family history of OCD, shedding light on potential genetic or environmental factors.

###  Take a look at the dataset 

Select * from ocd_patient_dataset;

### Query to Count Female vs Male that have ocd and their avg obsession score

SELECT 
    Gender,
    COUNT(`Patient ID`) AS patient_count,
    ROUND(avg(`Y-BOCS Score (Obsessions)`),2) AS avg_obsession_score
    
FROM
    ocd_patient_dataset
    
GROUP BY Gender

ORDER BY patient_count;

### Count of patients by ethnicity and their respective avg obsession score

SELECT
    Ethnicity,
    COUNT(`Patient ID`) AS patient_count,
    ROUND(AVG(`Y-BOCS Score (Obsessions)`),2) AS avg_obsession_score
    
FROM 
    ocd_patient_dataset
    
GROUP BY 
    Ethnicity
    
ORDER BY 
    patient_count;

#### The "OCD Diagnosis Date" column was in Text format. To modify the data type, we use, Alter statement.

ALTER TABLE ocd_patient_dataset 

MODIFY `OCD Diagnosis Date` DATE;

### Number of people diagnosed with OCD month over month

SELECT
     DATE_FORMAT(`OCD Diagnosis Date`, '%Y-%m-01 00:00:00') AS diagnosis_by_month,
     COUNT(`Patient ID`) AS patient_count
     
FROM
     ocd_patient_dataset
     
GROUP BY diagnosis_by_month

ORDER BY diagnosis_by_month;

### What is the Count of the most common obsession type and its respective avg obsession score

SELECT
    `Obsession Type`,
    COUNT(`Patient ID`) AS patient_count,
    ROUND(AVG(`Y-BOCS Score (Obsessions)`),2) AS avg_obsession_score
    
FROM
    ocd_patient_dataset
    
GROUP BY 
    `Obsession Type`
    
ORDER BY 
    patient_count;

### What is the Count of the most common Compulsion type and its respective avg Compulsion score

SELECT
     `Compulsion Type`,
     COUNT(`Patient ID`) AS patient_count,
     ROUND(AVG(`Y-BOCS Score (Compulsions)`),2) AS avg_compulsion_score
     
FROM
    ocd_patient_dataset
    
GROUP BY
    `Compulsion Type`
    
ORDER BY 
     patient_count;

### What is the total duration of symptoms by gender

SELECT
       SUM(`Duration of Symptoms (months)`) AS symptoms_duration,
       Gender
       
FROM
       ocd_patient_dataset
       
GROUP BY gender

Order by gender;

### What is the count of each medications

SELECT 
    Medications,
    COUNT(Medications) AS medications_count
    
FROM
    ocd_patient_dataset
    
GROUP BY Medications

ORDER BY medications_count;

#### The Result Datasets exported to the PC. 

![Photo Collage Maker_2023_12_27_05_49_06](https://github.com/Shana-Naz/OCDdash/assets/123564734/b67aecc9-0650-4a8c-b5a9-bcea5500a417)

#### Load each result datasets into Power BI.

![Photo Collage Maker_2023_12_27_07_34_02](https://github.com/Shana-Naz/OCDdash/assets/123564734/cdf92f05-0115-4ac7-810c-5994ef24d6e3)

# Charts and Graphs

## Avg obsession score by gender

![avg obs score](https://github.com/Shana-Naz/OCDdash/assets/123564734/580eaced-c406-46ad-beb4-6ef26eb31688)

## Patient ethnicity by avg obsession score

![ethnicity](https://github.com/Shana-Naz/OCDdash/assets/123564734/18b0c9b5-9604-4b36-8579-bdaf4f46f7e5)

## Total patients Month over Month

![patients MOM](https://github.com/Shana-Naz/OCDdash/assets/123564734/9dd6e0d8-59dc-40bc-a33d-afd64edd5bcd)

## Obsession types of patients

![obs type](https://github.com/Shana-Naz/OCDdash/assets/123564734/e5f668e0-be9f-4a96-9841-2e02dcafee25)

## Compulsion types of patients

![comp type](https://github.com/Shana-Naz/OCDdash/assets/123564734/07b8d51e-0cab-4212-a18e-5b2cc04a5632)

## Cards to display, "Total Patients", "Avg obsession score", "Avg compulsion score", "Total duration of symptoms"

![ocd cards](https://github.com/Shana-Naz/OCDdash/assets/123564734/bf4a1df8-7373-4331-9a0a-4e4e144483ed)

## Medications given to patients

![medications ocd](https://github.com/Shana-Naz/OCDdash/assets/123564734/709561d9-8a7a-48e9-be5b-558787e7010b)

# DASHBOARD

![Screenshot (17)](https://github.com/Shana-Naz/OCDdash/assets/123564734/2a5d709b-345b-49b6-a47d-0e2696d91c6c)














