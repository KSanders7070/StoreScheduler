# Store Scheduler

## Overview

**Store Scheduler** is a Python-based tool designed to automate the process of creating employee schedules for retail stores. By using a set of rules and constraints provided via two CSV files—**Store.csv** and **Employees.csv**—the script generates an optimized schedule that meets the store’s staffing requirements while respecting employee availability, preferences, and restrictions.

The scheduler prioritizes specific rules such as minimum hours between shifts, role-specific requirements, and employee preferences for coworkers. It also ensures that special constraints like "Cannot Work With" are considered, and prompts the user for overrides when necessary.

## How It Works

The script processes the data provided in **Store.csv** and **Employees.csv** and generates a basic schedule. It does this by:

1. **Reading and Validating Input Data**: Ensuring that all required fields are present and correctly formatted.
2. **Applying Constraints**: Following store operation hours, employee availability, and other defined rules to allocate shifts.
3. **Generating the Schedule**: Creating a schedule that fits the store’s needs while adhering to employee constraints.

## Input Data Requirements

### Store.csv

The **Store.csv** file defines the store’s operational requirements and rules. It must include the following fields:

- **Available Hours (Min/Max)**: Indicates the minimum and maximum total hours allotted for scheduling employees during the week.
- **Min # Hrs Between Shifts**: Required. Specifies the minimum number of hours that must pass between an employee's shifts.
- **Day of the Week**: Each day’s shift requirements are listed under this heading, with the following rows detailing the shifts and roles needed.
- **Shifts Times**: Specifies the different shifts for each day (e.g., "6 AM – 12 PM").
- **Employee Roles**: Lists the number of employees required for each role (e.g., Cashier, Manager) for each shift.

### Employees.csv

The **Employees.csv** file provides detailed information about each employee, including their availability, role, and specific constraints. This file must include the following columns:

- **Employee Name**: The name of the employee (Required).
- **Titles**: The roles/titles the employee can fill (e.g., Cashier, Manager) (Required).
- **Min Weekly Hours**: The minimum number of hours the employee should be scheduled to work in a week.
- **Max Weekly Hours**: The maximum number of hours the employee can work in a week.
- **Not Available**: Days or times the employee is unavailable to work.
- **Cannot Work With**: Names of other employees that this employee cannot work with.
- **Prefer to Not Work With**: Names of employees that this employee prefers not to work with, but can if necessary.
- **Preferred Coworkers**: Names of employees that this employee prefers to work with.
- **Min # Hrs Between Shifts**: Specifies the minimum number of hours this employee needs between shifts. This value overrides the store's setting if it is larger.

## Usage Instructions

1. Prepare the **Store.csv** and **Employees.csv** files according to the rules outlined above.
2. Run the `Store_Scheduler` script.
3. Review the generated schedule and make any necessary adjustments.

For any issues, refer to the error messages provided by the script or consult the script developer for support.
