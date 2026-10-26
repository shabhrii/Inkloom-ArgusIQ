# Hooks

Hooks encapsulate reusable client-side data fetching and state. They should use the services layer and expose typed loading/error/data states. Do not hide authorization decisions in client-only hooks.

## Phase discipline
Implement `(1)` work first. Do not begin `(2)` until the Phase (1) workflow passes. Add `(2)` features one at a time and rerun the full test/demo suite after each. Implement `(3)` only after the project remains stable.
