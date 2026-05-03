## Why
Generated specs currently require explicit operator acceptance before the workflow can continue. When an operator is unavailable, this creates avoidable blocking and delays.

## What Changes
- Add a configurable auto-accept option for generated specs.
- When enabled, generated specs are accepted automatically without requiring operator action.
- Keep current manual acceptance behavior as the default when auto-accept is not enabled.
- Record that acceptance was automatic (for auditability and operator visibility).

## Impact
- Reduces workflow blocking for unattended or off-hours runs.
- Preserves existing behavior for operators who prefer manual review.
- Requires clear logging/status signaling so downstream steps can distinguish auto-accepted specs from manually accepted specs.