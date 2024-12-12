# Excel Job Salary Dashboard  

![Dashboard](https://github.com/user-attachments/assets/4b2c9cec-3936-4e18-bb7b-2426288b1cef)

## Introduction

This job salary dashboard enables job seekers to explore different job salaries of their ideal jobs. From the dashboard, users can select a job title, country, and job type of their choice in order for the charts to produce that combination's results, and to compute the combination's median salary, top job platform, and job count.

From the dashboard diagram above, the job title "Data Analyst", the country "United States", and the job type "Full-time" were selected to produce the resulting charts, and to compute the median salary as $90,000, the top job platform as Indeed, and the job count as 6,480.

The dataset used was from Luke Barousse's Excel course, which has information about the different job postings that include the job title, yearly/hourly salary, job location, and the job type. Excel is a powerful tool not only for analyzing data but to also create this dashboard.

Dashboard file: [Project_1_Salary_Dashboard.xlsx](https://github.com/simonhsieh999/Excel_Project_Data_Analytics/blob/main/Project_1-Dashboard/Project%201%20-%20Salary%20Dashboard.xlsx)

## The Dataset Used

The dataset used has information about 32,673 job postings that include:
* Job titles
* Job location
* Job platform of the posted job
* Job type (full-time, part-time, intership, contractor, and temp work)
* On-site work or work-from-home
* Job posted date
* Yearly and hourly salary
* Company
* Skills required

## Dashboard Structure

The following excel tools were used to analyze data and to create the dashboard:
* Data Validation (To create the drop down menus)
* Charts (Bar graph and map)
* Formulas & Functions (Logical, math, statistical, and lookup functions)

### Charts

#### Data Validation

<img src="https://github.com/user-attachments/assets/71661aac-60d3-4fe6-88d6-da201604a713" alt="Job Title Chart" width="300" height="300">
<img src="https://github.com/user-attachments/assets/e8770324-53eb-4b48-8f0a-607cf7cd07a1" alt="Job Title Chart" width="300" height="300">
<img src="https://github.com/user-attachments/assets/d9bc70d8-a7e9-4d73-af6d-83351107683c" alt="Job Title Chart" width="300" height="300">

The drop down menus are created for the job title, country, and job type through data validation to allow users to select the options listed from the menus to explore their ideal jobs.
* The `unique()` function was used to produce the unique job titles, countries, and job type of the dataset. This allowed users to identify what choices they can select.
* Only the unique values from the drop down menus can be selected in order for the charts and results to display correctly.

#### Bar Chart:

<img src="https://github.com/user-attachments/assets/213e9f3f-af6d-4205-bf50-13638fdde5c9" alt="Job Title Chart" width="430" height="330">
<img src="https://github.com/user-attachments/assets/2eb01561-a324-496b-9e3f-27f39167f0c9" alt="Job Type Chart" width="430" height="330">

Horizontal bar charts were plotted to illustrate the results of the job title median salaries and job type based on the selected job title, country, and job type.
* In both bar charts, the selected job title and job type are bolded, which users can easily compare their selected job title and job type with the other ones.
* The job titles and job type are sorted by descending salary, which users can easily identify the highest and lowest job salaries and job type amount.
* From the bar charts above, it is revealed that senior and engineer roles are higher paying than analyst roles, and that the majority of the job types are full-time.

#### Map Chart:

<img src="https://github.com/user-attachments/assets/6f93c831-5903-4f95-bcde-1d5600dd973d" alt="Map Chart" width="430" height="330">

A map chart was plotted to identify the countries with the highest median salaries based on the selected job title and job type. 
* The countries from the map chart are color coded where the ones with a darker blue color are the ones with the higher median salaries, and the countries in grey are ones with no jobs available of the selected job title and type.
* Users can easily differentiate and compare the job salaries of each country, and can move the cursor towards a certain country to display its exact median salary
* For full-time data analyst positions, from the map above, the cursor is on the United States country where it displays the median salary to be $90,000. Also, the country that is dark blue is Belarus, which has the highest median salary of $400,000.

### Formulas & Functions

#### Computing the job title's median salary:

<img src="https://github.com/user-attachments/assets/b8f4065f-52e5-4936-ada4-e2f838ef3527" alt="Median Salary" width="400" height="500">

In order to compute the median salary of each of the job titles, a separate Excel sheet was used to store the computed data. First, the `unique()` function was used to gather the unique job titles. Then, the following formula & functions were used:

<img src="https://github.com/user-attachments/assets/a488303c-5b5d-48d3-8f68-c4728d930782" alt="Median Formula" width="500" height="200">

The `median()` function was used along with a nested `if()` function to compute an array of the job title median salaries based on the selected job title, country, job type, and the existence of a yearly salary. The following results have been produced:

<img src="https://github.com/user-attachments/assets/719785be-76e4-4675-85e2-faa002b7214b" alt="Median Salary Results" width="300" height="230">  

The median salaries were then sorted in ascending order so that the job title bar graph can display the results in descending order. Also, 2 other columns were created based on the selected job title so that the bar graph can display the selected job title in dark blue, and the other job titles in light blue.  

<img src="https://github.com/user-attachments/assets/4af9889e-2469-43dc-8ad5-f62ea535d74c" alt="Median Salary Columns" width="400" height="230">

Finally, to display the median salary of the selected job title onto the dashboard, the `xlookup()` function was used:
<img src="https://github.com/user-attachments/assets/67aabe47-ba92-4faf-9b33-de03502c6675" alt="Xlookup Median Salary" width="300" height="40">  
#### Computing the job count:

<img src="https://github.com/user-attachments/assets/ac9dfb42-16db-4cbf-b900-8e89bedfe670" alt="Counts" width="400" height="500">

To compute the job count of the job title, country, and job type selected, the `count()` function was used with a nested `if()` function. Similar to the median function used, the job title, country, job type, and the existence of a yearly salary conditions were incorporated into the count function.

<img src="https://github.com/user-attachments/assets/156c2fe2-541f-4db9-ac91-d1a8fcb66a97" alt="Job Count Function" width="500" height="200">  

The formula will produce the resulting array, in which the selected job title count will be displayed on the dashboard through the xlookup function: 

<img src="https://github.com/user-attachments/assets/d9725889-b46e-46fb-8014-3981e1fb2873" alt="Job Count Results" width="300" height="250">

## Conclusion

This dashboard can be beneficial for job seekers looking to explore salary information of different jobs based on the titles, countries, platform, and job type. Job seekers can use that information to identify trends in order to make decisions about their career path. 

