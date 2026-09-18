# Workflow of Tasks

*Replace all bracketed prompts with information specific to your proposed system. Delete instructional text that does not belong in your final specification. Add or remove task sections as needed. Every task shown in the general workflow must have a corresponding task specification below.*

## 1. Workflow Overview
### 1.1 Workflow Goal
This workflow supports the system goal defined in `my_first_agent/README.md`.

### 1.2 Workflow Trigger

Workflow begins when all data is registered and attendance is requested.

### 1.3 Completion Condition at Runtime

The system knows condition is completed when predictions are presented. This includes attendance and any additional resources in which may be required. 

### 1.4 General Workflow

HackTrack gathers the necessary information when registration is updated. This consists of current registrations,  days remaining until the event, past attendance records, and any RSVPs received. After reviewing, there is a forecast on how many participants are predicted to attend.

HackTrack also considers limits set by the organizer. HackTrack checks and notifies the organizer. In cases where there isn’t enough historical data or the forecast is uncertain, it advises the organizer to review data. If supplies exceed the budget or capacity, the organizer is also notified. Once everything is confirmed, the report is saved.

### 1.5 Workflow Diagram

```mermaid
flowchart TD
    Trigger["Workflow Trigger: All data is registered and attendance is requested"] --> T1["T1: Gather registration information"]
    T1 --> T2["T2: Review current registrations, days remaining, attendance records, and RSVPs"]
    T2 --> T3["T3: Forecast participant attendance"]
    T3 --> T4["T4: Check organizer limits"]
    T4 --> D1{"D1: Is historical data sufficient and the forecast certain?"}
    D1 -- "Yes" --> D2{"D2: Do supplies exceed the budget or capacity?"}
    D1 -- "No" --> T5["T5: Advise organizer to review data"]
    T5 --> T6["T6: Review forecast data"]
    T6 --> T3
    D2 -- "Yes" --> T7["T7: Notify organizer about supply limits"]
    D2 -- "No" --> D3{"D3: Is everything confirmed?"}
    T7 --> D3
    D3 -- "No" --> T6
    D3 -- "Yes" --> T8["T8: Save forecast report"]
    T8 --> T9["T9: Present attendance and required resource predictions"]
    T9 --> Complete["Completion: Present attendance and any required resource predictions"]
