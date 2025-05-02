# Bellabeat_Analysis
"This repository contains projects and case studies related to the Google Data Analytics Certification. It includes data cleaning, analysis, visualization, and insights using tools like SQL, R, and Tableau. The goal is to apply real-world data analytics techniques to solve business problems and derive actionable insights."







---

#GOOGLE-DATA-ANALYTICS

## GOOGLE DATA ANALYTICS

## How Can a Wellness Technology Company Play It Smart?

###Table Of Contents

- Introduction

- Overview of Bellabeat and Its Products
- Business Objective
- Data Cleaning & Preparation
- Data Loading and Inspection
- Handling Missing Values
- Standardizing and Formatting
- Exploratory Data Analysis (EDA)

- User Behavior Insights (Steps, Calories, Heart Rate, Sleep)
- Activity Intensity Trends (Daily & Hourly)
- Peak Usage Patterns


- Key Insights & Findings

- Trends in Smart Device Usage

- User Engagement by Activity Type

- Sedentary vs. Active Patterns


-Recommendations
- Product Feature Improvements
- Personalized Marketing Strategy
- Wellness-Focused Campaigns
- Conclusion
- Summary of Findings and Business Value




---

## Project Overview: Bellabeat Market Growth Strategy

Client: Bellabeat – a wellness tech company focused on women’s health
Challenge: Leverage smart device usage data to discover patterns and create a data-driven marketing strategy.

Objective: Analyze Fitbit smart device data to understand user behavior and develop actionable insights to support Bellabeat's product and marketing decisions.

Tools Used: Excel, R, SQL, Visualisations

Data Source: Publicly available Fitbit data (via Kaggle)

Technologies:

Excel – Data cleaning and structuring [Fitbit Health Data](https://www.kaggle.com/datasets/arashnic/fitbit)

R – Data transformation, analysis, and visualization

SQL – Filtering and querying datasets

Tableau – Visualization creation and data storytelling



---

### Data Cleaning & Preparation

#### Performed the following key tasks:

- Loaded and inspected datasets: daily activity, heart rate, sleep, and hourly intensity

- Standardized date formats and column naming conventions

- Removed or flagged outliers in Datasets

- Combined and joined datasets for comprehensive analysis





### Exploratory Data Analysis (EDA)

- EDA focused on revealing user habits and smart device engagement:

- What times of day and week show the most activity?

- How do users differ in activity intensity, steps, and calories burned?

- Is there a pattern between heart rate, movement, and sleep?

- Which users show consistent engagement or inactivity?


## Data Analysis using SQL
###Including some code features I worked with.

```sql
-- Select statements to access specific tables
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity ;
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Hourly_Calorie ;
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Hourly_Steps ;
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep ;
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info;
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities;
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.minutes_mets ;
```
```sql
# Summary stats of hourly intensity table
select max(Average_Intensity) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity as Max_hourly_Intensity ;
select count(*) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity 
group by Average_Intensity;
select avg(Average_Intensity) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity as Average_hourly_Intensity ;
select * from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity
order by Average_Intensity;
Select MAX(Total_Intensity) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity;
select avg(Total_Intensity) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity;
select min(Total_Intensity) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity;
select count(Id) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity;
select count(distinct Id) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity;
select count(Id) from bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity
group by Activity_Time
order by Activity_Time desc;
SELECT
  CAST(Activity_Time AS TIME) AS activity_time_casted,
  COUNT(Id) AS count
FROM bellabeat-analysis-458115.BellaBeat_Data.Hour_Intensity
GROUP BY activity_time_casted
ORDER BY activity_time_casted DESC;
```

```sql
# Summary stats of weight log info table
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info;
select cast(Time as time),Id from bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info;
select avg(WeightKg) from bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info;
SELECT AVG(BMI) FROM bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info;
SELECT Max(BMI) FROM bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info;
SELECT column_name
FROM bellabeat-analysis-458115.BellaBeat_Data.INFORMATION_SCHEMA.COLUMNS
WHERE table_name = 'Weight_Log_Info';
select count(Id) from bellabeat-analysis-458115.BellaBeat_Data.Weight_Log_Info
group by IsmanualReport;
```

```sql
# Summary Statistics from Hourly CAalorie Table
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Hourly_Calorie ;
select max(Calories) from bellabeat-analysis-458115.BellaBeat_Data.Hourly_Calorie as max_calorie;
select avg(Calories) from bellabeat-analysis-458115.BellaBeat_Data.Hourly_Calorie;
SELECT 
  *, 
  CAST(Activity_Time AS TIME) AS activity_time_casted
FROM bellabeat-analysis-458115.BellaBeat_Data.Hourly_Calorie
WHERE Calories < 200
ORDER BY activity_time_casted;
```

```sql
# Summary statistics for Hourly Steps Table

SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Hourly_Steps ;

select avg(Step_Total) from bellabeat-analysis-458115.BellaBeat_Data.Hourly_Steps;

select max(Step_Total) from bellabeat-analysis-458115.BellaBeat_Data.Hourly_Steps;

select min(Step_Total) from bellabeat-analysis-458115.BellaBeat_Data.Hourly_Steps;

select count(*),cast(Activity_Time as time ) as Casted_Time

from bellabeat-analysis-458115.BellaBeat_Data.Hourly_Steps

group by Casted_Time

Order by Casted_Time;

```
```sql
# Summary stats for minute sleep table
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep;
select max(value) from bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep;
select avg(value) from bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep;
select count(distinct Id),
cast(Time as time) 
from bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep
group by Time
order by Time desc
;
```
```sql
# summary stats for daily_activities
SELECT * FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities;
select max(Total_Steps) as maximum_step from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
select avg(Total_Steps) as avg_step from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
select max(Total_Distance) as maximum_dist from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
select avg(Total_Distance) as avg_dist from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
select max(Calories_Burned) as maximum_kcal from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
select avg(Calories_Burned) as avg_kcal from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
select (avg(Total_Steps)/avg(Calories_Burned)) from bellabeat-analysis-458115.BellaBeat_Data.daily_activities ;
```

```sql
#Understanding who is more active and who is mostly sedentary.
SELECT Id, AVG(Very_Active_Minutes) as avg_active_min, AVG(Sedentary_Minutes) as sed_min
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities
GROUP BY Id;

# Find how often users don't reach basic activity levels.
SELECT Id, COUNT(*) AS LazyDays
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities
WHERE Total_Steps < 5000
GROUP BY Id;


# Relationship Analysis
#Steps vs. Calories Correlation 
SELECT Total_Steps,Calories_Burned
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities;

# Do more active users sleep better?
SELECT da.Id,Very_Active_Minutes ,Sedentary_Minutes
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities as da
JOIN 
bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep as ms
ON da.Id = ms.Id AND da.Activity_Date = ms.date ;



SELECT da.Id,AVG(Total_Steps) AS AvgSteps, AVG(Sedentary_Minutes) AS AvgSleep
FROM  bellabeat-analysis-458115.BellaBeat_Data.daily_activities as da
JOIN 
bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep as ms
ON da.Id = ms.Id AND da.Activity_Date = ms.date
GROUP BY da.Id;


SELECT FORMAT_DATE('%A', CAST(Activity_Date AS DATE)) AS DayOfWeek,
       AVG(Sedentary_Minutes) AS AvgSleep
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities
GROUP BY DayOfWeek;

SELECT Id, COUNT(DISTINCT Activity_Date) AS DaysTracked
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities
GROUP BY Id;

SELECT da.Id, COUNT(*) AS FullTrackingDays
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities as da
JOIN 
bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep as ms
ON da.Id = ms.Id AND da.Activity_Date = ms.date
GROUP BY da.Id;  ```


