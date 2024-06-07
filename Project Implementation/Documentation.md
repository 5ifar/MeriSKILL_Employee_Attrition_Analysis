# 🧬 MeriSKILL HR Attrition Analysis Project Phase-wise Implementation

---

## Table of Contents
- [Phase 1: ETL with Power Query](#phase-1-etl-with-power-query)

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
