# 🧬 MeriSKILL HR Attrition Analysis Project Phase-wise Implementation

---

## Table of Contents
- [Phase 1: ETL with Power Query](#phase-1-etl-with-power-query)
- [Phase 2: Demographics View](#phase-2-demographics-view)
- [Phase 3: Turnover View](#phase-3-turnover-view)

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

