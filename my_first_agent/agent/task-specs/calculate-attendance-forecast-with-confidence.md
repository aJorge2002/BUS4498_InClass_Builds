# Calculate attendance forecast with confidence Task Specification

```yaml
# BASIC INFORMATION
task_id: "T4"
task_name: "Calculate attendance forecast with confidence"
task_owner: "CPVC Event Organizer"
```

## 1. Task Goal

- **Objective:** The business result produced by this task is a supported attendance forecast for the organizer to decide whether to continue planning food, drinks, and swag or review the forecast assumptions before moving forward.

## 2. Inbound Inputs

### Input 1

- **Input name:** Validated registration and event data
- **What it contains:** Agent receives registration totals and event information needed to estimate attendance, provided as a structured record.
- **Source:** T2: Validate registration and event data

### Input 2

- **Input name:** Revised assumptions or new information
- **What it contains:** Updated or fallback assumptions from the organizer, provided as a written decision record. 
- **Source:** T7: Capture new information or revised assumptions

## 3. Tool Permissions and Boundaries

## 4. How the Agent Should Reason

### Permitted Subtask 1

- **Subtask name:** Review forecast inputs
- **Subtask description:** Examine validated registration information and identify inconsistent data that could affect the forecast.
- **Subtask boundary:** Can review information, but not modify the source data.
- **Retry limits:** One additional attempt is allowed if revised information becomes available.

### Permitted Subtask 2

- **Subtask name:** Select forecast approach
- **Subtask description:** Choose an appropriate forecasting approach based on the amount and quality of the available information.
- **Subtask boundary:** Can use provided information only. 
- **Retry limits:** One additional attempt is allowed if the first approach cannot produce a supported forecast.

### Permitted Subtask 3

- **Subtask name:** Calculate attendance estimate
- **Subtask description:** Produce an estimated attendance result and record the assumptions supporting the estimate.
- **Subtask boundary:** Execute attendance calculation only. 
- **Retry limits:** One additional calculation is allowed when an approved input or assumption changes.

### Permitted Subtask 4

- **Subtask name:** Assess forecast confidence
- **Subtask description:** Examine the available evidence and uncertainty to evaluate forecast confidence. 
- **Subtask boundary:** The agent may explain uncertainty but may not approve low-confidence assumptions or choose a fallback for the organizer.
- **Retry limits:** One additional assessment is allowed after the forecast or its inputs are revised.

- **Decision guidance:** After each subtask, use its findings to select the permitted subtask most likely to resolve the most important remaining uncertainty. Do not follow a fixed sequence. If no permitted subtask can make useful progress, stop and hand the case to a person.

## 5. When to Stop or Hand Off to a Human

- **Stop successfully when:** An attendance forecast has been calculated from valid inputs, its assumptions have been recorded, and the available evidence supports its confidence level.
- **Hand off early when:** Important data is missing, data conflicts occur, repeated attempts do not resolve the issue, or no permitted forecasting approach can produce a supported result.
- **Hand off to:** CPVC Event Organizer

Stop when a successful result or handoff condition is reached. While waiting for organizer review, take no further action.

## 6. Outbound Deliverable

- **Status:** Completed or escalated to the organizer.
- **Result or recommendation:** The attendance forecast and confidence level. If the task cannot produce a supported forecast, record the result as undetermined.
- **Evidence summary:** The main registration data, event information, and approved assumptions supporting the result.
- **Subtasks performed:** The permitted subtasks completed, including any repeated attempts.
- **Unresolved issues:** Any missing, conflicting, or uncertain information; use none if no unresolved issues remain.
- **Handoff note:** Explain why the task stopped and what the organizer needs to review. Use "Not applicable" when the task is completed successfully.
- **Next task or recipient:** Send the completed forecast and confidence result to D2. Unresolved cases go to the CPVC Event Organizer.
