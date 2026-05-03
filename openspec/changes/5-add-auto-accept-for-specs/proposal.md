## Why
The current orchestrator flow requires manual operator acceptance after a spec is generated. When the operator is unavailable, the workflow blocks even when the generated spec is acceptable for low-risk or unattended runs.

## What Changes
- Add configurable auto-acceptance for generated specs.
- Introduce an operator-facing configuration setting to enable or disable auto-accept behavior.
- Apply auto-accept only to the spec acceptance gate, preserving all existing generation and validation steps.
- Record when acceptance was automatic so operators can audit workflow outcomes.

## Scope
In scope:
- Config surface for auto-accept behavior.
- Acceptance-gate logic change in the specify phase.
- Activity/log output indicating auto-accepted decisions.
- Tests for enabled and disabled behavior.

Out of scope:
- Changing spec generation quality checks.
- Adding confidence scoring or AI-based risk classification.
- Altering accept behavior in non-spec phases.

## Success Criteria
- With auto-accept enabled, a generated valid spec proceeds without manual acceptance.
- With auto-accept disabled (default), current manual-accept behavior remains unchanged.
- Runs clearly indicate whether acceptance was manual or automatic.
- Existing workflows and tests continue to pass.
