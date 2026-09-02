# Phase 8 — Repair, Integration & Reliability

## Scope

Phase 8 is a reliability pass over the existing MELE Reviewer. It does not add a new major study module.

### Repaired systems

- **Materials:** real browser-local file storage through IndexedDB, validation, processing states, text extraction, chunking/indexing, retry, and actual deletion of both file bytes and retrieval index.
- **PDF processing:** text extraction uses PDF.js loaded only when a PDF is processed. Image-only/scanned PDFs fail honestly instead of being marked ready.
- **Material retrieval:** indexed material chunks are retrieved selectively for Ace and search. Deleted materials are removed from retrieval because their metadata and index are deleted.
- **Current material context:** opening a material establishes current-material context for Ace.
- **Practice/Mock safety:** Ace is blocked while a Mock Exam is active. Completed Mock Exam review context can be passed to Ace.
- **Theme:** Light/Dark/System are centralized through CSS variables and `data-theme`. System follows the OS preference; the chosen setting persists in the existing reviewer state.
- **Data repair:** malformed collection shapes are normalized, saved-item references are cleaned, and invalid mistake/question relationships are filtered during initialization.
- **Failure handling:** upload/extraction/deletion failures remain visible and are not falsely reported as successful.

## Storage model

The application uses two layers:

1. `localStorage` stores reviewer metadata, progress, settings, history, and material metadata.
2. IndexedDB database `meleReviewerFiles` stores original file blobs and a `materialIndex` object store containing extracted text/chunks.

This separation avoids putting large original files into `localStorage`.

## Material pipeline

```text
Selected file
  ↓
Validation
  ↓
IndexedDB file storage
  ↓
Processing
  ↓
Parser / extractor
  ↓
Text cleaning
  ↓
Chunking
  ↓
IndexedDB materialIndex
  ↓
Ready
  ↓
Selective Ace/search retrieval
```

If any required processing step fails, the material remains in the library with `Failed` status and an error message.

## Deletion pipeline

```text
Delete → confirmation → delete original blob → delete material index →
remove metadata → clear current-material context → save → rerender
```

The UI is not allowed to claim deletion success if the underlying storage operation fails.

## Ace architecture

Ace remains an external AI integration. The HTML file does **not** contain a private provider API key.

The browser sends a selective payload to the configured server-side endpoint containing:

- recent conversation messages
- current page/context
- relevant built-in reviewer context
- relevant indexed user-material chunks
- relevant practice/mock context
- performance context only when relevant
- source-honesty and numerical-checking instructions

If no endpoint is configured, Ace does not fabricate a response.

A secure server-side endpoint is still required for actual provider communication. This package intentionally contains no user API credentials.

## URL importing

There is no URL-import workflow in this build. The interface does not pretend that a URL was retrieved or indexed.

## Known limitation

Browser-local processing cannot perform OCR for scanned/image-only PDFs in this build. Such PDFs are rejected from the `Ready`/indexed state rather than silently treated as searchable material.

## Validation performed

- JavaScript syntax check: PASS (`node --check`).
- Static Phase 8 audit: PASS for required material storage/index/delete functions, theme functions, Ace retrieval integration, and mock-exam safety guard.
- The test environment used for prior browser audits blocks direct `file://`/local web navigation and therefore cannot provide a trustworthy full-browser persistence test against the user's actual browser storage. Do not interpret environment-level tests as proof of personal stored data behavior.
