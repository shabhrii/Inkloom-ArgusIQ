# Verification modules

Phase (1) modules are the priority: rule engine, terminology/disclosure/date/channel/accessibility checks, claim extraction, evidence retrieval, claim verifier, tone analyzer and basic visual checks only to the supported scope. Every check returns normalized findings. Exact rules must be deterministic. Semantic checks return evidence, limitations and an uncertainty state. Do not implement advanced risk scoring, logo geometry or policy compilation until the core workflow passes.

## Implementation sequence
Complete Phase (1) first. Phase (2) must be introduced one feature at a time with full regression tests after each feature. Phase (3) is optional.
