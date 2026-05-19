# Quality Assurance And Testing Report

## Traceability Matrix

| ID | A1 Requirement / Criterion | Test Evidence | Expected Result | Final Result |
| --- | --- | --- | --- | --- |
| FR1 | One-click incident reporting with GPS location | TS-01, manual smoke test, screenshot | User submits incident with type, severity, location, notes, and status `New` | Pending |
| FR2 | Real-time incident dashboard for coordinators | TS-04, Monitor dashboard refresh trace | New incident appears in coordinator dashboard and status can be updated | Pending |
| FR3 | Volunteer availability and roster management | TS-02 | Volunteer availability record is saved and visible in roster view | Pending |
| FR4 | Equipment check and maintenance logging | TS-03 | Equipment condition is logged with date/time and notes | Pending |
| FR5 | Training and certification tracking | Manual smoke test | Training record is created with status and expiry date | Pending |
| NFR1 | Incident report under 10 seconds | timed manual test | A volunteer completes incident submission in under 10 seconds | Pending |
| NFR3 | Actions under 2 seconds where feasible | Power Apps Monitor | Common actions complete in around 2 seconds or limitation is documented | Pending |
| NFR4 | Role-based access control | manual role test | Coordinator-only controls are hidden from Volunteer role | Pending |
| NFR5 | Accessibility / WCAG 2.1 focus | accessibility checklist | Labels, contrast, focus order, and touch targets are acceptable | Pending |

## Test Studio Test Cases

### TS-01 Submit Incident Report
- Related requirements: FR1, NFR1.
- Preconditions: app is open on Incident Report screen.
- Steps:
  1. Select an incident type.
  2. Select severity.
  3. Use current location or enter a location manually.
  4. Enter short notes.
  5. Select Submit.
- Expected result: a new incident record is created and success notification appears.
- Final result: Pending.

### TS-02 Save Volunteer Availability
- Related requirements: FR3.
- Preconditions: app is open on Roster Availability screen.
- Steps:
  1. Select an available date.
  2. Select a time slot.
  3. Select availability status.
  4. Save the record.
- Expected result: availability appears in the roster gallery.
- Final result: Pending.

### TS-03 Log Equipment Check
- Related requirements: FR4.
- Preconditions: app is open on Equipment & Training screen.
- Steps:
  1. Select equipment type.
  2. Select condition status.
  3. Enter notes.
  4. Save equipment check.
- Expected result: equipment check record is created with date/time.
- Final result: Pending.

### TS-04 Dashboard Status Update
- Related requirements: FR2, NFR4.
- Preconditions: at least one incident exists.
- Steps:
  1. Switch role to Coordinator.
  2. Open Coordinator Dashboard.
  3. Select an active incident.
  4. Change status to Assigned or In Progress.
- Expected result: dashboard updates and incident status persists.
- Final result: Pending.

## Test Studio Limitations And Workarounds
- Location controls and browser permission prompts may not be fully reliable in automated Test Studio recordings. Workaround: allow manual location text input and test that path automatically.
- Some modern controls may not expose stable selectors to Test Studio. Workaround: use classic input controls for core testable flows where possible.
- Connector timing may vary. Workaround: add visible success labels/notifications and test those rather than relying only on fixed wait times.
- Prototype RBAC is app-level soft role selection, not tenant-level security. Workaround: document as a prototype limitation and use SharePoint permissions if time permits.

## Monitor Evidence Template
- Workflow observed:
- Date/time:
- Tool: Power Apps Monitor.
- Observation:
- Evidence file/screenshot:
- Interpretation:
- Improvement made or recommended:

Example observation format:
> During incident submission, Monitor showed the `Patch` call to the `Incidents` list completing in approximately ___ ms. The dashboard refresh triggered ___ data calls. This is acceptable / requires improvement because ___.

## Accessibility Evaluation

| Area | Check | Result | Notes |
| --- | --- | --- | --- |
| Visual contrast | Text and buttons are readable against backgrounds | Pending | Use high-contrast colors for emergency statuses. |
| Labels | Inputs have clear visible labels | Pending | Avoid icon-only critical actions. |
| Touch targets | Primary buttons are large enough for field use | Pending | Prioritize large submit/save buttons. |
| Focus/navigation | Keyboard/tab order follows screen flow | Pending | Verify after controls are built. |
| Error prevention | Required fields are clear before submit | Pending | Use validation labels and notifications. |
| Cognitive load | Screens use short labels and obvious workflow order | Pending | Keep incident submission minimal. |

