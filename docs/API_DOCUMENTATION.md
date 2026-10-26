# API contract guide

Use a versioned API prefix such as `/api/v1`. Keep route handlers thin and use Pydantic schemas.

## Core endpoint families
- `/auth`: login/session/token operations.
- `/users`: current user and authorised user administration.
- `/documents`: upload, list, detail, extracted content and document versions.
- `/guidelines`: guideline/rule/fact/terminology/disclosure management.
- `/assets`: approved brand asset management.
- `/verification`: start a verification run and retrieve status/results.
- `/findings`: finding detail and evidence references.
- `/reviews`: reviewer actions, comments and assignments.
- `/approvals`: approval decisions and state transitions.
- `/analytics`: aggregated recurring issues and counts.
- `/audit-logs`: Phase (2) audit-log querying if implemented.

## Contract rules
- Use consistent IDs, timestamps and status enums.
- Validate all inputs server-side.
- Apply authorization and organization scoping to every protected operation.
- Return stable error structures with an error code and human-readable message.
- Never return secrets, provider keys, private storage paths, or unnecessary document contents.
- Document request/response examples as endpoints are implemented.
- Do not expose endpoints for unimplemented features as if they work.
