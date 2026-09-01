# MELE Reviewer

A single-file, offline-first study platform for Philippine Mechanical
Engineering Licensure Examination (MELE) review — built as one self-contained
`index.html` with no server, no external services, and no account required.
Open the file in a browser and everything (progress, mistakes, saved items,
uploaded materials) is stored locally on your device via `localStorage` and
`IndexedDB`.

## Features

- **Dashboard** — overall progress, subject breakdown, weakest topics, study
  streak, exam countdown.
- **Terms & Definitions / Formula Bank / Study Notes** — organized
  `Subject → Topic` reference library, with built-in board-review content.
- **Practice Arena** — concept, numerical, and engineering-situation questions
  by subject, topic, and difficulty.
- **Flashcards** — quick front/back review cards per topic.
- **Mock Exam** — build a custom timed multiple-choice simulation (subject,
  question count, difficulty mix, time limit).
  - Draws from built-in questions *and* your own imported problem sets, and
    deprioritizes questions you were recently given so repeated sessions
    don't just reshuffle the same small pool.
  - **↻ Take Again** reruns the same setup with a fresh, recency-aware
    question order; your previous attempt stays recorded in your
    progress/mistake history.
  - **Full Answer Review** after grading shows every question with your
    answer, the correct answer, correct/incorrect status, explanation,
    subject, and topic — so you can actually study from the exam afterward.
  - Only questions with a confirmed correct answer are eligible for Mock
    Exam; unverified imported questions stay Practice-only until you confirm
    them in Problem Set Studio.
- **Problem Set Studio** — paste real board-style problems (question text +
  A–D choices, with or without an answer key) and Ace extracts each
  multiple-choice item straight into Practice. If you supply an answer key
  (or mark the correct choice inline), the question is added as verified and
  can appear in Mock Exam. If not, it's added as **unverified** — Ace does
  not invent an answer — and you confirm the correct choice yourself with one
  click before it's eligible for grading.
- **My Materials** — drop in your own PDF / TXT / CSV / JSON / image files,
  or paste a link or raw text. Readable text is extracted automatically and
  can be distributed with one click (**Analyze with Ace**) into Terms,
  Formulas, Notes, Practice questions, Flashcards, and Engineering Situations
  — all traceable back to the source material.
- **Trash Bin** — deleting a material moves it to Trash instead of destroying
  it immediately. Restore it anytime within 30 days, or delete it
  permanently; after 30 days it's cleaned up automatically.
- **Ace** — a private, local (non-cloud) study assistant that can explain
  built-in MELE concepts, report your saved progress/weak topics, and search
  both your generated reviewer items and the raw text extracted from your
  uploaded materials. "What should I study today?"-style questions get a
  direct **Answer / Why / Tip** response built from your actual accuracy
  data, not a generic paragraph. Conversations are saved locally under
  **Chat History**, and **New Chat** starts a fresh one.
- **Settings** — appearance/theme, daily study alarm, exam date + countdown,
  backup export/import, and progress reset.

## Getting started

1. Download `index.html`.
2. Open it directly in a modern desktop or mobile browser (Chrome, Edge,
   Firefox, or Safari 16.4+ recommended — PDF text extraction relies on the
   standard `DecompressionStream` Web API).
3. That's it — no install, no build step, no internet connection required
   after the page loads.

## Data & privacy

All data stays in your browser:
- App state (progress, mistakes, saved items, settings) is stored in
  `localStorage`.
- Uploaded files are stored in `IndexedDB` (files over ~30 MB are catalogued
  by name/size only, since reliable local storage isn't guaranteed at that
  size).

Nothing is uploaded anywhere. Use **Settings → Export Backup** periodically if
you want a portable copy of your data (e.g. before clearing browser storage
or switching devices).

## Known limitations

- **PDF text extraction is best-effort and local-only.** It reads
  FlateDecode-compressed and uncompressed text streams using the browser's
  built-in `DecompressionStream` API — no external OCR or cloud service is
  used. This works well for typical text-based PDFs (e.g. exported from Word
  or LibreOffice) but:
  - **Scanned PDFs (photographed/image pages)** cannot be read — there is no
    OCR engine built into the browser. The app will label these as
    "Scanned or protected PDF — no extractable text found locally" instead of
    pretending to have read them.
  - Images are catalogued but never auto-converted to text.
  - PDFs with unusual encodings, embedded custom font mappings, or heavy DRM
    may extract partially or not at all.
- **A website URL can refuse browser access (CORS).** If "Read Link" fails,
  paste the article text into the box instead — pasted text always works.
- This is an independent, unofficial study tool. It is not affiliated with
  or endorsed by the Professional Regulation Commission (PRC).

## Project structure

```
.
├── index.html     # the entire application — UI, logic, and built-in content
├── VERSION.txt     # current version string
├── LICENSE         # MIT license
└── README.md       # this file
```

## Version

See `VERSION.txt`. Current: **1.3.4**.

## License

MIT — see `LICENSE`.
