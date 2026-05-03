## ADDED Requirements
### Requirement: README includes Escalated status
The project README MUST list `Escalated` as a supported status in the workflow/status documentation.

#### Scenario: Status list includes Escalated
- **GIVEN** a reader checks the README section that enumerates statuses
- **WHEN** they review the documented status values
- **THEN** `Escalated` appears as one of the listed statuses

### Requirement: Escalated status is defined
The README MUST provide a brief explanation of what `Escalated` means.

#### Scenario: Reader interprets Escalated correctly
- **GIVEN** a reader sees `Escalated` in the README status list
- **WHEN** they read the accompanying description
- **THEN** they understand it indicates work was raised for operator attention or intervention
