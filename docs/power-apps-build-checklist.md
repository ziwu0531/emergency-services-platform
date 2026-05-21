# Power Apps Build Checklist

## 1. Create The App
1. Open Power Apps Maker Portal.
2. Select `Create`.
3. Choose `Blank canvas app`.
4. Name: `Emergency Services Platform`.
5. Choose tablet layout if offered.

## 2. Create Or Connect Data
Preferred: create SharePoint Lists first, then connect them from Power Apps.

If SharePoint setup is blocked:
1. Build screens using temporary collections.
2. Add a limitation note to the testing report.
3. Keep field names aligned with `app-build-spec.md` so SharePoint can replace collections later.

## 3. Screen Build Order
Build in this order to maximize marks quickly:
1. Home menu.
2. Incident Report.
3. Coordinator Dashboard.
4. Roster Availability.
5. Equipment & Training.

Current Power Apps screen mapping:
- `Screen1`: Home menu.
- `Screen2`: Incident Report.
- `Screen3`: Coordinator Dashboard.
- `Screen4`: Roster Availability.
- `Screen5`: Equipment & Training.

## 4. Incident Report Screen
Minimum controls:
- Incident type dropdown.
- Severity dropdown.
- Location text input.
- Notes input.
- Submit button.
- Success label or notification.

Acceptance check:
- A user can submit a meaningful incident report in one short flow.
- The saved record appears on the Coordinator Dashboard.

## 5. Coordinator Dashboard Screen
Minimum controls:
- Active incidents gallery.
- Status dropdown.
- Status update button.
- Counts for New, Assigned, In Progress, Resolved.

Acceptance check:
- Coordinator can review and update a submitted incident.

## 6. Roster Availability Screen
Minimum controls:
- Date picker.
- Time slot dropdown.
- Availability status dropdown.
- Notes input.
- Save button.
- Gallery of availability records.

Acceptance check:
- Volunteer availability can be saved and reviewed.

## 7. Equipment & Training Screen
Minimum controls:
- Equipment type dropdown.
- Equipment condition dropdown.
- Equipment notes input.
- Save equipment check button.
- Course/certification input.
- Certification status dropdown.
- Expiry date picker.
- Save training record button.

Acceptance check:
- At least one equipment check and one training record can be saved.

## 8. Test Studio
Create or document four tests:
1. Submit incident report.
2. Save volunteer availability.
3. Log equipment check.
4. Update incident status from dashboard.

Save final pass/fail evidence in `qa/testing-report.md`. If the native Test Studio editor blocks recording or action editing, keep screenshots and document the workaround in `qa/test-studio-suite.md`.

## 9. Monitor
Use Monitor while performing:
1. App launch.
2. Incident submission.
3. Dashboard refresh/status update.

Record:
- load time or connector call duration;
- number of data calls;
- one specific performance observation.

## 10. Export And GitHub
1. Save and publish the app.
2. Export `.msapp` or use Git integration if available.
3. If PAC/UI export is blocked, add a source reconstruction fallback and document the limitation.
4. Share GitHub repository with the teaching team.
