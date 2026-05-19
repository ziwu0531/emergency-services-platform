# A2 Power Apps Delivery Plan

## Status
- A1 documents reviewed.
- Project scope confirmed: emergency services platform for incident reporting, volunteer availability, equipment checks, training records, and coordinator oversight.
- Playwright is installed globally and Chromium is available.
- Power Platform CLI MSI was installed, but `pac.exe` currently throws an exception when invoked and should be treated as unavailable until repaired.
- Power Apps app created, saved, and published:
  - Name: `Emergency Services Platform`
  - App id: `2018936c-ebc9-4ae8-b0ec-30c85b38d29a`
  - Environment: The University of Sydney (Students) default environment.
- Manual smoke test was run in preview mode and screenshot evidence was captured as `powerapps-smoke-test.png`.

## Current Priorities
1. Add native Test Studio tests and record final pass/fail results.
2. Capture Power Apps Monitor evidence during the smoke-test workflows.
3. Export or unpack source code and publish to GitHub.
4. Replace collection fallback with SharePoint Lists if time and permissions allow.

## App Build Checklist
- Created Power Apps canvas app.
- Implemented a one-screen MVP with four assignment sections:
  - Incident Report
  - Coordinator Dashboard
  - Roster Availability
  - Equipment & Training
- Current backend is in-memory Power Apps collections, used as fallback because it is the fastest reliable path in the student environment:
  - `Incidents`
  - `VolunteerAvailability`
  - `EquipmentChecks`
  - `TrainingRecords`
- Preferred upgrade remains SharePoint Lists:
  - Incidents
  - VolunteerAvailability
  - EquipmentChecks
  - TrainingRecords

## Evidence Checklist
- Manual smoke test results: completed in preview mode.
- Test Studio suite results: pending native Test Studio creation.
- Monitor screenshot/log with one concrete performance observation: pending.
- Accessibility checklist.
- Exported app/source files in GitHub: pending.
