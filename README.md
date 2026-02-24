# SmartReplenish – Repository

This repository contains the Requirements Engineering (RE) deliverables for ValuPrice Pte Ltd’s Android Grocery Management App, **SmartReplenish**.  

## Quick Links (Latest)
- **Analysing (BCIC) Debriefing Report:** [PrjTm_P2_1376T_PD108_Analysis_Report.pdf](02_Analysis/PrjTm_P2_1376T_PD108_Analysis_Report.pdf)
- **Software Requirements Specification (SRS):** `01_Requirements/<FILE_NAME>.pdf`
- **iRTM (Traceability):** `04_Traceability/<FILE_NAME>.xlsx` (or `.pdf`)
- **UML / Diagrams:** `03_Models/`
- **Change Log / Open Issues:** `02_Analysis/Open_Issues.md`

## Repository Structure (CRaM – Contextually Relevant & Meaningful)
- `01_Requirements/` – SRS / Project Specification (baseline + revisions)
- `02_Analysis/` – Analysing stage outputs (BCIC report, findings, open issues)
- `03_Models/` – UML/PlantUML diagrams (use case, class, sequence), domain/data models
- `04_Traceability/` – iRTM mapping PS ↔ SRS ↔ (planned) tests
- `05_Solution_Design/` – UI flow sketches, architecture overview, interface assumptions (no code)
- `06_Testing_Evidence/` – planned test cases + acceptance criteria mapped to FR/NFR (if applicable)

## ID Conventions (used in this repo)
- Business Requirements: `BR-xx`
- Technical Requirements: `TR-xx`
- Incongruity Register items: `IR-xx` (issues found during BCIC)
- Use Cases: `UC-xx` (if numbered; otherwise use case names)
- Open Issues: `OI-xx` (ongoing unresolved decisions, if used separately from IR)
- Change Requests: `CR-xx` (post sign-off changes)

**Traceability rule:** Diagrams, checklists, and iRTM rows should reference the relevant IDs (e.g., `UC-02 ↔ BR-02 ↔ TR-07 ↔ IR-08`) to show impact and coverage.

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