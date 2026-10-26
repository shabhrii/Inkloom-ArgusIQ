# Testing strategy

## Required before Phase (2)
- Unit tests for file validation, text extraction, terminology rules, disclosure rules, permissions and finding schemas.
- Integration test for upload → extraction → verification → persisted findings.
- Integration test for reviewer action and persisted revision/history.
- Frontend build/type checks.
- Manual test of compliant and intentionally non-compliant demo samples.

## After every Phase (2) addition
1. Run all backend tests.
2. Run frontend type checks/build and tests.
3. Run the full demo workflow.
4. Verify existing Phase (1) behavior still works.
5. Fix regressions before adding another enhancement.

## Evaluation data
Keep a small, labelled corpus with expected findings. Avoid using the same near-identical examples for both development and evaluation. Report actual measured results only, including sample size and known limitations.
