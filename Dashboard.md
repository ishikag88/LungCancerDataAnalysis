## Analysis done using dashboard
13. Identify the smoking years' impact on lung cancer.  
16. Identify the relation between lung cancer prevalence and air pollution levels.  
    A1 - ss name  
    select Air_Pollution_Exposure, round(avg(Lung_Cancer_Prevalence_Rate),5) as AvgPrevRate  
    from lungcancertable Group by Air_Pollution_Exposure;
    
20. Determine if treatment type has a significant impact on survival years.  
    A2  - ss name  
    select Treatment_Type, avg(Survival_Years) as AvgSurvivalYears from lungcancertable  
group by Treatment_Type;

22. Compare lung cancer prevalence in men vs. women across countries.

    A3 - ss name
select Country, gender, avg(Lung_Cancer_Prevalence_Rate) as PrevalenceRate  
from lungcancertable group by country, Gender order by country asc;
    
24. Find how occupational exposure, smoking, and air pollution collectively impact lung cancer rates.  
25. Analyze the impact of early detection on survival years.
