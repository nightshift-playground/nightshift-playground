## ADDED Requirements

### Requirement: Agent-authored messages include a footer
The system SHALL render a footer for messages authored by an agent.

#### Scenario: Render footer for agent-authored message
- **Given** a message with `author.type` equal to `agent`
- **When** the message is rendered in a transcript surface
- **Then** a footer is shown beneath the message body
- **And** the footer contains the resolved display name
- **And** the footer contains the resolved role

### Requirement: Agent footer format is deterministic
The system SHALL render the footer text in the format `<displayName> · <role>`.

#### Scenario: Footer uses display name and role
- **Given** an agent-authored message with `author.displayName = "Runner"` and `author.role = "Implementer"`
- **When** the message is rendered
- **Then** the footer text is `Runner · Implementer`

### Requirement: Footer rendering is resilient to missing metadata
The system SHALL apply deterministic fallback text when optional agent metadata is absent.

#### Scenario: Missing role
- **Given** an agent-authored message with `author.displayName = "Runner"` and missing `author.role`
- **When** the message is rendered
- **Then** the footer text is `Runner · Unknown role`

#### Scenario: Missing display name
- **Given** an agent-authored message with missing `author.displayName` and `author.role = "Implementer"`
- **When** the message is rendered
- **Then** the footer text is `Agent · Implementer`

#### Scenario: Missing both display name and role
- **Given** an agent-authored message with missing `author.displayName` and missing `author.role`
- **When** the message is rendered
- **Then** the footer text is `Agent · Unknown role`

### Requirement: Non-agent-authored messages do not include an agent footer
The system SHALL NOT render the agent footer for messages not authored by an agent.

#### Scenario: User-authored message
- **Given** a message with `author.type` equal to `user`
- **When** the message is rendered
- **Then** no agent footer is shown

#### Scenario: System-authored message
- **Given** a message with `author.type` equal to `system`
- **When** the message is rendered
- **Then** no agent footer is shown

#### Scenario: Assistant-authored non-agent message
- **Given** a message with `author.type` not equal to `agent`
- **When** the message is rendered
- **Then** no agent footer is shown