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
1. Commit and push the updated QA evidence and documentation to GitHub.
2. If more time becomes available, repair PAC CLI or use Power Apps package export from the full app details/Solutions area.
3. Replace collection fallback with SharePoint Lists if time and permissions allow.

## App Build Checklist
- Created Power Apps canvas app.
- Implemented a five-screen canvas MVP:
  - Screen1: Home
  - Screen2: Incident Report
  - Screen3: Coordinator Dashboard
  - Screen4: Roster Availability
  - Screen5: Equipment & Training
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
- Test Studio suite results: native Test Studio opened and attempted; read-only action fields documented as limitation.
- Monitor screenshot/log with one concrete performance observation: completed in `qa/evidence/monitor-workflow.png`.
- Accessibility checklist: completed in `qa/testing-report.md`.
- Exported app/source files in GitHub: blocked by PAC CLI crash and missing compact-menu export command; documented in `docs/source-export-notes.md`.
