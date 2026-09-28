# Workflow of Tasks

*Replace all bracketed prompts with information specific to your proposed system. Delete instructional text that does not belong in your final specification. Add or remove task sections as needed. Every task shown in the general workflow must have a corresponding task specification below.*

## 1. Workflow Overview
### 1.1 Workflow Goal
This workflow supports the system goal defined in `my_first_agent/README.md`.

### 1.2 Workflow Trigger

Workflow begins when all data is registered and attendance is requested.

### 1.3 Completion Condition at Runtime

A run is complete when HackTrack has either saved or presented a dated report after the organizer has approved the forecast assumptions and any supply-planning decision, or blocked the run with validation errors because required inputs are invalid. If revised assumptions or quantities are needed, the run remains in progress until they are captured, recalculated or rechecked, and approved. 

### 1.4 General Workflow

On each run, HackTrack retrieves the approved registration and event inputs and validates the data. If the inputs are invalid, HackTrack blocks the run and reports the validation errors. If the inputs are valid, HackTrack calculates the attendance forecast and confidence level.
If forecast confidence is acceptable, HackTrack converts the forecast into recommended food, drink, and swag quantities. If confidence is low, HackTrack presents the forecast and assumptions to the organizer for review. The organizer either approves the assumptions or fallback decision, or provides revised assumptions or new information. HackTrack captures the revisions and recalculates the forecast before continuing.
HackTrack checks the recommended supply quantities against the available budget and venue capacity. If the quantities are within limits, HackTrack saves and presents the dated report. If the quantities exceed a limit, HackTrack presents quantity-revision options. The organizer either approves revised quantities or records a planning decision, or revises the quantities. Revised quantities are checked again until they are acceptable or the organizer approves a planning decision. The final report includes the forecast, assumptions, supply quantities, budget and capacity checks, planning decisions, and warnings.

### 1.5 Workflow Diagram

```mermaid
flowchart TD
    S["Organizer submits event and registration inputs"] --> T1["Retrieve inputs"]
    T1 --> T2["Validate registration/event data"]
    T2 --> D1{"Are the inputs valid?"}

    D1 -->|No| T3["Block run with error message"]
    T3 --> E1(["Run blocked. Please validate inputs"])

    D1 -->|Yes| T4["Calculate attendance with confidence"]
    T4 --> D2{"Forecast confidence acceptable?"}

    D2 -->|Yes| T6["Calculate drink, food, swag amounts"]
    D2 -->|No| T5["Present the forecast and capture the organizer's decision"]

    T5 --> D3{"Organizer approves?"}
    D3 -->|Yes| T6
    D3 -->|No| T7["Capture new information"]
    T7 --> T4

    T6 --> T8["Check budget and capacity"]
    T8 --> D4{"Is everything within its necessary limits?"}

    D4 -->|Yes| T9["Present data"]
    T9 --> E2(["Report delivered sucessfully"])

    D4 -->|No| T10["Present revision and request decision"]
    T10 --> D5{"Does the organizer approve quantities or planning decision?"}

    D5 -->|Yes| T9
    D5 -->|No| T11["Revise quantities"]
    T11 --> T8
