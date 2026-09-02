# Development Notes

## Current version

Phase 8 — Repair, Integration & Reliability (`8.0.0`).

## Project shape

The main application remains a self-contained `index.html` so it can be hosted directly on GitHub Pages or another static host.

- `index.html` — current application
- `README.md` — project overview and setup
- `docs/PHASE8-RELIABILITY.md` — reliability architecture and limitations
- `backups/` — previous stable builds
- `archive/` — earlier phase builds

## Important architecture

### Reviewer state

Reviewer metadata/progress is persisted under the existing localStorage key:

`meleSeriousReviewer.v1`

### Material storage

Original files and extracted retrieval indexes are stored in IndexedDB database:

`meleReviewerFiles`

Stores:

- `files`
- `materialIndex`

Do not move original file blobs into localStorage; large files can exceed browser storage limits.

### Ace

Ace is intentionally provider-agnostic. Configure a server-side endpoint in Settings. Never put a private provider key in `index.html`.

### Themes

Theme state is one of:

- `light`
- `dark`
- `system`

Theme colors are CSS variables. The resolved theme is applied through `html[data-theme]`.

## Testing principle

Do not treat visible controls as proof of functionality. For every important change test the underlying state transition, refresh/persistence behavior, and failure path.
