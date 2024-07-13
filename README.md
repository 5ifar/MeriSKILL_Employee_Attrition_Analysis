# <img src="https://media.licdn.com/dms/image/D4D0BAQFONtccW6kb_Q/company-logo_200_200/0/1692808405632?e=2147483647&v=beta&t=5-c1hlCyZ6eWKCDV5g9-B9tiZcc9GRE2MkQVg-vCmv8" width="6%" height="6%"> MeriSKILL - HR Attrition Analysis

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Employee%20Attrition%20HR%20Analysis%20Project%20Thumbnail.png" width="100%" height="100%"> </div>

This repository serves as my documentation for the MeriSKILL HR Attrition Analysis - Power BI Project.

It was created as a learning project as part of my Internship assignment at: [MeriSKILL](https://sites.google.com/view/meriskill/home) during May - June 2024.

It showcases my competancy to work with Microsoft Power BI and demonstrates my proficiency in essential Power BI concepts like Data Profiling, ETL with Power Query, Semantic Data Modelling, DAX Measures & DAX Calculated Columns, Dashboard Designing, Visualization, Conditional Formating, Filters, Bookmarks, Page Navigation, Publishing and Report Optimization etc.

The entire project has been implemented using Microsoft Power BI Desktop 2.128.751.0 and published on Microsoft Power BI Service.

---

## Purpose:
In this report we navigate through the core of HR Analytics, from meticulous data collection to the art of deriving actionable insights from employee attrition data. It involves identifying patterns and optimizing processes that breathes life into our organizational strategies.

HR analytics, also known as Human Resources analytics or talent analytics, is the systematic application of data analysis and statistical methods to human resources data. It involves gathering and analyzing data related to an organization’s workforce to make informed decisions and drive improvements in HR processes, policies, and strategies. The primary goal of HR analytics is to optimize the performance, engagement, and overall effectiveness of an organization’s workforce.

By leveraging HR analytics effectively, organizations can align their human resources strategies with business objectives, enhance organizational performance, and create a more engaged and productive workforce. It’s about leveraging data to make informed decisions that impact both employees and the organization positively.

## Contents:
Please find the resource links for the project below:
- [Purpose](#purpose)
- [Live Dashboard Link](https://app.powerbi.com/view?r=eyJrIjoiM2Y2NTQ2ZWQtMzJmOC00OWVlLTgwOTEtNzhiOWNlMWZiZDRlIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9&pageName=338e9479b01753438a87)
- [Tools used & Methodologies implemented](#tools-used)
- [About the Dataset](#about-the-dataset)
  - [Data Dictionary](#attrition-data-dictionary)
  - [Data Integrity](#data-integrity)
  - [HR Employee Attrition Raw Data](https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Employee%20Attrition%20Raw%20Data/HR-Employee-Attrition.csv)
- [Project Implementation](https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Project%20Implementation/Documentation.md)
- [Analysis Insights](#analysis-insights)
- [Data-driven Recommendations](#data-driven-recommendations)

## Tools used:
1. Microsoft Power BI: for Data Cleaning, Data Analysis, Data Visualization & Dashboarding
2. GitHub - for Documentation

## Skills & Methodologies implemented:
1. Data Cleaning: Power Query
2. Data Manipulation: DAX Measures & Columns
3. Data Modelling and Normalization
4. Data Visualization
5. Dashboarding: Filters, Custom Icon Buttons, Bookmarks, Page Navigation
6. Report Publishing: PBI Service and Report Optimization
7. Documentation

## About the Dataset:
The original dataset is a single file with 1470 records and 35 columns and contains employee related parameterized data that has been categorized into 3 broad types: Deomographics, Turnover & Wellbeing.

### Attrition Data Dictionary:
|Column Name|Type|Description|
|-|-|-|
|Age|int|The age of the employee|
|Attrition|char|Whether the employee has left the company (Yes) or not (No)|
|BusinessTravel|char|Frequency of business travel (e.g., Rarely, Frequently)|
|DailyRate|int|Daily rate of pay|
|Department|char|The department where the employee works|
|DistanceFromHome|int|Distance of employee’s residence from the workplace|
|Education|int|Employee’s education level|
|EducationField|char|Field of education|
|EmployeeNumber|int|Unique identifier for each employee i.e Primary Key|
|EnvironmentSatisfaction|int|Employee’s satisfaction with their work environment|
|Gender|char|Employee’s gender|
|HourlyRate|int|Hourly rate of pay|
|JobInvolvement|int|Level of involvement in the job|
|JobLevel|int|Job level or position in the company|
|JobRole|char|Employee’s role or position at work|
|JobSatisfaction|int|Employee’s job satisfaction level|
|MaritalStatus|char|Employee’s marital status|
|MonthlyIncome|int|Monthly income of the employee|
|MonthlyRate|int|Monthly rate of pay|
|NumCompaniesWorked|int|Number of companies the employee has worked for|
|OverTime|char|Whether the employee works overtime (Yes) or not (No)|
|PercentSalaryHike|int|Percentage increase in salary|
|PerformanceRating|int|Employee’s performance rating|
|RelationshipSatisfaction|int|Employee’s satisfaction with their relationships at work|
|StockOptionLevel|int|Employee’s stock option level|
|TotalWorkingYears|int|Total number of years the employee has worked|
|TrainingTimesLastYear|int|Number of times the employee was trained last year|
|WorkLifeBalance|int|Employee’s perceived work-life balance|
|YearsAtCompany|int|Number of years the employee has worked at the company|
|YearsInCurrentRole|int|Number of years the employee has been in the current role|
|YearsSinceLastPromotion|int|Number of years since the employee’s last promotion|
|YearsWithCurrManager|int|Number of years with the current manager|

These columns collectively provide valuable information about employees in the dataset, which can be used for various HR analytics and decision-making processes.

## Data Integrity:
ROCCC Evaluation:
- Reliability: LOW - The raw dataset is created and updated by MeriSKILL. It has only 1 file. There is no information how the data was collected or preprocessed. 
- Originality: MED - First party provider (MeriSKILL)
- Comprehensiveness: HIGH - Only 1 CSV File was provided however the availability of 1470 records and 35 columns is quite adequate for an in depth analysis on the influence of various factors towards employee attrition.
- Current: LOW - Dataset creation date was not documented/provided by MeriSKILL. So its not very relevant and hence the analysis needs to be comprehended as a general (not year-specific) trend.
- Citation: LOW - No official citation/reference available.

---

## Analysis Insights:

### Employee Demographic Patterns:

- The age category of **Adults (26 – 44 yrs)** is home to the highest workforce, with 876 Active and **157** Attrited employees. However the age category of **Young Adults (18 - 25 yrs)** despite having 2nd lowest Active employee count are affected with the highest Attrition rate of upto **32.5 %** in Males and upto **41.9%** in Females. Perhaps it’s a testament to the wisdom and stability that comes with age.

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%201.1.JPG" width="50%" height="50%"> </div>
<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%201.2.JPG" width="50%" height="50%"> </div>

- **Male** employees dominate our workforce, constituting **882** out of **1470** individuals. However, **Female** employees display a lower Attrition rate at **14.8 %**, contrasting to higher Male Attrition rate of **17 %**.

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%202.JPG" width="50%" height="50%"> </div>

- Attrition rate seems to be higher among employees with **Single Marital status** of around **23 - 26 %** regardless of the employee gender.

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%203.1.JPG" width="50%" height="50%"> </div>
<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%203.2.JPG" width="50%" height="50%"> </div>

- While **Bachelor employees** boast the highest Active employees they are also affected with the 2nd highest Attrition rate of **17.3 %** trailing just behind **High School employees (18.2 %)**, considering the wide range of opportunities available for them in the job market, which narrows down as employees complete their **Doctorate (10.4 %)**.

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%204.JPG" width="50%" height="50%"> </div>

- **HR (25.9 %)**, **Technical Degree (24.2 %)** & **Marketing (22 %)** field employees have Attrited highest in the company.

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%205.JPG" width="50%" height="50%"> </div>

- Attrition increases the longer employees have to travel to office with maximum Attrition rate of **42.9 %** seen around the **24 Km** mark indicating that the majority of employees prefer a close commute, reflecting an aspect of convenience and local integration.

<div align="center"> <img src="https://github.com/5ifar/MeriSKILL_HR_Attrition_Analysis/blob/main/Assets/Insights%20Images/Demographic/HR%20Attrition%20-%20Demographic%20Insights%206.JPG" width="50%" height="50%"> </div>

### Employee Turnover Patterns:

- There seems to be a direct correlation between **Average Monthly Income (AMI)** and Attrition. Managers earn the highest AMI of **17.4K $** and have one of the lowest Attrition rates of **5.5 %** while Sales Representative earn the lowest AMI of **2.6K $** and have the highest Attrition rate of **39.8 %**. The Attrition rate goes up with decreasing AMI hinting at the interplay between financial satisfaction and employee retention.
- Attrition in general goes down as employees scale the corporate ladder as seen with **Entry** level & **Executive** employees showing **26.3 %** & **4.7 %** Attrition rate.
- As employees spend more time in the company, Attrition rate decreases broadly from **36.4 %** at **0 yrs** in the company to **6.7 %** at **22 yrs** in the company post which it displays a contrasting rising trend till **40 yrs** in the company when it reaches **100 %** mark.

### Employee Wellbeing Patterns:

- Employee Satisfaction trends contradict the Attrition trend as expected. As **Employee Satisfaction, Relationship Satisfaction & Job Satisfaction** metrics increase, employee attrition decreases from around **23 %** to **13.2 %**.
- Similar to Employee Satisfaction as **Employee Job Involvement** increases, the Attrition rate decrease from **33.7 %** to just **9 %**.
- Attrition goes up from **8 %** to **24.9 %** as employees need to almost **Never Travel** to **Frequently Travel** for business.
- **Work-Life Balance** metric provides a bell curve trend of Attrition as both **Poor & Very Good WLB** leads to **24.4 %** attrition while **Fair & Good WLB** leads to **15.5 %** attrition on average.
- Increasing **Salary Hike %** leads to decreasing Attrition among employees across all job levels.

---

## Data-driven Recommendations:

### Employee Retention and Job Satisfaction:

- Conduct comprehensive surveys and engage in direct dialogues with employees to understand the underlying reasons for high attrition (Avg **23 %**) due to **Job/Environment/Relationship dissatisfaction**.
- Implement measures to improve **Work-Life Balance**, especially for long-standing employees, to reduce Attrition rates upto **14.2 %**.
- Recognizing the importance of proximity to work in their daily routines, allow **Working from Home (WFH)** for employess living with distance of more than **11 Km** to reduce travel frequency and drop Attrition rates from **24.9 %** to just **8 %**.
- Ensure **Salary Hike %** is at least **15 %** or higher to drastically cut down the attrited employees by almost **50%**.

### Training and Development:

- Offer training opportunities for **Entry-level** and **Junior** employees to bridge any skills gaps, particularly in emerging technologies like Python to complement existing skills in SQL, Excel, Power BI so that they can climb the ladder to be **Executive/Sr. Executives** dropping the attrition by upto **22 %**.

### Financial Incentive Programs:

- Review the **Salary compensation packages** to ensure they are competitive and aligned with industry standards, particularly for job roles with high attrition rates like **Sales Representatives (39.8 %)**, **Sales Executives (17.5 %)**, **Lab Techs (23.9 %)** & **Human Resources (32.1 %)** across the **Sales, HR and R&D** departments.
- Evaluate the effectiveness of **Low & Moderate value Stock Options** and other incentive programs to gauge their impact on employee engagement.

### Gender Diversity and Inclusion:

- Develop initiatives to promote gender diversity at all organizational levels and address any disparities in attrition rates between **Male (17 %)** and **Female (14.8 %)** employees.
- Establish mentorship programs and support networks to encourage the career growth and retention of Male employees within the organization.

### Data-Driven Decision Making:

- Establish regular feedback mechanisms to allow employees to voice concerns, share suggestions, and provide insights into improving workplace dynamics.
- Develop and refine data-driven models to anticipate attrition trends, enabling proactive strategies to retain valuable talent.

By implementing these recommendations, the organization can foster a positive work environment, improve employee satisfaction and retention, and drive organizational growth and success.
