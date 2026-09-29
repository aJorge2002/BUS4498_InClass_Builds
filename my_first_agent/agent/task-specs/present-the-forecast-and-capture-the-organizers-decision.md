# Present the forecast and capture the organizer's decision Task Specification

## Basic Information

- **Task ID:** T5
- **Task name:** Present the forecast and capture the organizer's decision
- **Task type:** Act
- **Task owner:** CPVC Event Organizer

## 1. Task Description

Presents attendance forecast, uncertainty, and confidence level to organizer. Task does not make decisions, instead, allows organizer to make final call on contnuing.

## 2. Inputs

### Input 1

- **Input name:** Forecast with confidence result
- **Contents and format:** Estimated attendance, summary, confidence level, and uncertainty. Provided as a visual dashboard. 
- **Source:** T4: Calculate attendance forecast with confidence

- **If a required input is missing or invalid:** Record missing information and return to T4

## 3. Outputs

### Output 1

- **Output name:** Organizer forecast decision
- **Contents and format:** Request for organizer to accept or decline the forecast
- **Next task or recipient:** T6: Calculate food, drink, and swag amounts if the organizer accepts the forecast; T7: Capture new information or revised assumptions if the organizer requests revision.
- **Complete when:** Organizer's decision has been received and appropriate next task is chosen


## 4. Planned Tools


### Tool 1

- **Tool name:** `present_forecast_capture_decision`
- **Input:** Forecast with confidence result
- **Output:** Organizer forecast decision
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Present forecast to organizer and record response
- **Task timeout:** 1 business day for the organizer to provide a response.
- **Maximum retries:** 1
- **Retry only when:** Forecast cannot be displayed properly or missing information is skewing forecast 
- **On timeout, exhausted retries, or an error that cannot be retried:** Do not continue to T6. Notify organizer.


