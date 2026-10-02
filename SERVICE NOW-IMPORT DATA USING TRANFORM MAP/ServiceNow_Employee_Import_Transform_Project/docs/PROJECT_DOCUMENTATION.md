# Project Documentation

## Team Information

- **Team Number:** 22
- **Team ID:** 6ab8b3e98c7cббе70672ef0b
- **College:** SRM MADURAI COLLEGE FOR ENGINEERING AND TECHNOLOGY

## 1. Objective

To implement a ServiceNow employee-data migration workflow using Import Sets and Transform Maps, followed by duplicate prevention with Coalesce and visualization using Reports and a Dashboard.

## 2. Workflow

```text
Excel / Spreadsheet
        |
        v
Load Data
        |
        v
Import Set Table
(u_employee_import)
        |
        v
Transform Map
(Sample Spreadsheet Import)
        |
        |-- Field Mapping
        |-- Coalesce on Employee ID
        |
        v
Employee Test Table
(u_employee_test)
        |
        +------------------+
        |                  |
        v                  v
     Reports           Validation
        |
        v
Employee Analytics Dashboards
```

## 3. Custom Table

Create:

- Label: Employee Test
- Name: `u_employee_test`

Fields:

- Employee ID — String
- Employee Name — String
- Email — String
- Department — String
- Location — String

## 4. Import Set

Create/load:

- Label: Employee Import
- Name: `u_employee_import`

The spreadsheet is loaded into the Import Set table as staging data.

## 5. Transform Map

Create:

- Name: Sample Spreadsheet Import
- Source Table: Employee Import
- Target Table: Employee Test

Use Auto Map Matching Fields or Mapping Assist.

### Field Mapping

| Source | Target |
|---|---|
| Employee ID | Employee ID |
| Employee Name | Employee Name |
| Email | Email |
| Department | Department |
| Location | Location |

## 6. Coalesce

Enable Coalesce on Employee ID in the Field Maps section.

This allows repeated imports to match an existing employee by Employee ID instead of creating a duplicate record.

## 7. Validation Scenarios

### Scenario A — New records

Import previously unseen Employee IDs.

Expected result: records are inserted.

### Scenario B — Existing records

Import existing Employee IDs with changed name/email values.

Expected result: existing records are updated when Coalesce is configured.

### Scenario C — Same data again

Import the same dataset without changes.

Expected result: the records can be ignored rather than duplicated.

## 8. Reports

### Employees by Department

- Table: Employee Test
- Chart: Pie
- Group By: Department
- Aggregation: Count

### Employees by Location

- Table: Employee Test
- Chart: Bar
- Group By: Location
- Aggregation: Count

### Employee List Report

- Table: Employee Test
- Type: List
- Columns:
  - Employee ID
  - Employee Name
  - Email
  - Department
  - Location

## 9. Dashboard

Dashboard name:

`Employee Analytics Dashboards`

Add all three reports to the dashboard.

## 10. Expected Outcome

The completed workflow provides:

- Spreadsheet-to-ServiceNow data loading
- Staging through Import Sets
- Field mapping through Transform Maps
- Duplicate prevention/update handling through Coalesce
- Employee data validation
- Department and location analytics
- Centralized dashboard visualization

## 11. Evidence to Add

Add screenshots from your own ServiceNow instance for:

1. Employee Test table creation
2. Employee Test fields
3. Load Data / Import Set
4. Transform Map
5. Field Maps
6. Coalesce enabled
7. Transform execution
8. Transform history
9. Employee Test records
10. Employees by Department report
11. Employees by Location report
12. Employee List Report
13. Dashboard
14. Dashboard containing all three reports
