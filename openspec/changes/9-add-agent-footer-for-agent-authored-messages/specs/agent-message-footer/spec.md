## ADDED Requirements

### Requirement: Agent-authored messages include a footer
The system SHALL render a footer on messages authored by an agent.

#### Scenario: Render footer for agent-authored message
- **Given** a message whose `author.type` is `agent`
- **When** the message is rendered in the transcript
- **Then** a footer is displayed beneath the message body
- **And** the footer includes the agent display name
- **And** the footer includes the agent role

### Requirement: Non-agent messages do not include an agent footer
The system SHALL NOT render the agent footer for messages not authored by an agent.

#### Scenario: No footer for user-authored message
- **Given** a message whose `author.type` is `user`
- **When** the message is rendered in the transcript
- **Then** no agent footer is displayed

#### Scenario: No footer for system-authored message
- **Given** a message whose `author.type` is `system`
- **When** the message is rendered in the transcript
- **Then** no agent footer is displayed

### Requirement: Footer rendering is resilient to partial metadata
The system SHALL render safely when optional agent metadata is absent.

#### Scenario: Missing optional agent role
- **Given** a message authored by an agent with a display name but no role
- **When** the message is rendered
- **Then** a footer is still displayed
- **And** the role text is `Unknown role`

#### Scenario: Missing optional agent display name
- **Given** a message authored by an agent with a role but no display name
- **When** the message is rendered
- **Then** a footer is still displayed
- **And** the display name text is `Agent`

#### Scenario: Missing both optional fields
- **Given** a message authored by an agent with neither display name nor role
- **When** the message is rendered
- **Then** a footer is still displayed
- **And** the footer text is `Agent · Unknown role`