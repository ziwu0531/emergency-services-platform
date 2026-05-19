# Emergency Services Platform - Power Apps Build Spec

## App
- Name: `Emergency Services Platform`
- Type: Canvas app, tablet layout preferred for dashboard space.
- Theme: high-contrast professional emergency-services palette with clear status colors.

## Data Sources
Prefer SharePoint Lists. If SharePoint list creation is unavailable, use collections with the same fields.

### Incidents
- `Title`: single line text, generated incident reference.
- `IncidentType`: choice: Fire, Flood, Medical, Road Hazard, Missing Person, Other.
- `Severity`: choice: Low, Medium, High, Critical.
- `LocationText`: single line text.
- `Latitude`: number.
- `Longitude`: number.
- `Notes`: multiple lines text.
- `Status`: choice: New, Assigned, In Progress, Resolved.
- `ReportedBy`: person or text.
- `CreatedAt`: date/time.

### VolunteerAvailability
- `Title`: volunteer name or email.
- `VolunteerEmail`: single line text.
- `AvailableDate`: date.
- `TimeSlot`: choice: Morning, Afternoon, Evening, Overnight.
- `AvailabilityStatus`: choice: Available, Maybe, Unavailable.
- `Notes`: multiple lines text.

### EquipmentChecks
- `Title`: equipment item.
- `EquipmentType`: choice: Radio, First Aid Kit, Vehicle, PPE, Rescue Tool, Other.
- `ConditionStatus`: choice: Ready, Needs Maintenance, Out of Service.
- `CheckedBy`: text.
- `CheckedAt`: date/time.
- `Notes`: multiple lines text.

### TrainingRecords
- `Title`: volunteer name or email.
- `CourseName`: text.
- `CertificationStatus`: choice: Current, Expiring Soon, Expired, Not Started.
- `ExpiryDate`: date.
- `Notes`: multiple lines text.

## Screens

### Incident Report
Purpose: satisfy FR1 and NFR1.
- Controls:
  - Dropdown `IncidentTypeDropdown`
  - Dropdown `SeverityDropdown`
  - Text input `LocationInput`
  - Text input `NotesInput`
  - Button `UseLocationButton`
  - Button `SubmitIncidentButton`
  - Label `IncidentSubmitStatusLabel`
- Submit behavior:
  - Create an `Incidents` record.
  - Default status is `New`.
  - Prefer `Location.Latitude` and `Location.Longitude` if available; otherwise store manual `LocationInput`.
  - Show success message and reset fields.

### Coordinator Dashboard
Purpose: satisfy FR2 and support dispatch review.
- Controls:
  - Gallery of active incidents filtered to non-resolved records.
  - Status dropdown for selected incident.
  - Summary counters: New, Assigned, In Progress, Resolved.
  - Refresh button.
- Behavior:
  - Coordinator can update status.
  - Sort newest first.

### Roster Availability
Purpose: satisfy FR3.
- Controls:
  - Date picker
  - Time slot dropdown
  - Availability status dropdown
  - Notes input
  - Save availability button
  - Availability gallery
- Behavior:
  - Volunteer saves availability.
  - Roster manager can review saved availability.

### Equipment & Training
Purpose: satisfy FR4 and FR5.
- Use tabs or a segmented control:
  - Equipment check form.
  - Training record form.
- Equipment behavior:
  - Log equipment condition and notes.
- Training behavior:
  - Log certification name, status, and expiry date.

## Role Handling
For a fast MVP, implement soft role switching in the app:
- Dropdown `RoleSelector`: Volunteer, Coordinator, Roster Manager.
- Hide coordinator-only controls unless role is Coordinator.
- Document this as a prototype RBAC limitation. If Microsoft Entra or SharePoint permissions are configured later, replace soft role switching with actual permission-based access.

## Power Fx Formula Sketches

### App OnStart
```powerfx
Set(varUserEmail, User().Email);
Set(varUserName, User().FullName);
Set(varRole, "Volunteer");
```

### Submit Incident
```powerfx
Patch(
    Incidents,
    Defaults(Incidents),
    {
        Title: "INC-" & Text(Now(), "yyyymmdd-hhmmss"),
        IncidentType: IncidentTypeDropdown.Selected.Value,
        Severity: SeverityDropdown.Selected.Value,
        LocationText: LocationInput.Text,
        Latitude: Location.Latitude,
        Longitude: Location.Longitude,
        Notes: NotesInput.Text,
        Status: "New",
        ReportedBy: varUserEmail,
        CreatedAt: Now()
    }
);
Notify("Incident submitted", NotificationType.Success);
Reset(IncidentTypeDropdown);
Reset(SeverityDropdown);
Reset(LocationInput);
Reset(NotesInput);
```

### Save Availability
```powerfx
Patch(
    VolunteerAvailability,
    Defaults(VolunteerAvailability),
    {
        Title: varUserName,
        VolunteerEmail: varUserEmail,
        AvailableDate: AvailabilityDatePicker.SelectedDate,
        TimeSlot: TimeSlotDropdown.Selected.Value,
        AvailabilityStatus: AvailabilityDropdown.Selected.Value,
        Notes: AvailabilityNotesInput.Text
    }
);
Notify("Availability saved", NotificationType.Success);
```

### Update Incident Status
```powerfx
Patch(
    Incidents,
    IncidentGallery.Selected,
    { Status: StatusDropdown.Selected.Value }
);
Notify("Incident status updated", NotificationType.Success);
```

