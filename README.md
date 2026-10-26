# Lonerism — Inkloom AI MVP

## Purpose
Build a pre-publication brand-governance platform that checks submitted content against approved brand guidelines, facts, terminology, disclosures and assets; explains findings; suggests corrections; and supports human review.

## Mandatory implementation order
**Do not build everything at once.**

1. **Phase (1): Official requirements and core MVP**
   - Implement all `(1)` components first.
   - Make the core upload → extraction → verification → findings → human review/approval workflow work end to end.
   - Add sample data and automated tests.
   - Do not begin Phase (2) until Phase (1) is working and tested.

2. **Phase (2): The three planned improvements and reliability enhancements**
   - Implement `(2)` components one at a time.
   - After EACH `(2)` component, run backend tests, frontend checks, and the end-to-end demo.
   - Fix regressions before proceeding to the next `(2)` component.
   - Never leave the project in a broken state while adding an enhancement.

3. **Phase (3): Advanced enhancements**
   - Start only after Phase (1) and the selected Phase (2) improvements are working.
   - Build `(3)` components only if time and stability permit.
   - Keep advanced features optional and never let them break the core workflow.

## Phase legend
- `(1)` = official requirements / minimum working product
- `(2)` = proposed improvements and reliability enhancements
- `(3)` = advanced features / future scope

## Architectural rules
- Frontend: React + TypeScript + Vite.
- Backend: Python + FastAPI.
- Database: PostgreSQL; use SQLAlchemy and Alembic for persistence and migrations.
- File storage: private storage abstraction; local storage for development, private object storage when configured.
- AI: access models only through backend provider interfaces. Never expose API keys to the frontend.
- Verification: deterministic rules for exact checks; AI/RAG only for contextual checks.
- Human authority: the system suggests and explains; it must not silently publish, overwrite creator content, or change policy automatically.
- Traceability: every finding should point to its document location, applicable rule and available evidence.
- Security: validate uploads, enforce server-side authorization, keep secrets out of source control, and do not commit private user content.
- Testing: no feature is considered complete until its tests and the demo workflow pass.

## Definition of a working Phase (1) MVP
A user can sign in, configure a small set of approved rules/facts/terminology/disclosures/assets, upload supported text/PDF/DOCX content, run checks, inspect findings and evidence, preview a minimal correction, record a review decision, and see revision/approval history. The app reports unsupported or uncertain checks honestly rather than inventing evidence.

## Build discipline
1. Read the relevant folder README before implementing a component.
2. Implement the smallest complete vertical slice.
3. Add or update tests.
4. Run all tests/checks.
5. Manually verify the end-to-end workflow.
6. Update documentation and mark the feature status accurately: `implemented`, `partially implemented`, or `planned`.
7. Only then continue to the next component.

## Scope note
This repository layout is a target architecture, not a claim that every listed feature is already implemented. Some items are planned for later phases. Keep the implementation aligned with the official Inkloom problem statement and the Round 1 proposal.
