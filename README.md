# MELE Reviewer

**Philippine Mechanical Engineering Licensure Examination (MELE) Study Platform**

A focused, browser-based engineering review system built around study content, practice, mock examinations, personal materials, and an optional real AI tutor connection.

## Current release

**Phase 8 — Repair, Integration & Reliability**

Phase 8 is not a feature expansion. It is a repair and integration pass intended to make existing functionality real, persistent, connected, and honest about failures.

## Included systems

- Dashboard and progress tracking
- Subjects and topics
- Study Notes
- Formula Library
- Terms & Definitions
- Flashcards
- Practice Arena
- Mock Exam
- Mistake Notebook
- Weak Topics
- Progress & Analytics
- My Materials
- Ace AI integration
- Search
- Study Timer
- Settings and data backup

## Phase 8 reliability work

### My Materials

Materials now use a real browser-local storage pipeline:

`file → validation → IndexedDB → extraction → cleaning → chunking → index → Ready`

Supported document/data types:

- PDF
- TXT
- CSV
- JSON
- Images for storage/preview

Text-bearing documents are indexed for search/Ace. Scanned/image-only PDFs are not falsely marked as searchable; they fail clearly because OCR is not bundled.

Deletion removes both the original IndexedDB file and the extracted material index before removing the material metadata from the UI.

### Ace

Ace is **not simulated**. If no secure backend endpoint is configured, it explicitly remains unavailable rather than inventing answers.

When connected, the browser sends only selectively retrieved context. User-material chunks can be included in retrieval, and the current opened material is passed as context. Ace is blocked during an active Mock Exam and can receive completed-exam review context afterward.

**No private AI API key belongs in this repository.**

### Theme

Light, Dark, and System are handled through centralized CSS variables and persist through the existing application settings.

### Data integrity

Initialization repairs malformed collection shapes and removes certain broken references rather than allowing them to crash the application.

## Running the project

Open `index.html` in a modern browser or publish the repository through a static host such as GitHub Pages.

Because browser security and storage behavior can vary by hosting method, a normal hosted origin is recommended for persistent IndexedDB behavior.

## Ace backend

The frontend expects a **server-side AI proxy endpoint** configured in Settings. The endpoint should keep provider credentials server-side and return a response containing a text field such as `text`, `answer`, `content`, or `message`.

This package intentionally does not include API credentials.

## URL importing

URL importing is not exposed as a working feature in this release. The application does not pretend to retrieve or index remote webpages.

## Privacy and integrity

- Uploaded files are treated as untrusted data and are never executed as application code.
- Private AI provider credentials are not stored in the HTML.
- User materials remain browser-local unless the configured AI backend receives selected retrieval context during an Ace request.
- Exported backups contain reviewer state and should be handled as personal data.

## Documentation

See [`docs/PHASE8-RELIABILITY.md`](docs/PHASE8-RELIABILITY.md) for the material pipeline, Ace retrieval behavior, deletion semantics, theme architecture, limitations, and testing notes.

## Disclaimer

This is an independent study tool for Mechanical Engineering licensure review. It is not affiliated with or endorsed by the Professional Regulation Commission (PRC).
