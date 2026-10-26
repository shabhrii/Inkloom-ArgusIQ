# Implementation contracts by module

This document explains the role and expected behavior of the principal files in the target structure. A file's existence in the structure does not mean it should be implemented immediately.

## Frontend modules
- `main.tsx`: React entry point; mounts the application.
- `App.tsx`: application shell and global providers.
- `routes.tsx`: route definitions and protected-route wiring.
- `components/common/*`: reusable UI primitives, status and error states.
- `components/upload/*`: file selection, preview and progress.
- `components/guidelines/*`: create/edit approved rules and knowledge.
- `components/verification/*`: findings, evidence, severity and correction preview.
- `components/visual/*`: image/region presentation and visual-compliance results.
- `components/review/*`: review actions, comments, approvals and revision history.
- `components/analytics/*`: summaries derived from persisted findings and decisions.
- `components/admin/*`: user/role management and settings.
- `pages/*`: route-level composition; no core verification logic.
- `services/*`: typed API access.
- `hooks/*`: reusable UI state/data access.
- `context/*`: authentication/session and notification state.
- `types/*`: shared TypeScript domain types.
- `utils/*`: pure helpers only.
- `tests/*`: component, service and end-to-end regression tests.

## Backend modules
- `main.py`: create FastAPI app, register middleware and routers, expose health check.
- `config.py`: validated environment-based configuration.
- `dependencies.py`: dependency injection for DB sessions and authenticated users.
- `api/v1/*`: HTTP endpoints; validate and delegate, no large business logic.
- `core/security.py`: password/token/session primitives selected for the implementation.
- `core/permissions.py`: server-side role and scope checks.
- `models/*`: SQLAlchemy entities.
- `schemas/*`: Pydantic input/output contracts.
- `db/session.py`: database engine/session lifecycle.
- `db/repositories/*`: data-access queries.
- `services/*`: orchestration and state transitions.
- `processing/file_validator.py`: file type, size and safety checks.
- `processing/text_extractor.py`: common extraction interface.
- `processing/pdf_processor.py`, `docx_processor.py`: format-specific extraction.
- `processing/ocr_engine.py`: OCR only for supported image/page workflows.
- `verification/rule_engine.py`: orchestrate deterministic checks.
- `verification/terminology_checker.py`: exact/approved terminology checks.
- `verification/disclosure_checker.py`: required disclosure checks.
- `verification/date_checker.py`: date/freshness constraints where configured.
- `verification/accessibility_checker.py`: measurable accessibility checks within supported formats.
- `verification/channel_checker.py`: channel constraints configured by policy.
- `verification/claim_extractor.py`: split text into atomic claims.
- `verification/evidence_retriever.py`: fetch applicable approved source passages.
- `verification/claim_verifier.py`: classify supported/contradicted/insufficient evidence.
- `verification/tone_analyzer.py`: semantic tone checks; human review remains available.
- `verification/visual_verifier.py`: coordinate supported visual checks.
- `verification/finding_aggregator.py` or `governance/finding_aggregator.py`: normalize and persist findings; avoid duplicate ownership.
- `verification/risk_engine.py`: Phase (2) severity/confidence/risk scoring.
- `verification/logo_matcher.py`, `geometry_checker.py`: Phase (2) visual asset comparison and measurable checks.
- `verification/policy_compiler.py`, `confidence_calibrator.py`: Phase (3).
- `ai/provider.py`, `llm_client.py`, `vision_client.py`: provider abstractions; provider choice is configurable.
- `ai/structured_outputs.py`, `response_validator.py`: validate model responses before persistence.
- `retrieval/keyword_search.py`: baseline approved-source search.
- `retrieval/vector_search.py`, `hybrid_search.py`: Phase (2) retrieval enhancements.
- `retrieval/reranker.py`: Phase (3) reranking.
- `governance/review_router.py`: Phase (2) risk-adaptive routing.
- `governance/policy_versioning.py`, `provenance_tracker.py`: add when version/audit needs justify and tests are ready.
- `governance/analytics_engine.py`: aggregate recurring issues from stored data.
- `governance/active_learning.py`: Phase (3).
- `storage/*`: private storage abstraction, local implementation and later retention/encryption controls.
- `tests/*`: tests that validate module contracts and cross-layer behavior.
- `scripts/*`: explicit development operations, no hidden production side effects.

## Resolve overlaps before coding
The initial tree has a few concepts that could be duplicated. Choose one canonical owner:
- Finding aggregation should have one implementation (prefer `governance/finding_aggregator.py` or `verification/finding_aggregator.py`, not both).
- Policy versioning should be represented in models and managed by one service.
- Review routing should not be duplicated between frontend and backend.
- Risk scoring is a backend source of truth; the frontend only displays its result.
- Audit logs are Phase (2) unless required by a specific core acceptance criterion; basic review history remains Phase (1).

## File implementation rule
Before implementing a module, define its inputs, outputs, errors, dependencies and tests. Avoid empty abstractions that add complexity without serving a Phase (1) workflow.
