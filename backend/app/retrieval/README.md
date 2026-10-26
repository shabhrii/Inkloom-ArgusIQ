# Approved-source retrieval

Start with PostgreSQL full-text/keyword search and metadata filtering. Store source identity, authority, scope and effective date when available. Retrieval must respect organization scope and applicable product/channel/locale. Vector and hybrid retrieval are Phase (2), reranking is Phase (3). Return source spans, not only generated summaries.

## Implementation sequence
Complete Phase (1) first. Phase (2) must be introduced one feature at a time with full regression tests after each feature. Phase (3) is optional.
