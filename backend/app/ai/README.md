# AI integration

Use a provider interface so the rest of the app is not coupled to one model vendor. Keep keys on the backend. Request structured outputs and validate them before use. Model output is untrusted until validated. If provider calls fail or evidence is insufficient, return an explicit unavailable/uncertain state rather than a pass.

## Implementation sequence
Complete Phase (1) first. Phase (2) must be introduced one feature at a time with full regression tests after each feature. Phase (3) is optional.
