# Block run with an error message Task Specification

## Basic Information

- **Task ID:** T3
- **Task name:** Block run with an error message
- **Task type:** Act
- **Task owner:** CPVC Event Organizer

## 1. Task Description

Stops workflow when registration or validation fails. Records reason for failure and displays error message accompanied with reason for faliure

## 2. Inputs

### Input 1

- **Input name:** Record of validation faliure
- **Contents and format:** Record diagnosing the reason of faliure
- **Source:** [T2: Validate registration and event data

- **If a required input is missing or invalid:** Communicate that failure could not be identified. Do not continue with the workflow 

## 3. Outputs

### Output 1

- **Output name:** Blocked status with error message
- **Contents and format:** Status report indicating that workflow has stopped. Includes reason for the stop.
- **Next task or recipient:** CPVC Event Organizer
- **Complete when:** Error message is displayed with diagnosis

## 4. Planned Tools


### Tool 1

- **Tool name:** blocked_status_with_error_message
- **Input:** Record of validation faliure
- **Output:** Blocked run status and error message
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Stop workflow and display error message using information from T2
- **Task timeout:** 60 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** Error message cannot be recorded
- **On timeout, exhausted retries, or an error that cannot be retried:** Record block status and send information to event organizer. Do not continue the workflow.



