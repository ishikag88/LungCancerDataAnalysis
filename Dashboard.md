## Analysis done using dashboard
13. Identify the smoking years' impact on lung cancer.  
16. Identify the relation between lung cancer prevalence and air pollution levels.  
    A1 - ss name  
    select Air_Pollution_Exposure, round(avg(Lung_Cancer_Prevalence_Rate),5) as AvgPrevRate  
    from lungcancertable Group by Air_Pollution_Exposure;
    
20. Determine if treatment type has a significant impact on survival years.  
21. Compare lung cancer prevalence in men vs. women across countries.  
22. Find how occupational exposure, smoking, and air pollution collectively impact lung cancer rates.  
23. Analyze the impact of early detection on survival years.
