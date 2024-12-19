# Project 2 Analysis

## Introduction

For this project, I investigated the job skills data from the job postings to figure out what are the most valuable skills for data jobs that will improve the chances of getting hired for a high paying data job. I did that by analyzing the following:  

**1. Does acquiring more skills lead to a higher salary?**  
**2. What are the median data job salaries in different countries?**  
**3. What are the top skills for data professionals?**  
**4. What is the salary for the top 10 skills?**  

### Dataset And Excel Tools Used

The [dataset](https://github.com/simonhsieh999/Excel_Project_Data_Analytics/blob/main/Project_2-Analysis/data_jobs_salary_all.xlsx) used is the same as the one from project 1, which contains information about 32,673 job postings that include:
* Job Titles
* Yearly and Hourly Salaries
* Locations
* Skills

However, I used different Excel tools for the analysis, which include:
* Pivot Tables
* Pivot Charts
* Power Query
* Power Pivot
* DAX (Data Analysis Expressions)

## 1. Does acquiring more skills lead to a higher salary?

For this analysis, I first used Power Query, which is an efficient data manipulation tool used to extract, transform, and load data. The following steps were performed in Power Query:

### Extract

The orginal data from the `data_jobs_salary_all.xlsx` file was first extracted onto a blank Excel sheet using the "Get Data" option from the "Data" tab. Then on Power Query, I created 2 queries:
* `data_jobs_salary`: Contains the original data jobs salary data
* `data_jobs_skill`: Contains the skills for each job ID (created by referencing the data_jobs_salary query)

### Transform

On Power Query, I then transformed both queries by doing a series of steps. 

#### Data_jobs_salary query:

<img src="https://github.com/user-attachments/assets/b3a7d460-b53a-434d-a0d9-49dfea75f903" alt="Salary Query" width="250" height="300">

For the data_jobs_salary query, I changed the column types, added the month and date column, and cleaned the text through trimming and removing unnecessary white space and text.

#### Data_jobs_skills query:

<img src="https://github.com/user-attachments/assets/8d3b9a95-b337-4f5b-940e-c15e69780c8f" alt="Salary Query" width="250" height="300">

For the data_jobs_skills query, I kept the job_ID and job_skills columns, and removed the other columns. For the job_skills column, I split each skill into separate columns by a delimiter. Then, I unpivoted the skills columns so that each skill appears in 1 column in separate rows instead.

### Load

After doing the transformations in the two queries, I then loaded both queries into the workbook. 

#### Data_jobs_salary query:

<img src="https://github.com/user-attachments/assets/0d701aac-c30c-41a6-b8f2-e27eea834aab" alt="Salary Query" width="850" height="500">

#### Data_jobs_skills query:

<img src="https://github.com/user-attachments/assets/20f8f5a0-d05c-4563-a0e1-0522236fb572" alt="Salary Query" width="850" height="500">

### Analysis

After extracting, transforming, and loading both the salary and skills data, I can then do my analysis on whether acquiring more skills lead to a higher salary. I created a Pivot Table with the job titles as the rows, and the median salary and skills per job as the values. 

<img src="https://github.com/user-attachments/assets/c50e870c-3eb3-4a99-82ca-96020f8ae295" alt="Salary Query" width="500" height="300">

<img src="https://github.com/user-attachments/assets/2138c9bf-4515-47ca-b5ee-adb79cba94c9" alt="Salary Query" width="650" height="400">

#### Insights From The Graph
* There is a positive correlation between the median salary and the number of skills required for the job position as indicated by the positive slope trend line.
* Engineer roles require more skills than the analyst and scientist roles, yet some of the analyst and scientist roles have a higher median salary than some of the engineer roles requiring more skills. This can mean that for a higher median salary, it's not about the quantity of skills required, but the certain specialized skills for the role that are required. 

## 2. What are the median data job salaries in different countries?

I first used Power Pivot to create a data model that integrates both the data_jobs_salary and data_jobs_skills tables.

![image](https://github.com/user-attachments/assets/dbb14ac4-4b9d-4394-8f01-51e5f6ff287a)

Then, I created a Pivot Table using the data model from Power Pivot. In the Pivot Table, I had the job title as the row, and the median salaries as the values. I wanted to create 3 different median salary columns to analyze: the general median salary, the median salary in the US, and the median salary for countries outside of the US. I did that by creating 3 different DAX measures. 

#### The general median salary measure:

`Median Salary := MEDIAN(data_jobs_all[salary_year_avg])`

#### The US median salary measure:

`=CALCULATE([Median Salary], data_jobs_salary[job_country]="United States")`

#### The non-US median salary measure:

`=CALCULATE([Median Salary], data_jobs_salary[job_country]<>"United States")`

#### Resulting Pivot Table:

<img src="https://github.com/user-attachments/assets/8f1f3bc7-06ce-49df-89de-65cab6e556f5" alt="Salary Query" width="650" height="300">

### Analysis

#### Insights:

* The total US median salary is greater than the total non-US median salary, and there is a big salary gap for engineer roles between the US and non-US. This can indicate that engineer roles in the US are highly valued.
* Senior data engineer and senior data scientist roles command a high salary close to $150,000 for both the US and non-US, which indicates the value of those roles worldwide.

## 3. What are the top skills for data professionals?

In order to find out the top skills for data professionals, I first created a relationship on Power Pivot between the `data_jobs_salary` and `data_jobs_skill` tables using the `job_id` column that exists in both tables within the data model.

<img src="https://github.com/user-attachments/assets/914895b6-c0fa-476e-89ab-86ab87f50a2c" alt="Salary Query" width="650" height="500">

Then, I created a Pivot Table and Pivot Chart using the data model. On the Pivot Table, I had the top 10 skills for the rows, and created a skill likelihood measure that has each skill as a percentage of the total job postings. I then created a bar chart as the Pivot Chart illustrating the top 10 skills in terms of its skill likelihood.

<img src="https://github.com/user-attachments/assets/7998bd49-a7fc-4dde-add0-c8a93e329942" alt="Salary Query" width="650" height="300">

#### Insights:
* From the bar chart, SQL and Python are the top 2 skills by a large margin compared to the other skills. This shows the importance of using those tools in data processing and analysis for data professionals.
* The next top skill is Tableau, which shows the importance of data visualization for data professionals.

## 4. What is the salary for the top 10 skills?

