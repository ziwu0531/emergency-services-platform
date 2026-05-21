# Source Export Notes

## App
- Name: `Emergency Services Platform`
- App id: `2018936c-ebc9-4ae8-b0ec-30c85b38d29a`
- Environment: The University of Sydney (Students) default environment

## Current Source Package Status
The working app exists in Power Apps and the repository contains the delivery documentation, evidence package, and a source reconstruction fallback under `source/EmergencyServicesPlatform/`. A full PAC-generated unpacked canvas app source export is not included because the local Power Platform CLI is not usable in this Windows environment.

`pac.exe` was installed at:

`C:\Users\Lenovo\AppData\Local\Microsoft\PowerAppsCLI\Microsoft.PowerApps.CLI.2.7.4\tools\pac.exe`

When invoked, it crashed before source unpacking could complete. Because `pac canvas unpack` depends on a working `pac.exe`, the repository documents this as a toolchain limitation rather than pretending an unpacked source export exists.

## UI Export Attempt
Power Apps Home was opened for the signed-in student account and the row menu for `Emergency Services Platform` was checked. The visible commands were edit, play, share, details, create agent from app, settings, and delete. A direct export/package command was not visible in the compact home row menu during this session.

Evidence:
- `qa/evidence/powerapps-home-for-export.png`
- `qa/evidence/powerapps-row-menu.png`

## Source Fallback Included
The repository includes `source/EmergencyServicesPlatform/` with screen-level YAML files documenting the app structure, named controls, and key formulas. This is not a replacement for a true PAC unpack, but it gives the teaching team reviewable source-like material in GitHub while the PAC toolchain is blocked.

## Recommended Final Export Path
If the export option becomes available from the app details page or Solutions area, export the app package as:

`EmergencyServicesPlatform_A2_Export.zip`

Then place it under a delivery folder and update this note with the exact file path. If `pac.exe` is repaired later, unpack the `.msapp` or package into source files and commit those files to GitHub.
