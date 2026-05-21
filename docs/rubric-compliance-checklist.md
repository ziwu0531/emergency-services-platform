# Rubric Compliance Checklist

## A. Functional Software (Power Apps & Source Code) [40 Marks]

| Rubric item | Evidence in this repository | Status |
| --- | --- | --- |
| Working Power App addressing A1 use cases [38] | Five-screen Power Apps build: `Screen1` Home, `Screen2` Incident Report, `Screen3` Coordinator Dashboard, `Screen4` Roster Availability, `Screen5` Equipment & Training. Evidence screenshots: `powerapps-Screen1-final.png` to `powerapps-Screen5-final.png`. | Completed as canvas MVP |
| Source code/package stored in GitHub [2] | GitHub repository contains documentation, final screenshots, QA evidence, and source reconstruction under `source/EmergencyServicesPlatform/`. PAC-generated unpack is blocked by the local `pac.exe` crash and documented in `docs/source-export-notes.md`. | Completed with documented fallback |

## B. Quality Assurance And Testing [20 Marks]

| Rubric item | Evidence in this repository | Status |
| --- | --- | --- |
| Formal plan mapped to A1 acceptance criteria with pass/fail [4] | `qa/testing-report.md` maps FR1-FR5 and NFR1/NFR3/NFR4/NFR5 to final results. | Completed |
| Native Power Apps Test Studio suite and limitations/workarounds [8] | Test Studio screenshots are in `qa/evidence/`; suite definition and workaround are in `qa/test-studio-suite.md`. | Completed |
| Performance evaluation using Power Apps Monitor [4] | `qa/evidence/monitor-opened.png`, `qa/evidence/monitor-workflow.png`, and `qa/evidence/monitor-multiple-workflows.png` document the Monitor session and captured workflow event. | Completed |
| Accessibility evaluation [4] | `qa/testing-report.md` accessibility checklist covers contrast, labels, touch targets, focus/navigation, error prevention, and cognitive load. | Completed |

## Remaining Risks

- SharePoint Lists were not connected in the final MVP, so Monitor cannot show SharePoint connector call durations.
- PAC CLI is installed but crashes before `pac canvas unpack`, so source export is represented by a source reconstruction package and documented limitation.
- Test Studio limitations for modern canvas controls are documented with workaround evidence and a native suite definition.
