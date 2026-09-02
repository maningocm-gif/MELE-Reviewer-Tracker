# Changelog

## Phase 8 — 8.0.0

### Reliability
- Repaired My Materials persistence around IndexedDB.
- Added real upload/validation/processing status flow.
- Added text extraction for TXT, CSV, JSON, and text-based PDFs.
- Added chunked material indexing for selective retrieval.
- Added actual material deletion of file bytes and index records.
- Added retry and honest failure states.
- Added material-aware search and Ace retrieval.
- Added current-material context for Ace.
- Added active Mock Exam protection for Ace.
- Added completed Mock Exam review context for Ace.
- Repaired centralized Light/Dark/System theme behavior and persistence.
- Added initialization cleanup for broken local relationships.
- Removed any implication of URL importing because no real URL retrieval pipeline is present.

### Integrity
- No private AI provider credentials are included.
- Uploaded content is treated as untrusted data.
- No fake AI response is generated when Ace is unconfigured or unavailable.

### Testing
- JavaScript syntax validation passes.
- Static Phase 8 reliability checks pass for the repaired pipelines.
- Browser limitations of the execution environment are documented in `docs/PHASE8-RELIABILITY.md`.
