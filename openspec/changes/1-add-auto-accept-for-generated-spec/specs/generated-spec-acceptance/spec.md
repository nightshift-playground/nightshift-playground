## ADDED Requirements

### Requirement: Configurable auto-accept for generated specs
The orchestrator MUST support configuration to auto-accept generated specs.

#### Scenario: Auto-accept disabled by default
- **GIVEN** no auto-accept configuration is provided
- **WHEN** a generated spec is produced
- **THEN** the orchestrator MUST require manual acceptance before continuing.

#### Scenario: Auto-accept explicitly enabled
- **GIVEN** auto-accept for generated specs is enabled in configuration
- **WHEN** a generated spec is produced
- **THEN** the orchestrator MUST mark the generated spec as accepted without waiting for operator input
- **AND** continue the workflow.

### Requirement: Acceptance path visibility
The orchestrator MUST make the acceptance path visible for generated specs.

#### Scenario: Auto-accepted spec is observable
- **GIVEN** auto-accept for generated specs is enabled
- **WHEN** a generated spec is accepted automatically
- **THEN** the orchestrator MUST emit a visible indicator (for example status or log) that acceptance was automatic.

#### Scenario: Manual acceptance remains observable
- **GIVEN** auto-accept for generated specs is disabled
- **WHEN** a generated spec is accepted by an operator
- **THEN** the orchestrator MUST preserve visibility that acceptance occurred via manual operator action.