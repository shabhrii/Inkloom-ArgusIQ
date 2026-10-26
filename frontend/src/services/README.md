# API services

Centralize HTTP calls and error mapping here. Do not call fetch directly throughout components. Use one configured API client, typed request/response models, timeouts where appropriate, and no provider secrets.

## Phase discipline
Implement `(1)` work first. Do not begin `(2)` until the Phase (1) workflow passes. Add `(2)` features one at a time and rerun the full test/demo suite after each. Implement `(3)` only after the project remains stable.
