# Check budget and capacity Task Specification

## Basic Information

- **Task ID:** T8
- **Task name:** Check budget and capacity
- **Task type:** Verify
- **Task owner:** CPVC Event Organizer

## 1. Task Description

Compares recommended food, drink, and swag quantities against the approved budget and capacity limits. Does revise quantities, instead, determines if recommendations are inside of event limits.

## 2. Inputs

### Input 1

- **Input name:** Recommended quantities
- **Contents and format:** Calculated quantities for food, drink, and swag
- **Source:** T6: Calculate food, drink, and swag amounts or T11: Organizer revises quantities

### Input 2

- **Input name:** Capacity and budget limits
- **Contents and format:** Approved capacity and budget limits
- **Source:** CPVC Event Organizer


- **If a required input is missing or invalid:** Record missing or invalid data and send to organizer. Do not continue in workflow.

## 3. Outputs

### Output 1

- **Output name:** Budget and capacity verification
- **Contents and format:** Structured record determining if quantities are within approved budget and capacity
- **Next task or recipient:**  T9: Save and present data if the quantities are within limits; T10: Present revision and request decision if the quantities exceed limits.
- **Complete when:** Quantities have been compared against all budget and capacity limits

## 4. Planned Tools

### Tool 1

- **Tool name:** `check_budget_capacity`
- **Input:** Capacity and budget limits; Recommended quantities
- **Output:** Budget and capacity verification
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Compares recommended food, drink, and swag quantities against the approved budget and capacity limits. Does revise quantities, instead, determines if recommendations are inside of event limits.
- **Task timeout:** 60 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** Error prevents comparison from being completed. Do not retry because limit is exceeded
- **On timeout, exhausted retries, or an error that cannot be retried:** Record failed comparison and hand information over to organizer. Do not continue the workflow.


