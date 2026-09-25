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
    S["Trigger: Organizer uploads approved inputs and requests forecast"] --> T1["Retrieve approved inputs"]
    T1 --> T2["Validate registration and event data"]
    T2 --> D1{"Inputs valid?"}
    D1 -- "No" --> T3["Block run with validation errors"]
    T3 --> E1(["Completion: Run blocked"])
    D1 -- "Yes" --> T4["Calculate attendance forecast and confidence"]
    T4 --> D2{"Forecast confidence acceptable?"}
    D2 -- "Yes" --> T6["Calculate food, drink, and swag quantities"]
    D2 -- "No" --> T5["Present forecast and assumptions"]
    T5 --> D3{"Organizer approves assumptions or fallback?"}
    D3 -- "Yes" --> T6
    D3 -- "No" --> T7["Capture revised assumptions or new information"]
    T7 --> T4
    T6 --> T8["Check budget and venue capacity"]
    T8 --> D4{"Supplies within limits?"}
    D4 -- "Yes" --> T9["Save and present dated report"]
    T9 --> E2(["Completion: Report delivered"])
    D4 -- "No" --> T10["Present quantity revision options"]
    T10 --> D5{"Organizer approves quantities or planning decision?"}
    D5 -- "Yes" --> T9
    D5 -- "No" --> T11["Revise supply quantities"]
    T11 --> T8
```
