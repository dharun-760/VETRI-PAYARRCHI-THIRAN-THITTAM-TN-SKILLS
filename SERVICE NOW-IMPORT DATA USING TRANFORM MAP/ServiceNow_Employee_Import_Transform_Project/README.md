# ServiceNow Employee Data Import, Transform Map & Analytics

## Team Information

- **Team Number:** 22
- **Team ID:** 6ab8b3e98c7cббе70672ef0b
- **College:** SRM MADURAI COLLEGE FOR ENGINEERING AND TECHNOLOGY


## Project Overview
This project demonstrates an end-to-end ServiceNow data import workflow using Import Sets and Transform Maps. Structured employee data is loaded from a spreadsheet into an Import Set staging table, transformed into a custom Employee Test table, validated, and then presented through reports and a dashboard.

The project also demonstrates **Coalesce** to prevent duplicate employee records and update existing records when the same Employee ID is imported again.

## Core ServiceNow Components

- Custom target table: `u_employee_test`
- Import Set table: `u_employee_import`
- Transform Map: `Sample Spreadsheet Import`
- Dashboard: `Employee Analytics Dashboards`

## Target Fields

| Field | Type |
|---|---|
| Employee ID | String |
| Employee Name | String |
| Email | String |
| Department | String |
| Location | String |

## Transform Map

**Name:** Sample Spreadsheet Import

**Source:** Employee Import (`u_employee_import`)

**Target:** Employee Test (`u_employee_test`)

The source and target fields should be mapped using Auto Map Matching Fields / Mapping Assist.

## Coalesce

Employee ID is intended to act as the unique matching field. When Coalesce is enabled on Employee ID:

- A new Employee ID creates a new record.
- An existing Employee ID updates the existing record.
- Re-importing the same unchanged data can result in ignored rows rather than duplicate records.

## Reports

1. **Employees by Department**
   - Source: Employee Test
   - Type: Pie chart
   - Group by: Department
   - Aggregation: Count

2. **Employees by Location**
   - Source: Employee Test
   - Type: Bar chart
   - Group by: Location
   - Aggregation: Count

3. **Employee List Report**
   - Source: Employee Test
   - Type: List
   - Columns: Employee ID, Employee Name, Email, Department, Location

## Dashboard

**Employee Analytics Dashboards**

The three reports are added to the dashboard so employee distribution and employee records can be viewed from one place.

## Repository Structure

```text
ServiceNow_Employee_Import_Transform_Project/
├── README.md
├── .gitignore
├── LICENSE
├── docs/
│   ├── Original_Project_Instructions.docx
│   ├── PROJECT_DOCUMENTATION.md
│   └── GITHUB_UPLOAD_GUIDE.md
├── data/
│   └── Sample_Employee_Data.csv
├── servicenow/
│   ├── CONFIGURATION_CHECKLIST.md
│   └── FIELD_MAPPING.csv
├── reports/
│   └── REPORT_AND_DASHBOARD_SPECIFICATION.md
└── screenshots/
    └── README.md
```

## Important

The `data/Sample_Employee_Data.csv` file is a **synthetic sample** generated for repository completeness. Replace it with your actual project spreadsheet if you have one.

The `screenshots/` directory is intentionally left ready for your actual ServiceNow screenshots. Screenshots should be added after verifying the corresponding steps in your own instance.

## Source

The detailed workflow in this repository is based on the supplied project instruction document.
