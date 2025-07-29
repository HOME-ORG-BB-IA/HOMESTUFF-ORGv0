# ✅ TO DO LISTER – Vision & Architecture  
*Version: 1.2*  
*Date: 2025-07-19*  

A foundational document outlining the design goals, functionality, and behavioral philosophy for the “TO DO LISTER” task management system. This app is built around solving fragmentation, automating capture, and using AI to reduce cognitive load in managing personal task workflows.

---

## 🧠 Concept Summary

TO DO LISTER is a custom-built to-do list system designed to:

- Eliminate the fragmentation of tasks across multiple apps  
- Use LLM input (preferably voice) as the **main task capture method**  
- Log and store all tasks in markdown files (buffer + sorted)  
- Organize intelligently across multiple lists without user overthinking  
- Present all lists in a single unified view with expandable modules  
- Optionally sync to passive displays (e.g. e-ink panels)  
- Enable future expansions like gamification and analytics  

---

## 🎤 1. Input System – Voice-Driven Capture

- Tasks are **spoken aloud** using a phone or small hardware device (e.g. Raspberry Pi, M5Stack, Arduino)  
- Audio is processed by an **LLM** (likely ChatGPT or local deployment)  
- LLM:  
  - Converts speech to text  
  - Parses the task structure (main task, subtasks, category, priority)  
  - Saves the task in a central buffer file in markdown format  

---

## 📝 2. Buffer File → Intelligent Sorting

- Captured tasks first go into a **staging buffer.md file**  
- A parser (via LLM or automation) then reads and:  
  - Analyzes intent and structure  
  - Sorts task(s) into appropriate markdown-based lists  
    - E.g. `Microtasks.md`, `Errands.md`, `LabTasks.md`  
    - Subtasks nested appropriately  
- Reduces decision fatigue by eliminating manual organization at capture time  

---

## 🧰 3. GitHub-Based Architecture

- All markdown files are stored in a **GitHub repo**  
- GitHub acts as a:  
  - File host  
  - Version control layer  
  - Sync backend for all devices  
- Edits and parsing flows may be automated via:  
  - GitHub Actions  
  - LLM parsing scripts  
  - Local CLI tools  

---

## 🪟 4. Unified Interface – One Panel, All Lists

> “I want to see all of my lists on a single screen or panel — no tapping into separate views unless I choose to expand one.”  

- All task lists are displayed in a **single scrollable or tiled interface**  
- Each list:  
  - Shows a summary or collapsed view  
  - Expands only when the user chooses to engage  
- UI modes:  
  - Scroll view with collapsible sections  
  - Drag-and-drop reorderable list panels  
  - Optional LLM-generated summaries per list (e.g. "3 overdue")  

---

## 🧠 5. Anti-Fragmentation Philosophy

**Problem**  
You currently face:  
- Task overload across many tools/apps  
- Overthinking where tasks should go  
- Creating too many lists  
- Losing context while browsing for where to file things  

**Design Responses**  
1. **Unify Capture**  
   → All tasks come through one input: voice/LLM  
2. **Delegate Sorting to Logic**  
   → LLM determines destination list, priority, subtask structure  
3. **Prevent List Overgrowth**  
   → Smart prompts to reduce redundant list creation  
4. **Central View, Multiple Perspectives**  
   → Lists never siloed — everything visible and filterable  
5. **Calm Review Mode**  
   → Option to review tasks in batch instead of deciding during capture  

---

## 🧮 6. Internal Architecture Notes

- The underlying data model will use **expandable arrays / modular structures**:  
  - Each list will be treated as an **array of task objects**  
  - Each task can include:  
    - Title (string)  
    - Subtasks (nested array)  
    - Tags or categories (optional)  
    - Priority or time values  
    - Metadata (created/modified/completed)  
- Subtasks will be **recursively nestable**, supporting depth without predefining limits  
- Modular structure allows:  
  - Reuse of task components across multiple lists/views  
  - References across views without duplication (e.g., a task appearing in both “Today” and “Errands”)  
  - Efficient sync and render operations (ideal for Git/markdown + UI sync)  

---

## 📺 7. Hardware Sync (Future)

- Passive display integration:  
  - E-ink screen shows task status (e.g. "Today's Tasks")  
  - Syncs to GitHub list markdown files  
  - Check off tasks via phone or physical button → syncs across system  
- Optional use of:  
  - ESP32 / M5Stack  
  - Kindle-based dashboards  
  - Custom DIY panels  

---

## 🧩 8. Tertiary Features (Optional Later)

- **Gamification**  
  - Streaks, XP, energy scores, rewards for daily completion  

- **Analytics**  
  - Completion rate over time  
  - Average task age  
  - List category balance  
  - Heatmaps of work style  

---

## 🧱 9. System Architecture Summary

| Layer           | Role                                       |
|----------------|--------------------------------------------|
| **Input**       | Voice-to-LLM (mobile or device)            |
| **Capture**     | Markdown buffer file (unfiled tasks)       |
| **Parser**      | LLM logic assigns tasks to correct lists   |
| **Storage**     | GitHub repo holding all markdown lists     |
| **Interface**   | Central app view or synced displays        |
| **Review**      | Option to approve or correct filing        |

---

## ✅ Summary of Core Principles

- **Fragmentation is the enemy** — unify capture and display  
- **LLM handles the complexity**, not the user  
- **Markdown + GitHub** offers auditability, portability, and control  
- **Visual calm** is essential — design should reduce thinking, not add to it  
- **Voice-first, logic-assisted, markdown-powered**  

---

## 🚧 Future GitHub Sections (Under Construction)

- `## LICENSE`  
  _To be added: likely MIT, GPL, or Creative Commons_

- `## CONTRIBUTING.md`  
  _To be added: contribution guidelines, formatting rules, merge strategy_

- `## SETUP / INSTALL`  
  _To be added: basic GitHub clone instructions, dependencies, markdown conventions_

- `## INTEGRATION NOTES`  
  _Planned section for hardware APIs, GitHub Actions, voice capture routing, LLM usage patterns_

- `## UI SKETCHES / WIREFRAMES`  
  _Planned visuals or text-based UI mockups for the unified list panel system_

---

## 🗂️ Proposed GitHub Repository Structure

    to-do-lister/
    │
    ├── README.md                         # Vision and architecture overview
    ├── LICENSE                           # Placeholder (e.g. MIT or GPL)
    ├── CONTRIBUTING.md                   # Contribution guidelines (TBD)
    │
    ├── /docs/                            # App planning and architectural notes
    │   ├── architecture.md
    │   ├── data-model.md
    │   └── llm-parsing-notes.md
    │
    ├── /lists/                           # Markdown-based user-facing task lists
    │   ├── microtasks.md
    │   ├── errands.md
    │   ├── lab-projects.md
    │   └── longterm.md
    │
    ├── /buffer/                          # Staging area for unfiled task input
    │   └── buffer.md
    │
    ├── /scripts/                         # Parsing, logic automation, GitHub Actions
    │   ├── parse-buffer.js
    │   └── sync-markdown.py
    │
    ├── /ui-sketches/                     # Mockups, wireframes, and layout ideas
    │   └── panel-wireframe.md
    │
    ├── /hardware-integration/           # Notes and code for display or sensor sync
    │   └── eink-sync-notes.md
    │
    └── .gitignore                        # GitHub cleanliness rules (e.g. temp files, logs)

---
