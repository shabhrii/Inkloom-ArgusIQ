# CI workflows

Run automated tests and frontend checks on changes. CI must not require production secrets for ordinary unit tests. Add workflows in Phase (2) after local commands are reliable.

## Phase discipline
Implement `(1)` work first. Do not begin `(2)` until the Phase (1) workflow passes. Add `(2)` features one at a time and rerun the full test/demo suite after each. Implement `(3)` only after the project remains stable.
