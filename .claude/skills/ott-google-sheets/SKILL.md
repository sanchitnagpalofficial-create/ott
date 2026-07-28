---
name: ott-google-sheets
description: Workflow memory for OTT's interconnected Google Sheets system: Client Records, Project Records, Book of Business, and Editor Job Records.
---

# OTT Google Sheets

## Purpose

Use this skill for OTT sheet architecture, experiments, or maintenance involving client records, prospect tracking, project records, job IDs, editor assignments, and delivery links.

## Hierarchy

The sheet hierarchy is:

1. Client Records
2. Project Records
3. Editor Job Records

Lower-level sheets may provide updates such as delivery links, but they must not structurally damage or overwrite higher-level sources of truth.

## Client Records

- Everyone who talks business with OTT enters Client Records.
- Client status should distinguish `Prospect` and `Active`.
- Prospects should appear in a `PROSPECTS` tab inside Client Records.
- Prospect information also feeds a separate shareable `Book of Business` sheet for marketing.
- Book of Business exists so marketing can see prospect information without access to the full sensitive client records.

## Project Records

- Project Records is the OTT source of truth.
- It supports client invoicing and editor payments, so it must be protected carefully.
- When a client becomes active, their project work moves into Project Records.
- One client may have multiple projects.
- Each project receives a `Project ID`.
- Each deliverable/video receives a unique `Job ID`.
- Client-facing job sheets may be replicated internally depending on client needs.

## Editor Job Records

- Project Records assigns jobs to editors.
- Assigned jobs should appear in Editor Job Records.
- Editors return work through status updates and final Drive/upload links.
- Editor output links should reflect back into Project Records and, where appropriate, the client-facing sheet.

## Design Requirement

Build formulas and links to survive column insertion, deletion, and reordering wherever possible. Prefer header-aware formulas, named ranges, config/helper tabs, protected ranges, and stable IDs over fragile hardcoded column letters.

## Existing Experiment Created In Earlier PA Chat

Three Google Sheets experiments were created:

- `CLIENT RECORD SHEET AI EXPERIMENT`
- `PROJECT RECORD SHEET AI EXPERIMENT`
- `JOB RECORD SHEET AI EXPERIMENT`

Known verification:

- Production sheets were not touched.
- Header-aware formulas were installed.
- Source/config tabs were hidden.
- Warning protections were added around formula/source areas.
- Cross-file `IMPORTRANGE` links may require one-time `Allow access` clicks in Google Sheets.

## Strictly Do Not Do

- Do not touch production sheets when Sanchit asks for experiments.
- Do not build fragile formulas that depend only on fixed column letters if a safer header-aware approach is feasible.
- Do not expose full Client Records to marketing when Book of Business is enough.
- Do not let Editor Job Records override source-of-truth project data.
- Do not treat Project Records casually; it affects invoicing and editor payments.

