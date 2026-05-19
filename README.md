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
- `docs/technical-documentation.md`: backend and UI flow documentation.
- `docs/user-guide.md`: volunteer-facing how-to guide.
- `notes.md`: extracted A1 requirements.
- `task_plan.md`: delivery progress tracker.

## Source Export
The final repository should also include the exported or unpacked app source after the app is built:
- preferred: Power Platform Git Integration source files;
- fallback: exported `.msapp` plus unpacked source from Power Platform CLI.

## Current Build Status
- Power App created and published: `Emergency Services Platform`.
- App id: `2018936c-ebc9-4ae8-b0ec-30c85b38d29a`.
- Current app is a collection-backed MVP created in Power Apps Studio.
- Smoke-test screenshot: `powerapps-smoke-test.png`.
- Native Test Studio tests, Monitor export, teaching-team sharing, and source export are still pending.
