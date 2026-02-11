# SmartReplenish – Repository

This repository contains the Requirements Engineering (RE) deliverables for ValuPrice Pte Ltd’s Android Grocery Management App, **SmartReplenish**.  

## Quick Links (Latest)
- **Analysing (BCIC) Debriefing Report:** `02_Analysis/<FILE_NAME>.pdf`
- **Project Specification / SRS:** `01_Requirements/<FILE_NAME>.pdf`
- **iRTM (Traceability):** `04_Traceability/<FILE_NAME>.xlsx` (or `.pdf`)
- **UML / Diagrams:** `03_Models/`
- **Change Log / Open Issues:** `02_Analysis/Open_Issues.md`

## Repository Structure (CRaM – Contextually Relevant & Meaningful)
- `00_README/` – this guide and navigation
- `01_Requirements/` – SRS / Project Specification (baseline + revisions)
- `02_Analysis/` – Analysing stage outputs (BCIC report, findings, open issues)
- `03_Models/` – UML/PlantUML diagrams (use case, class, sequence), domain/data models
- `04_Traceability/` – iRTM mapping PS ↔ SRS ↔ (planned) tests
- `05_Solution_Design/` – UI flow sketches, architecture overview, interface assumptions (no code)
- `06_Testing_Evidence/` – planned test cases + acceptance criteria mapped to FR/NFR (if applicable)

## Requirement ID Conventions
- Functional: `FR-xx`
- Non-functional: `NFR-xx`
- Use cases: `UC-xx`
- Open issues: `OI-xx`
- Change requests: `CR-xx`

Artifacts (diagrams, iRTM rows, planned tests) should reference these IDs for traceability.

## Status (at time of latest update)
- Analysing stage: Completed / In review (choose one)
- SRS baseline: Draft v0.x / Baseline v1.0 (choose one)
- Key dependencies: External item metadata, cloud/network availability, privacy/security constraints
- Next step: Finalise open issues → baseline SRS → update iRTM

## How to Review (Recommended Order)
1. Read `02_Analysis/...` to understand what was done and key findings.
2. Read `01_Requirements/...` for the approved baseline requirements.
3. Check `04_Traceability/...` to see mapping across artifacts.
4. Review `03_Models/` for design-level clarity and system interactions.

## Ownership / Contacts
- Vendor team: 1376T
- Date of last update: 11/2/2026
