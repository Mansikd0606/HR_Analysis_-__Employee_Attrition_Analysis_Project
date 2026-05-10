# HR_Analysis_-__Employee_Attrition_Analysis_Project

## Project Overview

This project focuses on analyzing employee data to identify workforce trends, employee attrition patterns, job satisfaction levels, salary distribution, and overtime impact within the organization. The project was developed using Python for data cleaning, MySQL for solving business problems through SQL queries, and Microsoft Power BI for creating interactive dashboards and visual reports.

The main objective of this project was to help HR departments make data-driven decisions to improve employee retention and overall workforce performance.

## Problem Statement

Employee attrition is one of the major challenges faced by organizations. High attrition impacts productivity, increases hiring costs, and affects business performance. HR teams need a data-driven solution to identify:

 - Why employees leave the company
 - Which departments have high attrition
 - Whether overtime affects employee retention
 - How salary and job satisfaction impact attrition
 - Which employees are at high risk of leaving

This project was developed to solve these HR business problems using analytics and visualization techniques.

## Project Objectives

 - Analyze employee attrition trends
 - Identify factors affecting employee retention
 - Study overtime impact on attrition
 - Analyze employee satisfaction and work-life balance
 - Evaluate salary distribution across departments
 - Build interactive HR dashboards for decision-making
 - Provide business insights to HR management

## Tools & Technologies Used
- Python --	Data cleaning & preprocessing
- Pandas -- Handling missing values and transformations
- PostgreSQL --	SQL analysis & business problem solving
- Microsoft Power BI	-- Dashboard creation & visualization
- Microsoft Excel	-- Initial data review

## Dataset Description

The dataset contains employee-related information such as:

- Employee ID
- Age
- Gender
- Department
- Job Role
- Monthly Income
- Years at Company
- Work-Life Balance
- Job Satisfaction
- Overtime
- Performance Rating
- Attrition

## Step 1 — Data Cleaning Using Python

Data preprocessing and cleaning were performed using Python and the Pandas library.

### Data Cleaning Steps
- Removed duplicate records
- Handled missing/null values
- Renamed columns for consistency
- Corrected inconsistent categorical values
- Converted data types

## Python Libraries Used
- ```import pandas as pd```  
- ```import matplotlib.pyplot as plt```
- ```from sqlalchemy import create_engine```

## Step 2 — SQL Analysis for Business Problem Solving

After cleaning the dataset, SQL queries were used to solve various HR business problems and generate insights.

## Business Problems Solved Using SQL
1. Department with Highest Attrition
```
SELECT department,
COUNT(*) AS total_attrition
FROM hr_analysis
WHERE attrition = 'Yes'
GROUP BY department
ORDER BY total_attrition DESC;
```

Insight

Sales and HR departments showed the highest employee attrition.

2. Overtime Impact on Attrition
```
SELECT overtime,
COUNT(*) AS employees
FROM hr_analysis
WHERE attrition = 'Yes'
GROUP BY overtime;
```
Insight

Employees working overtime were more likely to leave the company.

3. Average Salary by Job Role
```
SELECT job_role,
AVG(monthly_income) AS avg_salary
FROM hr_analysis
GROUP BY job_role;
```
Insight

Salary differences were identified across job roles.

4. Employees with Low Job Satisfaction
```
SELECT *
FROM hr_analysis
WHERE job_satisfaction <= 2;
```
Insight

Employees with low job satisfaction showed higher attrition trends.

5. High-Risk Employees
```
SELECT *
FROM hr_analysis
WHERE overtime = 'Yes'
AND work_life_balance <= 2
AND job_satisfaction <= 2;
```
Insight

Employees with overtime and poor work-life balance were identified as high-risk employees.

## Step 3 — Power BI Dashboard Development

Interactive dashboards were developed using Microsoft Power BI.

The dashboard contains 2 interactive pages:

## Dashboard Page 1 — HR Analysis Dashboard
## Dashboard Preview

<img width="1278" height="740" alt="Screenshot 2026-05-10 170455" src="https://github.com/user-attachments/assets/e6cd6640-124c-496e-93d0-e37a9ceca896" />

This page provides an overview of the organization’s workforce and employee performance.

## KPIs Included
- Total Employees
- Attrition Count
- Attrition Rate %
- Average Salary
- Active Employee
- Average Age

## Visuals Used
1. Active Employees & Attrition by Department

Visual Type

Clustered Column Chart

Insight
 - HR department has the highest number of employees and attrition cases.
 - Marketing department has the lowest employee count.
   
2. Active Employees by Department
   
Visual Type

Donut Chart

Insight

 - HR department contributes the highest workforce share.
 - Finance and Operations have balanced workforce distribution.
   
3. Average Monthly Income by Job Role
   
Visual Type

Area Chart

Insight

 - Managers and Team Leads receive higher salaries.
 - Recruiters and entry-level roles have comparatively lower salaries.
   
4. Performance by Job Role
   
Visual Type

Donut Chart

Insight

 - Accountant and Data Analyst roles show strong performance scores.
 - Performance distribution is relatively balanced across roles.

5. Total Salary by Department
   
Visual Type

Treemap

Insight

 - HR department has the highest salary expenditure.
 - Marketing and IT departments have lower salary allocations.

6. Total Employees by Department
   
Visual Type

Bar Chart

Insight

 - HR department has the highest employee count.
 - Marketing department has the smallest workforce.
   
7. Job Satisfaction by Job Role
   
Visual Type

Table Visual

Insight

 - Accountants and Data Analysts have higher satisfaction scores.
 - HR Executives and Recruiters show lower satisfaction levels.

## Dashboard Features

- Interactive slicers for:
   - Gender
   - Department
   - Job Role
- Dynamic filtering across all visuals
- KPI cards for executive overview
- Dark-themed professional dashboard design

## Dashboard Page 2 — Attrition Analysis Dashboard
## Dashboard Preview

<img width="1313" height="732" alt="Screenshot 2026-05-10 170554" src="https://github.com/user-attachments/assets/2da8042b-ab85-4398-9009-842236a7d1b2" />

This dashboard specifically focuses on employee attrition trends and retention analysis.

## Visuals Used
1. Attrition by Gender
   
Visual Type

Pie Chart

Insight
- Attrition is almost equally distributed between male and female employees.

2. Attrition by Department
   
Visual Type

Bar Chart

Insight
- HR department has the highest attrition.
- Marketing department has the lowest attrition.
  
3. Attrition by Job Role
   
Visual Type

Horizontal Bar Chart

Insight
- Accountants and Data Analysts show higher attrition.
- HR Executives show relatively lower attrition.

4. Overtime by Attrition
   
Visual Type

Column Chart

Insight
- Employees working overtime are more likely to leave the company.
- Overtime is one of the strongest attrition factors.
  
5. Attrition by Job Satisfaction
   
Visual Type

Donut Chart

Insight
- Employees with low satisfaction levels show higher attrition trends.

6. Attrition by Performance Rating
   
Visual Type

Donut Chart

Insight
- Attrition exists even among good-performing employees, indicating non-performance-related issues.
  
7. Attrition by Work-Life Balance
   
Visual Type

Donut Chart

Insight
- Poor work-life balance strongly impacts employee retention.

## DAX Measures Used
- Attrition Rate %
```
Attrition Rate % =DIVIDE([Attrition Count], [Total Employees]) * 100
```

- Active Employees
```
Active Employees =[Total Employees] - [Attrition Count]
```

- Average Salary
```
Average Salary =AVERAGE('HR Analysis'[monthly_income])
```

- High Risk Employees
```
High Risk Employees =CALCULATE(    COUNT('HR Analysis'[employee_id]),    'HR Analysis'[job_satisfaction] <= 2 &&    'HR Analysis'[overtime] = "Yes")
```

## Key Business Insights
## Workforce Insights
 - HR department has the highest employee count and salary expenditure.
 - Marketing department has the smallest workforce.

## Attrition Insights
 - Attrition rate is 20.33%.
 - Overtime significantly increases employee attrition.
 - Employees with poor work-life balance are more likely to resign.

## Satisfaction Insights
 - Low satisfaction employees contribute heavily to attrition.
 - Some high-performing employees are also leaving the organization.

## Salary Insights
 - Salary imbalance exists among certain job roles.
 - Lower salary groups show higher turnover patterns.

## Challenges Faced During the Project
- Missing and inconsistent data ---- Cleaned using Python Pandas
- Duplicate employee records ---- Removed duplicates
- Complex DAX calculations ---- Built reusable DAX measures
- Dashboard optimization ---- Reduced unnecessary visuals
- Understanding attrition patterns ---- Performed SQL analysis and filtering

## Skills Demonstrated
Technical Skills
- Data Cleaning using Python
- SQL Query Writing
- DAX Measures
- Power BI Dashboard Development
- Data Visualization
- HR Analytics

## Business Skills
- Workforce Analysis
- Employee Retention Analysis
- KPI Reporting
- Business Problem Solving
- Decision Support Analytics

## Conclusion
The HR Analytics & Attrition Analysis project successfully transformed raw employee data into meaningful insights using Python, SQL, and Power BI. The interactive dashboards help HR teams monitor employee performance, identify attrition factors, and improve workforce retention strategies through data-driven decision-making.
This project demonstrates strong analytical thinking, visualization skills, and business understanding required for a Data Analyst role.

