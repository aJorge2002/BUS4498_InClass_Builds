# Organizer revises quantities Task Specification

## Basic Information

- **Task ID:** T11
- **Task name:** Organizer revises quantities
- **Task type:** Decide
- **Task owner:** CPVC Event Organizer


## 1. Task Description

Allows organizer to manually make revisions to the final results

## 2. Inputs

### Input 1

- **Input name:** Organizer decisions
- **Contents and format:** Decisions conducted by organizer to manually change any information
- **Source:** T10: Present revision and request decision

### Input 2

- **Input name:** Current quantities
- **Contents and format:** The current food, drink, and swag quantities organizer to review
- **Source:** T10: Present revision and request decision

- **If a required input is missing or invalid:** Return the case to T10 or event organizer

## 3. Outputs

### Output 1

- **Output name:** Revised quantities
- **Contents and format:** Manually revised qantities approved by event organizer
- **Next task or recipient:** T8: Check budget and capacity
- **Complete when:** Organizer revises information and gives confirmation to move on 

## 4. Planned Tools

### Tool 1

- **Tool name:** `record_revised_quantities`
- **Input:** Organizer decisions; Current quantities
- **Output:** Revised quantities
- **Implementation Route:** file operations
- **Integration approach:** direct integration
- **Role in this task:** Allows organizer to manually make revisions to the final results
- **Task timeout:** 1 business day after the revision request is presented to the organizer.
- **Maximum retries:** N/A
- **Retry only when:** N/A
- **On timeout, exhausted retries, or an error that cannot be retried:** Return to the case organizer. Do not make any changes or move to T8



