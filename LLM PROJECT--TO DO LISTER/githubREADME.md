# TO DO LISTER

A modular, markdown-based task management system powered by AI logic and GitHub versioning. TO DO LISTER is designed to unify fragmented task capture, intelligently organize tasks using an LLM parser, and provide a calm, centralized interface for managing personal or project workflows.

---

## 🔧 Features

- Voice-first task input (via phone or hardware device)
- Tasks parsed and organized by LLM
- Markdown files as the source of truth (version-controlled in GitHub)
- Buffer → Logic → Sorted task lists pipeline
- Unified interface: see all lists in one view
- Optional hardware display syncing (e-ink, ESP32)
- Optional gamification and analytics extensions

---

## 📦 System Architecture Overview

| Layer       | Description                                      |
|------------|--------------------------------------------------|
| Input       | Voice or device capture to LLM                  |
| Capture     | Markdown buffer file (unsorted tasks)           |
| Parsing     | LLM logic assigns tasks to correct list         |
| Storage     | GitHub repo (markdown files, version control)   |
| Interface   | Central UI panel (multi-list view)              |
| Review      | Optional cleanup/approval flow per task batch   |

---

## 🗂️ Repository Structure

    to-do-lister/
    │
    ├── README.md                         # This file
    ├── LICENSE                           # License placeholder
    ├── CONTRIBUTING.md                   # Contribution guidelines (TBD)
    │
    ├── /docs/                            # Planning and architecture
    │   ├── architecture.md
    │   ├── data-model.md
    │   └── llm-parsing-notes.md
    │
    ├── /lists/                           # Final task lists in markdown
    │   ├── microtasks.md
    │   ├── errands.md
    │   ├── lab-projects.md
    │   └── longterm.md
    │
    ├── /buffer/                          # Staging area for unfiled input
    │   └── buffer.md
    │
    ├── /scripts/                         # LLM parsing logic, GitHub Actions
    │   ├── parse-buffer.js
    │   └── sync-markdown.py
    │
    ├── /ui-sketches/                     # UI mockups, layout ideas
    │   └── panel-wireframe.md
    │
    ├── /hardware-integration/           # E-ink & hardware sync notes/code
    │   └── eink-sync-notes.md
    │
    └── .gitignore                        # Cleanup rules

---

## 📌 Core Principles

- **Fragmentation is the enemy** – unify capture and display
- **Let the LLM organize** – remove cognitive load at entry
- **Markdown-first** – portable, diffable, and easy to sync
- **Review, not rework** – batch-process tasks calmly
- **Calm visual space** – one interface, multiple perspectives

---

## 🚧 Planned Enhancements

- GitHub Actions: automatic parsing/sorting on commit
- E-ink dashboard syncing with current task state
- Gamification (XP, streaks, visual momentum)
- Analytics (task completion trends, heatmaps)

---

## 📥 Setup (To Be Added)

Instructions for cloning the repo, setting up your parsing tools, and syncing lists locally.

---

## 🤝 Contributing

*Coming soon.* Interested collaborators can submit PRs or join roadmap discussions.

---

## 📄 License

To be defined. MIT or GPL likely.

