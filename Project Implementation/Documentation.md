# 🧬 MeriSKILL HR Attrition Analysis Project Phase-wise Implementation

---

## Table of Contents
- [Phase 1: ETL with Power Query](#phase-1-etl-with-power-query)
- [Phase 2: Demographics View](#phase-2-demographics-view)
- [Phase 3: Turnover View](#phase-3-turnover-view)
- [Phase 4: Well being View](#phase-4-well-being-view)
- [Phase 5: Slicer Panel](#phase-5-slicer-panel)
- [Phase 6: Insights](#phase-6-insights)
- [Phase 7: Recommendations](#phase-7-recommendations)

---

## Phase 1: ETL with Power Query

### Step 1: Extraction & Transforming Data

- Extract Data: Get Data → Text/CSV → HR Employee Attrition.csv → Transform Data
- Business Travel column Categorization changed: Non-Travel → Never, Travel_Rarely → Rarely, Travel_Frequently → Frequently
- Age group Categorization column created: Young adult (18-25 age), Adult (26-44 age), Middle-age (45-55 age), Old age (56+ age) about four sequential patterns using Conditional Column.
- Deleted EmployeeCount and Over18 columns as every employee count is 1 and all employees are above 18, so not useful data for analysis.
- EducationLevel Conditional column: Categorized as 1 → High school, 2 → College degree, 3 → Bachelors, 4 → Masters , 5 → Doctorate
- Add “MS-” i.e MeriSKILL prefix to the Employee Number column. Changed data type to Text.
- EnvironmentSatisfaction, JobSatisfaction, RelationshipSatisfaction Columns: Levels were categorized as 1 → 1 - Dissatisfied, 2 → 2 - Neutral, 3 → 3 - Satisfied and 4 → 4 - Highly Satisfied.
- JobInvolvement, WorkLifeBalance Columns: Levels were categorized as 1 → 1 - Poor, 2 → 2 - Fair, 3 → 3 - Good and 4 → 4 - Very Good
- JobLevel Column: Levels were categorized as 1 → Entry, 2 → Junior, 3 → Expert, 4 → Executive and 5 → Senior Executive
- Deleted StandardHours Column since every row has same value of 80, so not useful data for analysis.
- StockOptionLevel Column: Levels are categorized as 0 → No Stock, 1 → Low Value, 2 → Moderate Value and 3 → High Value

---

## Phase 2: Demographics View

Color Pallet: Active Emp → Teal (#00CBC7), Attrited Emp → Maroon (#DC0034) & Attrition Rate → Blue (#41A4FF)

### Step 1: Creating Measures Table

- To collect all report measures in a single place we’ll create a measures table to store all the measures together.
- Data View → Enter Data → Rename as measure.

### Step 2: Key Measures

- `Total Emp = COUNT('Employee Attrition'[EmployeeNumber])`
- `Attrited Emp = CALCULATE([Total Emp], 'Employee Attrition'[Attrition]="Yes")`
- `Active Emp = [Total Emp] - [Attrited Emp]`
- `Male Emp = CALCULATE([Total Emp], 'Employee Attrition'[Gender]="Male")`
- `Female Emp = [Total Emp] - [Male Emp]`
- `Male Attrited Emp = CALCULATE([Attrited Emp], 'Employee Attrition'[Gender]="Male")`
- `Female Attrited Emp = [Attrited Emp] - [Male Attrited Emp]`
- `Male Active Emp = CALCULATE([Active Emp], 'Employee Attrition'[Gender]="Male")`
- `Female Active Emp = [Active Emp] - [Male Active Emp]`
- `Attrition Rate = DIVIDE([Attrited Emp], [Total Emp], 0)`
- `Male Attrition Rate = DIVIDE([Male Attrited Emp], [Male Emp], 0)`
- `Female Attrition Rate = DIVIDE([Female Attrited Emp], [Female Emp], 0)`
- `Avg Age = AVERAGE('Employee Attrition'[Age])`
- `Median Monthly Income = MEDIAN('Employee Attrition'[MonthlyIncome])`
- `Average Monthly Income = AVERAGE('Employee Attrition'[MonthlyIncome])`
- `Avg Tenure = AVERAGE('Employee Attrition'[YearsAtCompany])`

### Step 3: Employee Age Category vs Attrition Trend Visual

- Add a Clustered Bar Chart visual with Age Category field on Y Axis and Male Active Emp, Male Attrited Emp and Male Attrition Rate measures on X Axis.
- Duplicate the Clustered Bar Chart visual with Age Category field on Y Axis and Female Active Emp, Female Attrited Emp and Female Attrition Rate measures on X Axis.
- This divides the Emp stats across 4 categories: Young Adult (18-25 age), Adult (26-44 age), Middle-age Adult (45-55 age), Old-age Adult (56+ age)
- Enable Data Labels and apply Active Emp - Attrited Emp - Attrition Rate Color formatting.
- Create a custom icon blank button toggle for switching the male - female fields visuals using male & female icon buttons using 2 bookmarks: Male Age - MS Trend and Female Age - MS Trend and set the Bookmarks as actions on the buttons.

### Step 4: Employee Gender vs Attrition Trend Visual

- Create a Donut Chart with Male Attrited Emp and Male Active Emp field to display the distribution. Add Male Attrition Rate Card to the visual center for reference.
- Create a Donut Chart with Female Attrited Emp and Female Active Emp field to display the distribution. Add Female Attrition Rate Card to the visual center for reference.
- Add Male - Female icon to denote gender-specific pie charts.
- Enable Data Labels and apply Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 5: Employee Education Level vs Attrition Trend Visual

- Create a Line and Stacked Column Chart with EducationLevel field on X Axis, Active Emp and Attrited Emp measures on the Y Axis and Attrition Rate measure on Line Y Axis.
- Enable Data Labels and apply Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 6: Employee Education Field vs Attrition Trend Visual

- Duplicate the Employee Education Level vs Attrition Trend Visual and replace by Education Field on X Axis.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 7: Employee Marital Status vs Attrition Trend Visual

- Create a Clustered Bar Chart with MaritalStatus field on Y Axis and Male Attrited Emp, Male Active Emp and Male Attrition Rate measures on the X Axis.
- Create a copy Clustered Bar Chart with MaritalStatus field on Y Axis and Female Attrited Emp, Female Active Emp and Female Attrition Rate measures on the X Axis.
- Create a custom icon blank button toggle for switching the male - female fields visuals using male & female icon buttons using 2 bookmarks: Male Employee Marital Status Trend and Female Employee Marital Status Trend and set the Bookmarks as actions on the buttons.

### Step 8: Distance from Home vs Attrition Trend Visual

- Create a Area Plot with DistancefromHome field on X Axis and Active Emp & Attrited Emp measures on the Y Axis and Attrition Rate measure on Secondary Y Axis to display the distribution of the metrics.
- Enable Data Markers and Data Labels only for the Attrition Rate line and match them with line colors.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

---

## Phase 3: Turnover View

### Step 1: View Layout

- Duplicate the Demographic view and delete all the visuals only retaining the Project Elements Group and KPI Custom Bar.

### Step 2: Average Monthly Income in Job Role vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with Dept and JobRole field on X Axis, Average Monthly Income measure on Column Y Axis and Attrition Rate measure on Line Y Axis.
- Add Total Emp, Active Emp and Attrited Emp measures to visual tooltips.
- Set the Sort Axis as Average Monthly Income measure in descending order.
- Enable Data Labels for both Average Monthly Income and Attrition Rate fields.
- Maintain the Attrition Rate Color formatting.

### Step 3: Stock Option Level vs Attrition Trend Visual

- Create a Funnel visual with StockOptionLevel field as Category and Attrition Rate measure as Values. Add Total Emp, Active Emp and Attrited Emp measures to visual tooltips.
- Maintain the Attrition Rate Color formatting.

### Step 4: Job Level vs Attrition Trend Visual

- Duplicate the Stock Option Level vs Attrition Trend Visual and replace by JobLevel field as the Category.

### Step 5: Years at Company vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with YearsAtCompany field in X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Configure a Zoom Slider on the X Axis to enable data range isolation and examination.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

---

## Phase 4: Well being View

### Step 1: View Layout

- Duplicate the Demographic view and delete all the visuals only retaining the Project Elements Group and KPI Custom Bar.

### Step 2: Environment Satisfaction vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with EnvironmentSatisfaction field as X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Set the Sort Axis as EnvironmentSatisfaction  field in ascending direction.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 3: Relationship Satisfaction vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with RelationshipSatisfaction field as X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Set the Sort Axis as RelationshipSatisfaction field in ascending direction.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 4: Job Satisfaction vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with JobSatisfaction field as X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Set the Sort Axis as JobSatisfaction field in ascending direction.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 5: Job Involvement vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with JobInvolvement field as X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Set the Sort Axis as JobInvolvement field in ascending direction.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 6: Business Travel Frequency vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with BusinessTravel field as X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Set the Sort Axis as Attrition Rate measure in ascending direction.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 7: Work-Life Balance vs Attrition Trend Visual

- Create a Line & Clustered Column Chart visual with WorkLifeBalance field as X Axis, Active Emp & Attrited Emp measures in Column Y Axis and Attrition Rate measure in Line Y Axis.
- Set the Sort Axis as WorkLifeBalance  field in ascending direction.
- Maintain the Active Emp - Attrited Emp - Attrition Rate Color formatting.

### Step 8: Percent Salary Hike vs Attrition Trend Visual

- Create a Stacked Area Chart  with PercentSalaryHike field on X Axis, Attrited Emp measure on Y Axis and JobLevel field in Legend parameter.
- Maintain the Attrited Emp - Red color based Color formatting. Vary Red darkness shades for the different Job levels.
- Add Data Marked and Labels and configure a X Axis Zoom Slider to zoom in on PercentSalaryHike value range.

---

## Phase 5: Slicer Panel

### Step 1: Filter Panel

- Create a Panel with same dimensions as the KPIs Panel and add slicers for fields: Department/Job Role/Job Level, Age Category, Gender, Marital Status, Education Field/Education level, Business Travel, Work-Life Balance & Stock Option Level.
- Add 2 custom Buttons for Closing the Panel and Clearing all filters on the page.
- Create 6 Bookmarks, 2 per view: Demographics Filter Panel Closed, Demographics Filter Panel Opened, Turnover Filter Panel Closed, Turnover Filter Panel Opened, Well being Filter Panel Closed, Well being Filter Panel Opened. Bind the corresponding bookmarks with the view-specific Open Filter & Close Filter Panel Buttons.

---

## Phase 6: Insights

### Employee Demographic Patterns:

- The age category of Adults (26 – 44 yrs) is home to the highest workforce, with 526 Active and 100 Attrited employees. However the age category of Young Adults (18 - 25 yrs) despite having 2nd lowest Active employee count are affected with the highest Attrition rate of upto 32.5 %. Perhaps it’s a testament to the wisdom and stability that comes with age.
- Male employees dominate our workforce, constituting 882 out of 1470 individuals. However, Female employees display a lower Attrition rate at 14.8 %, contrasting to higher Male Attrition rate of 17 %.
- Attrition rate seems to be higher among employees with Single Marital status of around 23 - 26 % regardless of the employee gender.
- While Bachelor employees boast the highest Active employees they are also affected with the 2nd highest Attrition rate of 17.3 % trailing just behind High School employees (18.2 %), considering the wide range of opportunities available for them in the job market, which narrows down as employees complete their Doctorate (10.4 %).
- HR (25.9 %), Technical Degree (24.2 %) & Marketing (22 %) field employees have Attrited highest in the company.
- Attrition increases the longer employees have to travel to office with maximum Attrition rate of 42.9 % seen around the 24 Km mark indicating that the majority of employees prefer a close commute, reflecting an aspect of convenience and local integration.

### Employee Turnover Patterns:

- There seems to be a direct correlation between Average Monthly Income (AMI) and Attrition. Managers earn the highest AMI of 17.4K $ and have one of the lowest Attrition rates of 5.5 % while Sales Representative earn the lowest AMI of 2.6K $ and have the highest Attrition rate of 39.8 %. The Attrition rate goes up with decreasing AMI hinting at the interplay between financial satisfaction and employee retention.
- Attrition in general goes down as employees scale the corporate ladder as seen with Entry level & Executive employees showing 26.3 % & 4.7 % Attrition rate.
- As employees spend more time in the company, Attrition rate decreases broadly from 36.4 % at 0 yrs in the company to 6.7 % at 22 yrs in the company post which it displays a contrasting rising trend till 40 yrs in the company when it reaches 100 % mark.

### Employee Well being Patterns:

- Employee Satisfaction trends contradict the Attrition trend as expected. As Employee Satisfaction, Relationship Satisfaction & Job Satisfaction metrics increase, employee attrition decreases from around 23 % to 13.2 %.
- Similar to Employee Satisfaction as Employee Job Involvement increases, the Attrition rate decrease from 33.7 % to just 9 %.
- Attrition goes up from 8 % to 24.9 % as employees need to almost Never Travel to Frequently Travel for business.
- Work-Life Balance metric provides a bell curve trend of Attrition as both Poor & Very Good WLB leads to 24.4 % attrition while Fair & Good WLB leads to 15.5 % attrition on average.
- Increasing Salary Hike % leads to decreasing Attrition among employees across all job levels.

---

## Phase 7: Recommendations

### Employee Retention and Job Satisfaction:

- Conduct comprehensive surveys and engage in direct dialogues with employees to understand the underlying reasons for high attrition (Avg 23 %) due to Job/Environment/Relationship dissatisfaction.
- Implement measures to improve Work-Life Balance, especially for long-standing employees, to reduce Attrition rates upto 14.2 %.
- Recognizing the importance of proximity to work in their daily routines, allow Working from Home (WFH) for employess living with distance of more than 11 Km to reduce travel frequency and drop Attrition rates from 24.9 % to just 8 %.
- Ensure Salary Hike % is at least 15 % or higher to drastically cut down the attrited employees by almost 50%.

### Training and Development:

- Offer training opportunities for Entry-level and Junior employees to bridge any skills gaps, particularly in emerging technologies like Python to complement existing skills in SQL, Excel, Power BI so that they can climb the ladder to be Executive/Sr. Executives dropping the attrition by upto 22 %.

### Financial Incentive Programs:

- Review the Salary compensation packages to ensure they are competitive and aligned with industry standards, particularly for job roles with high attrition rates like Sales Representatives (39.8 %), Sales Executives (17.5 %), Lab Techs (23.9 %) & Human Resources (32.1 %) across the Sales, HR and R&D departments.
- Evaluate the effectiveness of Low & Moderate value Stock Options and other incentive programs to gauge their impact on employee engagement.

### Gender Diversity and Inclusion:

- Develop initiatives to promote gender diversity at all organizational levels and address any disparities in attrition rates between Male (17 %) and Female (14.8 %) employees.
- Establish mentorship programs and support networks to encourage the career growth and retention of Male employees within the organization.

### Data-Driven Decision Making:

- Establish regular feedback mechanisms to allow employees to voice concerns, share suggestions, and provide insights into improving workplace dynamics.
- Develop and refine data-driven models to anticipate attrition trends, enabling proactive strategies to retain valuable talent.

By implementing these recommendations, the organization can foster a positive work environment, improve employee satisfaction and retention, and drive organizational growth and success.

---
