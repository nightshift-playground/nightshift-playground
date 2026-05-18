## Why
Agent-authored messages are currently indistinguishable from other assistant messages once rendered in the conversation transcript. This limits auditability, reduces operator trust in who produced a message, and makes debugging multi-actor flows harder.

## What Changes
- Add an explicit footer to every agent-authored message.
- Footer includes stable agent identity metadata: `displayName` and `role`.
- Define deterministic fallback text for missing optional metadata.
- Render the footer consistently across all transcript/message presentation surfaces used by the orchestrator.
- Do not render the footer for non-agent-authored messages.

## Impact
- Improves provenance and operator clarity for generated output.
- Introduces a small UI/layout change for agent-authored messages.
- Requires updates to message view-model plumbing where agent metadata is shaped for rendering.
- Requires tests for rendering logic, author-type gating, and fallback behavior.