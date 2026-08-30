# MELE Reviewer

### Practice • Review • Improve

**MELE Reviewer** is an independent, offline-first Mechanical Engineering study and practice platform designed to help students organize review materials, practice questions, review formulas and concepts, track mistakes, and monitor study progress.

> **Current version: v1.2.0**

## What it includes

- **Dashboard** — overview of progress, accuracy, study sessions, and weakest topics
- **Subjects & Topics** — organized Mechanical Engineering review areas
- **Practice Arena** — subject/topic practice with recorded attempts and accuracy
- **Formula Bank** — review governing equations and engineering relationships
- **Flashcards** — concept and terminology review
- **Mistake Notebook** — keep track of questions and topics that need another look
- **My Materials** — add and organize personal reviewer material
- **Weak Topics** — identify areas that need more practice
- **Study Timer** — focused study sessions
- **Ace AI** — a local, rule-based study assistant built into the application
- **Personal design settings** — paper/linen/parchment/quiet visual styles and typography options
- **Offline/local storage** — reviewer data is designed to stay in the browser rather than requiring a backend

## Ace AI

Ace is intentionally different from a cloud AI chatbot.

In v1.2.0, Ace is a **local, rule-based study assistant**. It uses knowledge built into the HTML file and can inspect locally stored reviewer progress and mistakes. The application does not require a cloud AI service for Ace to operate.

The source includes built-in responses for MELE concepts and prompts such as:

- Explain a Mechanical Engineering concept
- Ask about formulas
- Request practice guidance
- Review weak topics
- Review local progress and recorded mistakes

Because Ace is rule-based, it does **not** have the open-ended knowledge or reasoning ability of a full external AI model.

## Offline-first architecture

The project is intentionally simple:

- HTML5
- CSS3
- Vanilla JavaScript
- SVG/text-based interface elements where appropriate
- Browser local storage for reviewer data
- No required backend
- No required account
- No required API key
- No required cloud AI service

The application is packaged as a self-contained `index.html`, making it easy to run locally or deploy through a static host such as GitHub Pages.

## Main repository structure

```text
MELE-Reviewer/
│
├── index.html
├── README.md
├── LICENSE
├── VERSION.txt
│
└── versions/
    └── v1.2.0/
        └── index.html
```

### Why keep `versions/`?

The root `index.html` is the **live/current website**.

The `versions/` directory is an archive of releases. It lets you keep older working versions without replacing or mixing them with the live site.

When a new version is released, the recommended structure is:

```text
versions/
├── v1.0.0/
│   └── index.html
├── v1.1.0/
│   └── index.html
├── v1.1.1/
│   └── index.html
├── v1.1.2/
│   └── index.html
└── v1.2.0/
    └── index.html
```

## Using the reviewer

1. Open `index.html` in a modern web browser.
2. Choose a subject or feature from the navigation.
3. Practice questions and review concepts.
4. Use the Formula Bank and Flashcards for recall.
5. Check Weak Topics and the Mistake Notebook to target areas that need improvement.
6. Use the Study Timer for focused sessions.
7. Use Ace for the built-in local study assistance.

Because much of the application state is browser-local, clearing the site's browser storage can remove saved progress and personal reviewer data.

## GitHub Pages deployment

The project can be deployed as a static GitHub Pages website.

The important file for the live page is:

```text
index.html
```

The other files are project documentation and release archives.

## Version 1.2.0

v1.2.0 introduces the **Ace AI** experience and personal design settings while retaining the single-file, offline-first architecture.

Notable v1.2.0 additions include:

- Local Ace study assistant
- Built-in MELE knowledge responses
- Local progress/mistake awareness
- Personal background/design options
- Typography options
- Expanded study-platform presentation

## Disclaimer

MELE Reviewer is an **independent educational study tool**. It is not affiliated with, sponsored by, endorsed by, or officially connected to the Professional Regulation Commission (PRC) or any government agency.

The reviewer content should be used as a supplementary study resource. Students should consult official examination announcements, syllabi, references, textbooks, instructors, and other authoritative sources when preparing for the Mechanical Engineering Licensure Examination.

## Project philosophy

The application follows a simple study loop:

**Learn → Apply → Repair**

- **Learn:** understand definitions, formulas, assumptions, units, and physical meaning.
- **Apply:** practice numerical problems and engineering situations.
- **Repair:** use mistakes and weak-topic data to decide what deserves another review.

---

**MELE Reviewer — Practice • Review • Improve**
