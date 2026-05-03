## 1. Configuration
- [ ] 1.1 Add a new orchestrator config option for spec auto-accept (default `false`).
- [ ] 1.2 Validate and thread this option into specify-phase dependencies.
- [ ] 1.3 Document config semantics in relevant operator docs.

## 2. Specify Phase Behavior
- [ ] 2.1 Update spec acceptance gating logic to bypass manual wait when auto-accept is enabled.
- [ ] 2.2 Preserve existing error paths for invalid or missing generated specs.
- [ ] 2.3 Emit an explicit event/log marker for auto-accepted specs.

## 3. Tests
- [ ] 3.1 Add unit tests for default/manual acceptance behavior.
- [ ] 3.2 Add unit tests for enabled auto-accept behavior.
- [ ] 3.3 Add integration or e2e coverage showing non-blocking flow with auto-accept enabled.

## 4. Rollout Safety
- [ ] 4.1 Verify backward compatibility for existing configs.
- [ ] 4.2 Confirm observability output is sufficient for post-run auditing.
