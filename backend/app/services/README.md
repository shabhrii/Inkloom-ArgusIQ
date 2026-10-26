# Services

Business orchestration lives here. Coordinate processing, verification, persistence and workflow transitions. Services should be testable without making HTTP requests.

## Phase discipline
Implement `(1)` work first. Do not begin `(2)` until the Phase (1) workflow passes. Add `(2)` features one at a time and rerun the full test/demo suite after each. Implement `(3)` only after the project remains stable.
