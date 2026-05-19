# A1 Extracted Notes

## Problem Statement
Volunteer emergency services currently rely on fragmented tools including radio, WhatsApp, paper forms, Excel rosters, and email. This causes delays in incident response, poor roster visibility, lost equipment checks, and miscommunication during high-pressure situations.

The A2 app should provide a unified digital platform for incident reporting, volunteer rostering, resource management, and communication, with attention to efficiency, safety, and usability under stress.

## Use Cases
- Incident Reporting & Volunteer Dispatch
  - Actors: field volunteer, operations coordinator.
  - User story: as a volunteer, I want to report an incident quickly so that coordinators can dispatch the nearest available team.
- Volunteer Roster & Availability Management
  - Actors: roster manager, volunteer.
  - User story: as a volunteer, I want to set my availability so that I only receive shifts I can attend.

## Functional Requirements
- FR1: One-click incident reporting with GPS location.
- FR2: Real-time incident dashboard for coordinators.
- FR3: Volunteer availability and roster management.
- FR4: Equipment check and maintenance logging.
- FR5: Training and certification tracking.

## Non-Functional Requirements
- NFR1: Usability: incident report under 10 seconds.
- NFR2: Reliability: 99.9% uptime; offline caching.
- NFR3: Response time: all actions under 2 seconds.
- NFR4: Security: role-based access control.
- NFR5: Accessibility: WCAG 2.1 compliant.

## A1 Acceptance Criteria
- FR1: user can submit incident in under 3 taps with auto-location.
- NFR1: 90% of test users complete report within 10 seconds.

