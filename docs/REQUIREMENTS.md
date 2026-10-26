# Requirements and acceptance criteria (Phase 1)

## Official requirements
The system should:
- Import or define brand guidelines, approved facts, terminology and reusable assets.
- Review supported content formats before publication.
- Detect tone, terminology, factual/claim, visual and accessibility issues within the implemented scope.
- Explain each finding and identify the applicable guideline or approved source.
- Suggest corrections without automatically overriding the creator's intent.
- Support comments, approvals, revision history and role-based review.
- Identify recurring issues and provide useful governance insights.
- Protect confidential content and preserve human control.
- Clearly disclose use of AI and external services.

## MVP acceptance criteria
- Upload validation rejects unsupported or oversized files with a clear error.
- Text extraction results are visible or inspectable; extraction failures are reported.
- Deterministic terminology/disclosure checks produce repeatable findings.
- Claim checks use configured approved sources and can return `insufficient_evidence`.
- Each finding contains a type, location, severity, explanation, rule/source references where available, and status.
- A reviewer can accept, reject, edit, or escalate a finding.
- Decisions and revisions are persisted.
- Unauthorized users cannot access protected data or perform restricted actions.
- Demo seed data produces both compliant and non-compliant examples.
- Tests and a documented local run procedure exist.

## Do not claim
Do not claim comprehensive visual compliance, production-grade security, calibrated confidence, or measured accuracy unless implemented and tested. Label planned or partial functionality honestly.
