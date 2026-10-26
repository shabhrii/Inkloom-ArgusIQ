# Core security and infrastructure

Centralize configuration-independent security helpers, permission checks, exceptions, logging and middleware. Never log secrets or rely on frontend checks for access control.

## Phase discipline
Implement `(1)` work first. Do not begin `(2)` until the Phase (1) workflow passes. Add `(2)` features one at a time and rerun the full test/demo suite after each. Implement `(3)` only after the project remains stable.
