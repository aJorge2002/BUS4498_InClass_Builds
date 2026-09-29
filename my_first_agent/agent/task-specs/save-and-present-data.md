# Save and present data Task Specification

## Basic Information

- **Task ID:** T9
- **Task name:** Save and present data
- **Task type:** Act
- **Task owner:** CPVC Event Organizer

## 1. Task Description

Saves planning results and presents final report to CPVC Event organizer

## 2. Inputs

### Input 1

- **Input name:** Budget and capacity check result
- **Contents and format:** Results confirming that the recommended food, drink, and swag quantities are within the approved budget and capacity limits.
- **Source:** T8: Check budget and capacity

### Input 2

- **Input name:** Final results
- **Contents and format:** Approved attendance forecast and final food, drink, and swag quantities
- **Source:** T4: Calculate attendance forecast with confidence and T6: Calculate food, drink, and swag amounts, including any approved revisions from T11.

- **If a required input is missing or invalid:** Record information and send to organizer. Do not mark as complete

## 3. Outputs

### Output 1

- **Output name:** Planning report dashboard
- **Contents and format:** An organized dashboard with all of the results. 
- **Next task or recipient:** CPVC Event Organizer
- **Complete when:** The organizer can access the completed dashboard and the workflow records the report as presented.

### Output 1

- **Output name:** Planning report xlsx
- **Contents and format:** Organized excel file with all data
- **Next task or recipient:** CPVC Event Organizer
- **Complete when:** The organizer can access the completed report and the workflow records the report as presented.

## 4. Planned Tools

*Use a verb-object name, usually matching the task: Check Completeness can use `check_completeness`. List every tool separately and use the same name and type wherever the tool appears in the project.*

### Tool 1

- **Tool name:** `save_present_report`
- **Input:** Budget and capacity check result; Final results
- **Output:** Planning report dashboard; Planning report xlsx
- **Implementation Route:** file operations
- **Integration approach:** direct integration
- **Role in this task:** Saves planning results and presents final report to CPVC Event organizer
- **Task timeout:** 60 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** Excel file or dashboard can not be generated
- **On timeout, exhausted retries, or an error that cannot be retried:** Diagnose reason for fail and send information to organizer. Do not continue the workflow.




