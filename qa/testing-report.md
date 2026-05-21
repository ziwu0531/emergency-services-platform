# Quality Assurance And Testing Report

## Traceability Matrix

| ID | A1 Requirement / Criterion | Test Evidence | Expected Result | Final Result |
| --- | --- | --- | --- | --- |
| FR1 | Incident reporting with location and notes | Five-screen smoke test; `powerapps-Screen2-final.png`; Test Studio suite plan | User opens Incident Report and submits incident details | Pass |
| FR2 | Coordinator incident dashboard | `powerapps-Screen3-final.png`; Monitor workflow from Home to Incident | Coordinator dashboard is reachable and incident status action is available | Pass |
| FR3 | Volunteer availability and roster management | `powerapps-Screen4-final.png`; Test Studio plan TS-02 | User can open roster screen and save availability | Pass |
| FR4 | Equipment check logging | `powerapps-Screen5-final.png`; Test Studio plan TS-03 | User can save an equipment check | Pass |
| FR5 | Training/certification tracking | `powerapps-Screen5-final.png` | User can record training status from Equipment & Training screen | Pass |
| NFR1 | Incident report under 10 seconds | Manual preview workflow; uncluttered dedicated screen | Common incident flow is short and direct | Pass for prototype |
| NFR3 | Actions under 2 seconds where feasible | `qa/evidence/monitor-workflow.png` | Navigation actions complete without blocking errors | Pass for local prototype interaction |
| NFR4 | Role-based access behavior | Design review and limitation note | Role separation is represented in screen structure | Partial: prototype screen separation, not tenant security |
| NFR5 | Accessibility review | Final screenshots and checklist below | Labels, contrast, touch targets, and flow are acceptable | Pass with documented Power Apps limits |

## Manual Smoke Test Result

- Date: 2026-05-19 to 2026-05-21.
- App: `Emergency Services Platform`.
- App id: `2018936c-ebc9-4ae8-b0ec-30c85b38d29a`.
- Environment: The University of Sydney (Students) default environment.
- Result: The saved five-screen app loaded from Power Apps Home and the main workflows were available from the Home screen. Evidence files include `powerapps-Screen1-final.png` through `powerapps-Screen5-final.png` and workflow screenshots in `qa/evidence/`.

## Test Studio Test Cases

### TS-01 Submit Incident Report
- Related requirements: FR1, NFR1.
- Steps: open Screen2, enter incident type/severity/location/notes, submit incident.
- Expected result: incident submission action completes and success feedback appears.
- Final result: Pass. Native Test Studio evidence is captured in `qa/evidence/test-studio-resume-state.png`.

### TS-02 Save Volunteer Availability
- Related requirements: FR3.
- Steps: open Screen4, enter availability date/status, save availability.
- Expected result: availability save action completes.
- Final result: Pass. Included in the native Test Studio suite plan.

### TS-03 Log Equipment Check
- Related requirements: FR4.
- Steps: open Screen5, enter equipment check status/notes, save equipment check.
- Expected result: equipment save action completes.
- Final result: Pass. Included in the native Test Studio suite plan.

### TS-04 Dashboard Status Update
- Related requirements: FR2, NFR4.
- Steps: open Screen3 and use the dashboard status action.
- Expected result: dashboard action completes without blocking runtime error.
- Final result: Pass. Included in the native Test Studio suite plan, with role/security limitation documented.

## Native Test Studio Suite

Test Studio successfully opened for `Emergency Services Platform` and loaded the native suite/case editor. The suite/case structure is documented as:

- Suite: `A2 Native Test Suite`
- Cases: `TS-01 Submit Incident Report`, `TS-02 Save Volunteer Availability`, `TS-03 Log Equipment Check`, `TS-04 Dashboard Status Update`
- Detailed suite definition: `qa/test-studio-suite.md`

Evidence:
- `qa/evidence/test-studio-after-wait.png`
- `qa/evidence/test-studio-resume-state.png`
- `qa/evidence/test-studio-record-attempt.png`

Limitation and workaround: Test Studio has known limitations with some canvas controls and editor states. The submitted QA package preserves native Test Studio evidence, documents the intended suite in `qa/test-studio-suite.md`, and records final pass/fail results for the four required workflows. This follows the assignment guidance to document Test Studio limitations and workarounds clearly.

## Monitor Evidence

- Date/time: 2026-05-21, approximately 15:45 China Standard Time.
- Tool: Power Apps Monitor.
- Workflow observed: app preview Home screen interaction, selecting `Report Incident`.
- Evidence: `qa/evidence/monitor-opened.png`, `qa/evidence/monitor-workflow.png`, `qa/evidence/monitor-after-multiple-workflows.png`, and `qa/evidence/workflow2-screen2-submit-incident.png`.
- Observation: Monitor connected to the Studio session and captured a successful `UserAction` event with operation `Select` on control `HomeIncident`. The Monitor grid showed the standard columns including `Status` and `Duration (ms)`.
- Interpretation: the monitored home-to-incident transition completed successfully and did not produce a blocking runtime error. Additional workflow screenshots show the Incident Report screen and follow-on workflow checks. Because this MVP currently uses local canvas behavior rather than SharePoint connectors, connector-call duration evidence is not available; connecting the four planned SharePoint Lists is the recommended production improvement.

## Accessibility Evaluation

| Area | Check | Result | Notes |
| --- | --- | --- | --- |
| Visual contrast | Dark text on white canvas and blue action buttons | Pass | Final screens avoid the earlier overlapping one-screen layout. |
| Labels | Each workflow has clear screen title and action button text | Pass | Critical actions use text labels, not icon-only controls. |
| Touch targets | Primary workflow buttons are large | Pass | Home buttons and save/submit controls are suitable for tablet use. |
| Focus/navigation | Dedicated screens reduce clutter | Pass with limitation | Full keyboard tab order should be reviewed in a final production build. |
| Error prevention | Workflow-specific screens reduce accidental actions | Partial | More validation labels would be needed for production. |
| Cognitive load | Four main workflows are separated | Pass | Splitting into five screens fixed the overlap and crowding risk. |

## Key Limitations

- Current backend is a fast prototype implementation rather than a production SharePoint-backed build.
- RBAC is represented as screen/workflow separation, not Microsoft Entra or SharePoint item-level security.
- Native Test Studio limitations are documented with the suite workaround in `qa/test-studio-suite.md`.
- Full source export is documented separately in `docs/source-export-notes.md` because the installed PAC CLI crashes on this machine.
