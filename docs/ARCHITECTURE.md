# Architecture and boundaries

## High-level request flow
React UI → FastAPI router → service layer → processing/verification components → repositories → PostgreSQL/private storage.

## Layers
- **Frontend:** presentation, input validation for usability, API calls, loading/error states. It is not a security boundary.
- **API:** request/response validation, authentication, authorization, HTTP status codes.
- **Services:** orchestration and business rules; routes should remain thin.
- **Processing:** safe parsing and extraction of supported files.
- **Verification:** deterministic checks first; evidence retrieval and AI-based checks where needed.
- **Governance:** findings, risk routing, comments, decisions, revisions and analytics.
- **Repositories:** database queries, isolated from business logic.
- **Storage:** a common interface for local development and private object storage.
- **AI provider adapters:** provider-specific code behind interfaces; structured outputs must be validated.

## Data flow
1. Validate and store upload.
2. Create document/version record and calculate content hash.
3. Extract text and, where supported, image/OCR regions.
4. Load applicable policy/rules and approved knowledge.
5. Run deterministic checks and supported semantic checks.
6. Persist typed findings and evidence references.
7. Present findings to the reviewer.
8. Record reviewer action and revision; never auto-change approved policy.
9. Aggregate only persisted, appropriately scoped findings into analytics.

## Key entities
User, Organization, Document, Guideline, PolicyRule, ApprovedFact, Terminology, Disclosure, BrandAsset, VerificationRun, Finding, Evidence, Review, Comment, Approval, Revision, AuditLog, PolicyVersion.

## Core interfaces
Keep stable service contracts around `DocumentService`, `GuidelineService`, `VerificationService`, `ReviewService`, and `StorageService`. Prefer typed Pydantic request/response schemas and explicit enums over unstructured dictionaries.

## Error handling
Return safe, actionable errors. Log technical details server-side without logging secrets or full confidential document contents unnecessarily. AI/provider failures must not be represented as successful verification.

## Incremental development
Phase (1) must run end-to-end before Phase (2). Add Phase (2) modules individually and run all tests after each. Phase (3) is optional and must not be required to run the MVP.
