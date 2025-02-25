## Step 1. Data Cleaning
  - Duplicate Data : None
  - Missing Data : Yes, in 2 columns cancer_stage and treatment_type,  
    handled with none as a value by choosing not null constraint in sql table
    
## Step 2. Create SQL Database Table
 - Tool : Microsoft SQL Management Studio Version 20.2
 - Language : T-SQL
 - Rows : 220632
 - Columns : 24
 - Query to create table :  
   CREATE TABLE lung_cancer_data (
    ID INT PRIMARY KEY,
    Country VARCHAR(255),
    Population_Size INT,
    Age INT,
    Gender VARCHAR(10),
    Smoker VARCHAR(3),
    Years_of_Smoking INT,
    Cigarettes_per_Day INT,
    Passive_Smoker VARCHAR(3),
    Family_History VARCHAR(3),
    Lung_Cancer_Diagnosis VARCHAR(3),
    Cancer_Stage VARCHAR(50),
    Survival_Years INT,
    Adenocarcinoma_Type VARCHAR(50),
    Air_Pollution_Exposure VARCHAR(10),
    Occupational_Exposure VARCHAR(3),
    Indoor_Pollution VARCHAR(3),
    Healthcare_Access VARCHAR(50),
    Early_Detection VARCHAR(3),
    Treatment_Type VARCHAR(50),
    Developed_or_Developing VARCHAR(50),
    Annual_Lung_Cancer_Deaths INT,
    Lung_Cancer_Prevalence_Rate FLOAT,
    Mortality_Rate FLOAT
);

## Step 3. Ask Questions
*1. Retrieve all records for individuals diagnosed with lung cancer.*  
select * from lungcancertable where Lung_Cancer_Diagnosis='Yes';

*2. Count the number of smokers and non-smokers.*  
select Smoker, count(smoker) as Smokers_count 
from lungcancertable group by smoker;

*3. List all unique cancer stages present in the dataset.*  
select count(cancer_stage) as count, cancer_stage from lungcancertable
group by Cancer_Stage order by Cancer_Stage;

*4. Retrieve the average number of cigarettes smoked per day by smokers.*  
select smoker, AVG(cigarettes_per_day) as AvgCigPerDay from lungcancertable
group by smoker;

*5. Count the number of people exposed to high air pollution.*  
select sum(case when air_pollution_exposure = 'high' then 1 else 0 end) as HighAirPolCount  
from lungcancertable

*6. Find the top 5 countries with the highest lung cancer deaths.*  
SELECT Country, SUM(CAST(Annual_Lung_Cancer_Deaths AS BIGINT)) AS AnnualDeaths
FROM lungcancertable
GROUP BY Country 
ORDER BY annualdeaths DESC;

*7. Count the number of people diagnosed with lung cancer by gender.*  
select Gender, sum(case when lung_cancer_diagnosis = 'Yes' then 1 else 0 end) as Countbygender
from lungcancertable
group by Gender

*8. Retrieve records of individuals older than 60 who are diagnosed with lung cancer.*  
select * from lungcancertable 
where age>60 and Lung_Cancer_Diagnosis = 'Yes';

*9. Find the percentage of smokers who developed lung cancer.*  
*10. Calculate the average survival years based on cancer stages.*  
*11. Count the number of lung cancer patients based on passive smoking.*  
*12. Find the country with the highest lung cancer prevalence rate.*  
*13. Identify the smoking years' impact on lung cancer.*  
*14. Determine the mortality rate for patients with and without early detection.*  
*15. Group the lung cancer prevalence rate by developed vs. developing countries.*  
*16. Identify the correlation between lung cancer prevalence and air pollution levels.*  
*17. Find the average age of lung cancer patients for each country.*  
*18. Calculate the risk factor of lung cancer by smoker status, passive smoking, and family history.*  
*19. Rank countries based on their mortality rate.*  
*20. Determine if treatment type has a significant impact on survival years.*  
*21. Compare lung cancer prevalence in men vs. women across countries.*  
*22. Find how occupational exposure, smoking, and air pollution collectively impact lung cancer rates.*  
*23. Analyze the impact of early detection on survival years.*  
