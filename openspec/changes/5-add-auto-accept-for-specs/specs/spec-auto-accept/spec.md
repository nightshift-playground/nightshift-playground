## ADDED Requirements

### Requirement: Configurable Spec Auto-Accept
The orchestrator MUST support a configuration option that controls whether generated specs are accepted automatically.

#### Scenario: Auto-accept disabled by default
- **GIVEN** orchestrator configuration does not explicitly enable spec auto-accept
- **WHEN** a spec is generated in the specify phase
- **THEN** the workflow MUST wait for operator acceptance as it does today

#### Scenario: Auto-accept explicitly enabled
- **GIVEN** orchestrator configuration enables spec auto-accept
- **WHEN** a valid spec is generated in the specify phase
- **THEN** the orchestrator MUST mark the spec as accepted without waiting for manual operator input

### Requirement: Acceptance Gate Safety
Auto-accept MUST only skip manual acceptance input and MUST NOT bypass spec validity checks.

#### Scenario: Generated spec is invalid while auto-accept enabled
- **GIVEN** spec auto-accept is enabled
- **AND** generated spec fails validation or is incomplete
- **WHEN** the specify phase evaluates the spec
- **THEN** the run MUST follow the existing failure path and MUST NOT advance as accepted

### Requirement: Acceptance Auditability
The orchestrator MUST emit observable output that distinguishes automatic acceptance from manual acceptance.

#### Scenario: Auto-accepted run is logged
- **GIVEN** a generated spec is auto-accepted
- **WHEN** run activity is recorded
- **THEN** logs or activity output MUST include an explicit indicator that acceptance was automatic
