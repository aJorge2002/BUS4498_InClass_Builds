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

<img width="500" height="952" alt="image" src="https://github.com/user-attachments/assets/20f58adf-b098-4160-8f3f-57c14e7e99a4" />

```mermaid
flowchart TD
    S([Organizer requests forecast])
    T1["T1: Retrieve approved inputs"]
    T2["T2: Validate input data"]
    D1{"D1: Are inputs valid?"}
    T3["T3: Report data problems"]
    E1([Run blocked])
    T4["T4: Calculate attendance forecast"]
    D2{"D2: Is confidence acceptable?"}
    T5["T5: Review forecast assumptions"]
    T6["T6: Generate supply recommendations"]
    D3{"D3: Within budget and capacity?"}
    T7["T7: Adjust recommended quantities"]
    T8["T8: Save and present report"]
    E2([Run complete])

    S --> T1
    T1 --> T2
    T2 --> D1
    D1 -- No --> T3
    T3 --> E1
    D1 -- Yes --> T4
    T4 --> D2
    D2 -- No --> T5
    T5 --> T6
    D2 -- Yes --> T6
    T6 --> D3
    D3 -- No --> T7
    T7 --> T8
    D3 -- Yes --> T8
    T8 --> E2
