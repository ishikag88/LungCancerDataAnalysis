## Step 1. Data Cleaning
  - Duplicate Data : None
  - Missing Data : Yes, in 2 columns cancer_stage and treatment_type,  
    handled with none as a value by choosing not null constraint in sql table  
<picture><img src="Q3 Duplicates.png"></picture>
    
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
<picture>
<img src="Q1.png">
</picture>  

*2. Count the number of smokers and non-smokers.*  

select Smoker, count(smoker) as Smokers_count from lungcancertable group by smoker;

<picture>
<img src="Q2.png">
</picture>  

*3. List all unique cancer stages present in the dataset.*  

select count(cancer_stage) as count, cancer_stage from lungcancertable group by Cancer_Stage  
order by Cancer_Stage;

<picture>
<img src="Q3.png">
</picture>  

*4. Retrieve the average number of cigarettes smoked per day by smokers.*  

select smoker, AVG(cigarettes_per_day) as AvgCigPerDay from lungcancertable group by smoker;

<picture>
<img src="Q4.png">
</picture>  

*5. Count the number of people exposed to high air pollution.*  

select sum(case when air_pollution_exposure = 'high' then 1 else 0 end) as HighAirPolCount  
from lungcancertable;

<picture>
<img src="Q5.png">
</picture>  

*6. Find the top 5 countries with the highest lung cancer deaths.*  

SELECT Country, SUM(CAST(Annual_Lung_Cancer_Deaths AS BIGINT)) AS AnnualDeaths  
FROM lungcancertable  
GROUP BY Country ORDER BY annualdeaths DESC;

<picture>
<img src="Q6.png">
</picture>

<picture>
<img src="Q6 II.png">
</picture>  

*7. Count the number of people diagnosed with lung cancer by gender.*  

select Gender, sum(case when lung_cancer_diagnosis = 'Yes' then 1 else 0 end)  
as Countbygender from lungcancertable group by Gender

<picture>
<img src="Q7.png">
</picture>  

*8. Retrieve records of individuals older than 60 who are diagnosed with lung cancer.*  

select * from lungcancertable where age>60 and Lung_Cancer_Diagnosis = 'Yes';

<picture>
<img src="Q8.png">
</picture>

<picture>
<img src="Q8 I.png">
</picture>  

*9. Find the percentage of smokers who developed lung cancer.*  

select 
sum(case when lung_cancer_diagnosis = 'Yes' and Developed_or_developing = 'Developed'  
then 1 else 0 end)*100.0/  
sum(case when lung_cancer_diagnosis = 'Yes' then 1 else 0 end) as percentofdevelopedLC  
from lungcancertable

<picture>
<img src="Q9.png">
</picture>  

*10. Calculate the average survival years based on cancer stages.*  

select cancer_stage, avg(survival_years) as AvgSurvivalYears  
from lungcancertable group by cancer_stage order by cancer_stage;

<picture>
<img src="Q.10.png">
</picture>  

*11. Count the number of lung cancer patients based on passive smoking.*  

select sum(case when lung_cancer_diagnosis = 'Yes' and passive_smoker = 'Yes'  
then 1 else 0 end) as Result from lungcancertable  

<picture>
<img src=".png">
</picture>

*12. Find the country with the highest lung cancer prevalence rate.* 

SELECT country, Lung_Cancer_Prevalence_Rate FROM lungcancertable  
WHERE Lung_Cancer_Prevalence_Rate =  
(SELECT MAX(Lung_Cancer_Prevalence_Rate) FROM lungcancertable);  

<picture>
<img src=".png">
</picture>

~~13. Identify the smoking years' impact on lung cancer.~~


*14. Determine the mortality rate for patients with and without early detection.*  

<picture>
<img src=".png">
</picture>

*15. Group the lung cancer prevalence rate by developed vs. developing countries.*  

<picture>
<img src=".png">
</picture>

*16. Identify the correlation between lung cancer prevalence and air pollution levels.*  

<picture>
<img src=".png">
</picture>

*17. Find the average age of lung cancer patients for each country.*  

<picture>
<img src=".png">
</picture>

*18. Calculate the risk factor of lung cancer by smoker status, passive smoking, and family history.*  

<picture>
<img src=".png">
</picture>

*19. Rank countries based on their mortality rate.*  

<picture>
<img src=".png">
</picture>

*20. Determine if treatment type has a significant impact on survival years.*  

<picture>
<img src=".png">
</picture>

*21. Compare lung cancer prevalence in men vs. women across countries.*  

<picture>
<img src=".png">
</picture>

*22. Find how occupational exposure, smoking, and air pollution collectively impact lung cancer rates.*  

<picture>
<img src=".png">
</picture>

*23. Analyze the impact of early detection on survival years.*  

<picture>
<img src=".png">
</picture>

