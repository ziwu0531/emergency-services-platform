# Emergency Services Platform

Canvas Power App prototype for ELEC1005 Assignment 2.

## Purpose
This app supports community emergency service volunteers by consolidating incident reporting, dispatch visibility, roster availability, equipment checks, and training records into a single Power Apps prototype.

## A1 Traceability
- FR1: Incident reporting with location support.
- FR2: Coordinator incident dashboard.
- FR3: Volunteer availability and roster review.
- FR4: Equipment check and maintenance logging.
- FR5: Training and certification tracking.
- NFR1/NFR3: Usability and response time evaluated with Test Studio and Monitor.
- NFR4: Prototype role separation using app-level role selector.
- NFR5: Accessibility evaluated against practical Power Apps limitations.

## Repository Contents
- `app-build-spec.md`: implementation specification for the Power App.
- `qa/testing-report.md`: traceability matrix, test cases, Test Studio results, Monitor evidence, and accessibility evaluation.
- `qa/evidence/`: screenshots from Power Apps Studio, Test Studio, Monitor, and export checks.
- `docs/technical-documentation.md`: backend and UI flow documentation.
- `docs/source-export-notes.md`: source/package export status and PAC CLI limitation.
- `docs/user-guide.md`: volunteer-facing how-to guide.
- `notes.md`: extracted A1 requirements.
- `task_plan.md`: delivery progress tracker.

## Source Export
The app source export is tracked as a documented limitation in `docs/source-export-notes.md`.
Power Platform CLI was installed, but `pac.exe` crashes in this environment, so `pac canvas unpack` could not be used.
The Power Apps Home row menu was checked for package export; direct export was not visible in the current compact row menu.

## Current Build Status
- Power App created and published: `Emergency Services Platform`.
- App id: `2018936c-ebc9-4ae8-b0ec-30c85b38d29a`.
- Current app is a five-screen canvas MVP created in Power Apps Studio:
  `Screen1` Home, `Screen2` Incident Report, `Screen3` Coordinator Dashboard,
  `Screen4` Roster Availability, and `Screen5` Equipment & Training.
- Final layout screenshots: `powerapps-Screen1-final.png` through `powerapps-Screen5-final.png`.
- Earlier smoke-test screenshot: `powerapps-smoke-test.png`.
- Native Test Studio was opened and attempted; the browser session exposed read-only step action fields, so the final QA package records the native attempt and manual workflow pass/fail results.
- Monitor evidence captured a successful `UserAction Select` on `HomeIncident` during preview.
- Source/package export remains a documented tooling limitation pending a working PAC CLI or visible Power Apps export command.
