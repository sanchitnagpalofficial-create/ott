---
type: project
project: OTT Google Sheets
status: active
tags: [ott, google-sheets, operations]
---

# OTT Google Sheets

Current workflow memory is stored in `.claude/skills/ott-google-sheets/SKILL.md`.

## System

- Client Records stores all business contacts.
- Prospect status feeds Prospects and Book of Business.
- Active status feeds Project Records.
- Project Records is the source of truth for invoicing and editor payments.
- Editor Job Records receives assigned jobs and returns output links.

## Implementation Principle

Use header-aware formulas and protected source/config areas so the system survives column movement better than hardcoded column-letter formulas.

