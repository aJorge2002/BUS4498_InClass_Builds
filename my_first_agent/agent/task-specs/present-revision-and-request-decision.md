# Present revision and request decision Task Specification

## Basic Information

- **Task ID:** T10
- **Task name:** Present revision and request decision
- **Task type:** Reason
- **Task owner:** CPVC Event Organizer

## 1. Task Description

Creates revisions to quantities when recommendations exceed the budget or capacity

## 2. Inputs

### Input 1

- **Input name:** Budget and capacity check
- **Contents and format:** Results for which budget or capacity limits are exceeded and the amount in excess.
- **Source:** T8: Check budget and capacity

### Input 2

- **Input name:** Recommended supply quantities
- **Contents and format:** Current food, drink, and swag quantities
- **Source:** T6: Calculate food, drink, and swag amounts or T11: Organizer revises quantities

- **If a required input is missing or invalid:** Record missing or invalid information and send to Organizer. Do not generate revision options without quantity information.


## 3. Outputs

### Output 1

- **Output name:** Proposed supply revisions
- **Contents and format:** Revised food, drink, and swag quantity plans. This includes how each option addresses the identified budget or capacity issue.
- **Next task or recipient:** CPVC Event Organizer
- **Complete when:** Revision options have been generated and presented to the organizer for review.


## 4. Planned Tools

### Tool 1

- **Tool name:** `generate_revision_options`
- **Input:** Budget and capacity check; ecommended supply quantities
- **Output:** Proposed supply revisions
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Creates revisions to quantities when recommendations exceed the budget or capacity
- **Task timeout:** 60 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** Error results in block for creating revisions. Do not retry if organizer cancels request.
- **On timeout, exhausted retries, or an error that cannot be retried:** [Record status and reason for error. Send information to organizer


