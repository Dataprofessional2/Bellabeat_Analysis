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


-- This query calculates the average number of steps and average sedentary minutes (used here as a proxy for sleep)
-- for each user, by joining daily activity and sleep data using user ID and date.
SELECT da.Id,AVG(Total_Steps) AS AvgSteps, AVG(Sedentary_Minutes) AS AvgSleep
FROM  bellabeat-analysis-458115.BellaBeat_Data.daily_activities as da
JOIN 
bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep as ms
ON da.Id = ms.Id AND da.Activity_Date = ms.date
GROUP BY da.Id;

-- This query calculates the average sedentary minutes for each day of the week.
-- It helps understand whether users are more or less sedentary on weekdays vs weekends.
SELECT FORMAT_DATE('%A', CAST(Activity_Date AS DATE)) AS DayOfWeek,
       AVG(Sedentary_Minutes) AS AvgSleep
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities
GROUP BY DayOfWeek;

-- This query calculates how many distinct days each user tracked activity data.
-- It's a measure of user engagement and consistency.
SELECT Id, COUNT(DISTINCT Activity_Date) AS DaysTracked
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities
GROUP BY Id;

-- This query finds out how many days each user tracked both their activity and sleep data.
-- Useful for identifying fully engaged users.
SELECT da.Id, COUNT(*) AS FullTrackingDays
FROM bellabeat-analysis-458115.BellaBeat_Data.daily_activities as da
JOIN 
bellabeat-analysis-458115.BellaBeat_Data.Minutes_Sleep as ms
ON da.Id = ms.Id AND da.Activity_Date = ms.date
GROUP BY da.Id;  
```


### Bellabeat Market Analysis Summary in R

```r
# Step 1: Install Required Packages 
install.packages("lubridate")
install.packages("ggplot2")
install.packages("tidyr")
install.packages("dplyr")
```
```r
# Step 2: Load Libraries 
library(lubridate)
library(ggplot2)
library(tidyr)
library(dplyr)
```
```r
# Checking if our file exists into the system
file.exists("D://Google_capstone_2//project_files//project_org_file//eleven_project_file/dailyActivity_merged.csv")

#Importing our csv data
Daily_Activity <- read.csv("D://Google_capstone_2//project_files//project_org_file//eleven_project_file/dailyActivity_merged.csv")

# Sleep Data
file.exists("D://Google_capstone_2//project_files//project_org_file//eleven_project_file//minuteSleep_merged.csv")
Sleep_Data <- read.csv("D://Google_capstone_2//project_files//project_org_file//eleven_project_file//minuteSleep_merged.csv")
```
```r
#Viewing Data
View(Sleep_Data)
View(Daily_Activity)

#looking at column names to avoid case sensitive error
colnames(Daily_Activity)

#converting to df
Df=data.frame(Daily_Activity)
print(Df)
```
```r
#Standardising data
Daily_Activity <- Daily_Activity %>%
  mutate(ActivityDate = mdy(ActivityDate))

Sleep_Data <- Sleep_Data %>%
  mutate(date = mdy(date))
```
```r
Daily_Activity <- Daily_Activity %>%
  mutate(
    Weekday = weekdays(ActivityDate),
    Month = month(ActivityDate, label = TRUE, abbr = TRUE)
  )

Daily_Activity %>%
  group_by(Weekday) %>%
  summarise(AverageSteps = mean(TotalSteps))
```
```r
#  Average steps by weekday
Daily_Activity %>%
  group_by(Weekday) %>%
  summarise(AverageSteps = mean(TotalSteps)) %>%
  arrange(match(Weekday, c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")))
```
```r
#Establishing joins
Combined_Data <- Daily_Activity %>%
  inner_join(Sleep_Data, by = c("Id" = "Id", "ActivityDate" = "date"))
```
```r
#  Average sleep on weekends vs weekdays
Combined_Data %>%
  mutate(Weekend = ifelse(Weekday %in% c("Saturday", "Sunday"), "Weekend", "Weekday")) %>%
  group_by(Weekend) %>%
  summarise(AvgSleep = mean(SedentaryMinutes))

# Correlation between steps and calories
Daily_Activity %>%
  summarise(correlation = cor(TotalSteps, Calories, use = "complete.obs"))
```
```r
# Illustrative Visualisations in R
Daily_Activity %>%
  group_by(Weekday) %>%
  summarise(AverageSteps = mean(TotalSteps)) %>%
  ggplot(aes(x = Weekday, y = AverageSteps, fill = Weekday)) +
  geom_bar(stat = "identity") +
  labs(title = "Average Steps by Weekday", x = "Day", y = "Steps") +
  theme_minimal()
```
```r
ggplot(Daily_Activity, aes(x = VeryActiveMinutes, y = SedentaryMinutes)) +
  geom_point(alpha = 0.6, color = "purple") +
  labs(title = "Activity vs Sleep Duration", x = "Very Active Minutes", y = "SedentaryMinutes") +
  theme_minimal()
```

## Key Findings from the Fitbit Daily Activity Project

1. Strong Correlation Between Steps and Calories
The scatter plot and line charts show a positive correlation: as total steps increase, calories burned also increase.
Suggests steps are a good predictor of energy expenditure.

2. Weekday Activity Patterns
From the weekday line chart:
Some days (like Tuesday or Thursday) may consistently show higher step counts.
Weekends (Saturday/Sunday) may have either a drop or rise, depending on user lifestyle (e.g., more free time = more activity, or rest days).
Insight: users follow consistent weekday routines, which can inform fitness plans.

3. Total Steps Vary Significantly Across Days
High variance in daily steps across different days shows that user activity is not uniform.
Implication: motivation or schedule factors affect consistency.

4. Potential Underutilization of Very Active Minutes
If plotted, Very Active Minutes may be low despite high step counts — suggesting low-intensity walking dominates.
Fitness plans may need to promote higher-intensity sessions.

## Recommendations

Product Feature Improvements
Personalized Marketing Strategy
Wellness-Focused Campaigns
Conclusion
Summary of Findings and Business Value

