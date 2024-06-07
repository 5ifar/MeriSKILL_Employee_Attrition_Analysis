# 🧬 MeriSKILL HR Attrition Analysis Project Phase-wise Implementation

---

## Table of Contents
- [Phase 1: ETL with Power Query](#phase-1-etl-with-power-query)
- [Phase 2: Demographics View](#phase-2-demographics-view)

---

## Phase 1: ETL with Power Query

### Step 1: Extraction & Transforming Data:

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

### Step 1: Creating Measures Table:

- To collect all report measures in a single place we’ll create a measures table to store all the measures together.
- Data View → Enter Data → Rename as measure.

### Step 2: Key Measures:

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
