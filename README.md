# MELE Ace Backend v1

Secure server-side proxy for the Phase 8 MELE Reviewer Ace integration.

## What it does

- Keeps `OPENAI_API_KEY` off the browser.
- Accepts the exact Phase 8 `POST /api/ace` payload.
- Uses the OpenAI Responses API.
- Sends Ace's system behavior separately from retrieved MELE context.
- Treats retrieved/user material as untrusted reference data.
- Blocks requests identified as an active Mock Exam.
- Applies a simple per-IP request limit.
- Limits request body size and output size.
- Supports the frontend's `connection_test` request.
- Returns `{ "text": "..." }`, which the existing Phase 8 frontend already accepts.

## Requirements

Node.js 20+.

## Local setup

1. Copy `.env.example` to `.env`.
2. Put your OpenAI API key in `.env`.
3. Start the server.

The backend intentionally has no npm dependencies. It uses Node's built-in `fetch`, so there is no SDK package that needs to be installed for v1.

Example environment:

```bash
OPENAI_API_KEY=your_key_here
OPENAI_MODEL=gpt-5.6-luna
OPENAI_REASONING_EFFORT=medium
ALLOWED_ORIGINS=*
```

Then:

```bash
node server.mjs
```

The endpoint is:

```text
http://localhost:8787/api/ace
```

Paste that endpoint into Ace's **Backend endpoint** field in the Phase 8 UI.

## Production

Deploy this backend to a server/runtime that supports Node 20+ and environment secrets. Set `ALLOWED_ORIGINS` to the exact production frontend origin rather than `*`.

Do not put `.env` in Git. Do not put the API key in `index.html`, JavaScript sent to the browser, or a public GitHub repository.
