# Calculate food, drink, and swag amounts Task Specification

## Basic Information

- **Task ID:** T6
- **Task name:** Calculate food, drink, and swag amounts
- **Task type:** Reason
- **Task owner:** CPVC Event Organizer
## 1. Task Description

Creates recommendations for food, drink, and swag amounts depending on forecast results

## 2. Inputs

### Input 1

- **Input name:** Approved attendance forecast
- **Contents and format:** Forecast and anyadditional data required to make food, drink, and swag calculations
- **Source:** T4: Calculate attendance forecast with confidence or T5: Present the forecast and capture the organizer's decision

- **If a required input is missing or invalid:** Record and display missing or invalid data. Do not make food, drink, or swag calculations.

## 3. Outputs

### Output 1

- **Output name:** Calculated recommendations for food, drink, and swag
- **Contents and format:** Calculated quantities for food, drinks, and swag
- **Next task or recipient:** T8: Check budget and capacity
- **Complete when:** Recommended quantities for food, drink, and swag are calculated

## 4. Planned Tools


### Tool 1

- **Tool name:** `calculate_supply_quantities`
- **Input:** Approved attendance forecast
- **Output:** Calculated recommendations for food, drink, and swag
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Return recommended amounts of food, drink, and swag depending on forecast results
- **Task timeout:** 60 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** Error prevents quantities from being produced. 
- **On timeout, exhausted retries, or an error that cannot be retried:** Record calculation error and present information to organizer. Do not move forward in workflow.




