# Capture new information or revised assumptions Task Specification

## Basic Information

- **Task ID:** T7
- **Task name:** Capture new information or revised assumptions
- **Task type:** Remember
- **Task owner:** CPVC Event Organizer

## 1. Task Description

Records new information or revised assumptions provided by the organizer. Information is then sent back to T4 to reconstruct attendance forecast.

## 2. Inputs

### Input 1

- **Input name:** Revised organizer information 
- **Contents and format:** New, correct, or revised information provided by the organizer 
- **Source:** T5: Present the forecast and capture the organizer's decision

- **If a required input is missing or invalid:** Record missing or invalid information and notify case organizer. Do not return invalid data back to T4.

## 3. Outputs

### Output 1

- **Output name:** New information and assumptions
- **Contents and format:** Record containing new information and revised assumptions 
- **Next task or recipient:** T4: Calculate attendance forecast with confidence
- **Complete when:** Revised information has been recorded. Is available in T4 for forecasting reattempt 


## 4. Planned Tools

### Tool 1

- **Tool name:** `capture_revised_assumptions`
- **Input:** Revised organizer information 
- **Output:** New information and assumptions
- **Implementation Route:** file operations
- **Integration approach:** direct integration
- **Role in this task:** Records new information or revised assumptions provided by the organizer. Information is then sent back to T4 to reconstruct attendance forecast.
- **Task timeout:** 1 business day for the organizer to provide revised information.
- **Maximum retries:** 1
- **Retry only when:** Error prevents organizer's input from being saved
- **On timeout, exhausted retries, or an error that cannot be retried:** Record unresolved status and hand case back to the organizer. Do not return to T4



