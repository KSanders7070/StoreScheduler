# Store Scheduler

## Overview

**Store Scheduler** is a Python-based tool designed to automate the process of creating employee schedules for retail stores. By using a set of rules and constraints provided via two CSV files—**Store.csv** and **Employees.csv**—the script generates an optimized schedule that meets the store’s staffing requirements while respecting employee availability, preferences, and restrictions.

The scheduler prioritizes specific rules such as minimum hours between shifts, title-specific requirements, and employee preferences for coworkers. It also ensures that special constraints like "Cannot Work With" are considered, and prompts the user for overrides when necessary.

## How It Works

The script processes the data provided in **Store.csv** and **Employees.csv** and generates a basic schedule. It does this by:

1. **Reading and Validating Input Data**: Ensuring that all required fields are present and correctly formatted.
2. **Applying Constraints**: Following store operation hours, employee availability, and other defined rules to allocate shifts.
3. **Generating the Schedule**: Creating a schedule that fits the store’s needs while adhering to employee constraints.

## Input Data Requirements

### Store.csv

The **Store.csv** file defines the store’s operational requirements and rules. It must include the following fields:

- **Available Hours (Min/Max)**: Indicates the minimum and maximum total hours allotted for scheduling employees during the week. If no minimum is specified, leave the first cell blank.
  - **Format**: An integer
  - **Example**: `300`

- **Min # Hrs Between Shifts**: Required. Specifies the minimum number of hours that must pass between an employee's shifts.
  - **Format**: A single integer
  - **Example**: `8`

- **Day of the Week**: Each day’s shift requirements are listed under this heading, with the following rows detailing the shifts and titles needed.
  - **Format**: Day name as text
  - **Example**: `Sunday`

- **Shifts Times**: Specifies the different shifts for each day.
  - **Format**: `Time, space, AM or PM, space, dash, space time, space, AM or PM.`
  - **Example**: `6 AM – 12 PM`

- **Employee Titles**: Lists the number of employees required for each title (e.g., Cashier, Manager) for each shift.
  - **Column "A" Format**: Title as text
    - **Column "A" Example**: `Stocker`
  - **Column "B+" Format**: Integer in the row for the desired title.
    - **Column "B+" Example**: `4`

### Employees.csv

The **Employees.csv** file provides detailed information about each employee, including their availability, title, and specific constraints. This file must include the following columns:

- **Employee Name**: The name of the employee (Required).
  - **Format**: Full name as text
  - **Example**: `John Doe`

- **Titles**: The roles/titles the employee can fill (e.g., Cashier, Manager) (Required).
  - **Format**: Comma-separated list if multiple
  - **Example**: `Cashier`
  - **Example 2**: `Cashier, Stocker, Customer Service Manager`

- **Min Weekly Hours**: The minimum number of hours the employee should be scheduled to work in a week.
  - **Format**: Integer
  - **Example**: `20`

- **Max Weekly Hours**: The maximum number of hours the employee can work in a week.
  - **Format**: Integer
  - **Example**: `35`

- **Not Available**: Days or times the employee is unavailable to work.
  - **Format**: List of days and times beginning with the three-character day abbreviation, space, time in 12-hour format, space, AM or PM, dash, space, time in 12-hour format, space, AM or PM. If multiple days, separate with a comma.
  - **Example**: `Mon 2 PM – 6 PM`
  - **Example 2**: `Mon 2 PM – 6 PM, Fri 6 PM – 12 AM`

- **Cannot Work With**: Names of other employees that this employee cannot work with. Listed employees must be an employee found in the same file.
  - **Format**: Full text name. If multiple, separate with commas.
  - **Example**: `Jane Smith`
  - **Example 2**: `Jane Smith, Bob Lee`

- **Prefer to Not Work With**: Names of other employees that this employee prefers not to work with. Listed employees must be an employee found in the same file.
  - **Format**: Full text name. If multiple, separate with commas.
  - **Example**: `Jane Smith`
  - **Example 2**: `Jane Smith, Bob Lee`

- **Preferred Coworkers**: Names of other employees that this employee prefers to work with. Listed employees must be an employee found in the same file.
  - **Format**: Full text name. If multiple, separate with commas.
  - **Example**: `Jane Smith`
  - **Example 2**: `Jane Smith, Bob Lee`

- **Min # Hrs Between Shifts**: Specifies the minimum number of hours this employee needs between shifts. This value overrides the store's setting if it is larger.
  - **Format**: Integer
  - **Example**: `8`

## Usage Instructions

1. Prepare the **Store.csv** and **Employees.csv** files according to the rules outlined above.
2. Run the `Store_Scheduler` script.
3. Review the generated schedule and make any necessary adjustments.

For any issues, refer to the error messages provided by the script or consult the script developer for support.
