Toman Bike Share Analysis
Project Overview
This project involves an analysis conducted for Toman Bike Share to determine if increasing prices next year is feasible. As a data analyst,the focus was on examining current and historical data to provide insights for pricing decisions.

Tools and Technologies
SQL: Used for data extraction,transformation,and loading (ETL) processes.
Power BI: Utilized for data visualization and dashboard creation to present findings.
Objectives
Hourly revenue Analysis.
Profit and revenue trends.
Seasonal Revenue.
Rider demographics.
Provide recommendations on raising prices next year.
Key Findings
Conservative Increase: Considering the substantial increase last year,a more conservative increase might be prudent to avoid hitting a price ceiling where demand starts to drop.An increase in the range of 10-15% could test the market's response without risking a significant loss of customers.
Price Setting: If the price in 2022 was $4.99,a 10% increase would make the new price about $5.49, while a 15% increase would set the price at approximately $5.74.
Data Sources
You can access the datasets through the following links:

https://github.com/lbaraza/SQL-Power-BI/blob/main/bike_share_yr_0.csv
https://github.com/lbaraza/SQL-Power-BI/blob/main/bike_share_yr_1.csv
https://github.com/lbaraza/SQL-Power-BI/blob/main/cost_table.csv
Usage
SQL Scripts: Located in the sql directory, containing scripts used for data extraction and transformation.
Power BI Dashboard: Located in the powerbi directory, showcasing the interactive dashboard created for the analysis.
Conclusion
The analysis provides a comprehensive overview of Toman Bike Share's current performance and supports informed decision-making regarding potential price adjustments.

SQL Code
WITH cte AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL
    SELECT * FROM bike_share_yr_1
)

SELECT 
    dteday, 
    season, 
    a.yr, 
    weekday, 
    hr, 
    rider_type, 
    riders, 
    price, 
    COGS, 
    riders * price AS revenue, 
    (riders * price) - COGS AS profit 
FROM 
    cte a 
LEFT JOIN 
    cost_table b 
ON 
    a.yr = b.yr;
Explanation
CTE (Common Table Expression): Combines data from two tables (bike_share_yr_0 and bike_share_yr_1) using UNION ALL.
Main Query: Selects relevant columns from the combined data (cte) and joins with the cost_table on the yr column.
Calculations: Computes revenue as riders * price and profit as (riders * price) - COGS.
