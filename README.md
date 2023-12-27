# OCD Patient Diagnosis Dashboard 
# INTRODUCTION
The "OCD Patient Dataset" is a comprehensive collection of information pertaining to 1500 individuals diagnosed with Obsessive-Compulsive Disorder (OCD). This dataset encompasses a wide range of parameters, providing a detailed insight into the demographic and clinical profiles of these individuals.
Included in this dataset are key demographic details such as age, gender, ethnicity, marital status, and education level, offering a comprehensive overview of the sample population. Additionally, clinical information like the date of OCD diagnosis, duration of symptoms, and any previous psychiatric diagnoses are recorded, providing context to the patients' journeys.
The dataset also delves into the specific nature of OCD symptoms, categorizing them into obsession and compulsion types. Severity of these symptoms is assessed using the Yale-Brown Obsessive-Compulsive Scale (Y-BOCS) scores for both obsessions and compulsions. Furthermore, it documents any co-occurring mental health conditions, including depression and anxiety diagnoses.
The dataset outlines the medications prescribed to patients, offering valuable insights into the treatment approaches employed. It also records whether there is a family history of OCD, shedding light on potential genetic or environmental factors.

###  Take a look at the dataset 

Select * from ocd_patient_dataset;

### Query to Count Femlae vs Male that have ocd and their avg obsession score

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



