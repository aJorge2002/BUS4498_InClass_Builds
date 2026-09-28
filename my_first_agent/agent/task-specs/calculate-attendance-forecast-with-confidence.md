# Calculate attendance forecast with confidence Task Specification

```yaml
# BASIC INFORMATION
task_id: "T4"
task_name: "Calculate attendance forecast with confidence"
task_owner: "CPVC Event Organizer"

# Agent Inference Configuration
Provider: Groq
Model: "openai/gpt-oss-120b"
Role: Analyze inputs, calculate attendance, and evaluate forecast confidence.
Maximum inference requests per task run: 6
On inference failure or exhausted limits: Record the unresolved data and hand the case to organizer.
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

*Name each planned tool and specify its permitted use. Use verb-object names, such as **`retrieve_records`**, usually matching the task or permitted subtask it supports. Tool name identifies the capability; tool type identifies the proposed implementation. No scripts or working integrations are required.*

### Task-Wide Limits

- **Total task timeout:** 120 seconds for task. Retry or additional inference request does not restart this clock
- **Maximum tool calls:** 6 maximum calls across all tools during task run

### Tool 1

- **Tool name:** `review_forecast_inputs`
- **Input:** Validate event data. Confirm new information
- **Output:** Reviewed inputs for forecast. 
- **Implementation Route:** file operations
- **Integration approach:** direct integration
- **Role in this task:** Support Review forecast inputs 
- **Task timeout:** 120 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** Temporary error prevents the information from being reviewed. Retry once if time and tool calls remain. Do not retry if data is missing or conflicting.
- **On timeout, exhausted retries, or an error that cannot be retried:** Record the issue and hand the case to the CPVC Event Organizer. Do not continue as if the review succeeded.

### Tool 2

- **Tool name:** `calculate_attendance_estimate`
- **Input:** Validate event data. Confirm new information
- **Output:** Estimated attendance, and confidence information
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Use provided data to calculate expected attendance. Help determine how reliable the forecast is.
- **Task timeout:** 120 seconds per task run.
- **Maximum retries:** 1
- **Retry only when:** The calculation fails because of a temporary error or an approved input changes. Retry once if there is still enough time.
- **On timeout, exhausted retries, or an error that cannot be retried:** Record what went wrong. Send case to organizer if forecast cannot be completed.

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
