# MELE Reviewer

A clean, browser-based study platform for the Philippine Mechanical Engineering Licensure Examination (MELE).

## Current Version

**Phase 7 / v7.0.0** — final audit, analytics, data integrity, responsive UI, and reliability refinement.

## What’s Included

- Study Notes
- Formula Library
- Terms & Definitions
- Flashcards
- MELE Knowledge Base
- Practice Arena
- Mock Exam
- Ace AI tutor integration architecture
- Progress & Analytics
- Mistakes / Weak Topics tracking
- Search
- Saved items
- Study materials
- Timer
- Settings
- Import / Export and progress reset

## Important: Ace AI

Ace is intentionally **not a fake/local AI**. The frontend supports a secure server-side AI endpoint configuration. No private provider API key is embedded in the HTML.

If no endpoint is configured, Ace clearly reports that AI is not configured and does not fabricate answers.

## Project Structure

```text
MELE-Reviewer/
├── index.html                 # Main deployable application
├── README.md                  # Project documentation
├── docs/
│   └── DEVELOPMENT.md         # Development and testing notes
├── backups/
│   └── MELE-Reviewer-Phase6-backup.html
└── archive/
    ├── index_phase3.html
    ├── index_phase4.html
    └── index_phase5.html
```

## Running Locally

This project is intentionally lightweight and can run as a static website.

1. Open `index.html` in a browser, or serve the folder with a simple local HTTP server.
2. The application stores user progress in browser LocalStorage.
3. Use the built-in Export/Import functions to back up or restore application data.

For GitHub Pages, upload the contents of the project folder to a repository and use `index.html` as the site entry point.

## Data & Privacy

Study progress is stored locally in the browser. The application does not require an account for its core study features.

AI requests, when configured, are sent to the server-side endpoint configured by the user. Private AI provider credentials should remain on the server and must never be placed in `index.html`.

## Quality Notes

The Phase 7 build was checked for:

- JavaScript syntax errors
- Major-page navigation
- Search modal behavior
- Practice flow
- Mock Exam setup
- Ace unconfigured state
- Import validation logic
- Analytics rendering
- Clean-state data integrity
- Missing/duplicate question IDs
- Duplicate question text
- Mobile layout at a 390×844 viewport
- Browser page/console errors in the integration harness

The test harness used a clean LocalStorage state; it did not inspect or alter the user's personal accumulated browser data.

## Version History

- **Phase 7 / v7.0.0** — analytics, final audit, import validation, reset improvements, responsive/accessibility refinements, and reliability fixes.
- **Phase 6 / v6.0.0** — honest Ace AI architecture with secure endpoint configuration and contextual retrieval.
- **Phase 5** — Mock Exam engine and completion flow.
- **Phase 4** — Practice Arena and expanded MELE question bank.
- **Phase 3** — Knowledge base and study-content foundations.

## License

No license has been specified yet. Add a `LICENSE` file if you want to publish the project under an open-source license.
