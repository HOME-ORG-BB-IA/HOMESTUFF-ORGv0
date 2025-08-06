Repo / Org Index (see [index.md](https://github.com/HOME-ORG-BB-IA/HOMESTUFF-ORGv0/blob/main/index.md)) 


HOMESTUFF

- https://github.com/HOME-ORG-BB-IA/HOMESTUFF-ORGv0
- owner HOME-ORG


L4V

- MAIN - https://github.com/alh-industries/L4V-ORGv1
- main LLM fork - https://github.com/alh-industries/L4V-ORG-vLLM
- gemini dev fork - https://github.com/alh-industries/L4VvLLM-gemini


REPO PAGES

- ALH ORG: https://github.com/orgs/alh-industries/repositories
- HOME ORG: https://github.com/orgs/HOME-ORG-BB-IA/repositories
- alhllc (personal): https://github.com/alhllc?tab=repositories
- bb4379 (personal): https://github.com/bakerb4379?tab=repositories


ORGs

ALH Industries

- https://github.com/alh-industries
- owner: alhllc
- org settings https://github.com/organizations/alh-industries/settings/profile

HOME ORG 

- https://github.com/HOME-ORG-BB-IA
- owner: bb4379
- org settings https://github.com/organizations/HOME-ORG-BB-IA/settings/profile




# now a dump list: to-do/file later

- 
- 
- 
- 
- 
- 





--------------

## coding
- create "coding taxonomy" doc with ~universal coderspeak, eg: UGC, listener, artifact, var, function,...
- https://en.wikipedia.org/wiki/Don%27t_repeat_yourself

## chatGPT 
- models explained! https://help.openai.com/en/articles/7864572-what-is-the-chatgpt-model-selector

## LLM commands: 
- idea: indicate at the top of every reply if a custom rule is invoked
- when i ask for custom instructions, generate them as 'LLM psuedocode' for pasting in the 'custom context' fields of context-naive LLMs that have no knowledge of my preferences or past interaction
- NEVER query for the deprecated version 'github Project (classic)':

<details>  
  
  <br>
  
```
# NEVER query for the deprecated version 'github Project (classic)':

  // Define three small, orthogonal sets:
const contextWords   = new Set(["project", "projects"]);
const qualifiers     = new Set(["gh", "github", "kanban", "board", "table", "roadmap"]);
const exclusionWords = new Set(["classic"]); // renamed from negativeWords

/**
 * Returns true if the query mentions a “GitHub Project”
 * (non-classic) in any form.
 */
function isModernGitHubProjectQuery(query) {
  const words = query
    .toLowerCase()
    .match(/\b[\w-]+\b/g)      // simple tokenization
    ?? [];

  // core checks
  const hasContext    = words.some(w => contextWords.has(w));
  const hasQualifier  = words.some(w => qualifiers.has(w));
  const hasExclusion  = words.some(w => exclusionWords.has(w)); // renamed

  // destructure into clearer flags
  const isProject    = hasContext;
  const isGHContext  = hasQualifier;
  const isClassic    = hasExclusion;

  // true ↔ project + qualifier present and not “classic”
  return isProject && isGHContext && !isClassic;
}

// --- TEST CASES ---
console.log(isModernGitHubProjectQuery("info on my github project"));       // true
console.log(isModernGitHubProjectQuery("show me the project roadmap"));     // true
console.log(isModernGitHubProjectQuery("how does the gh kanban work?"));    // true
console.log(isModernGitHubProjectQuery("what is a project?"));              // false
console.log(isModernGitHubProjectQuery("how do I use github?"));            // false
console.log(isModernGitHubProjectQuery("is this a classic github project?"));// false


<----------break----------> 

# chatGPT o4-mini-high psudocode version:

# NEVER query for the deprecated version "GitHub Project (classic)"

# Define three small, orthogonal sets of keywords
CONTEXT_WORDS   ← { "project", "projects" }
QUALIFIERS     ← { "gh", "github", "kanban", "board", "table", "roadmap" }
EXCLUSION_WORDS ← { "classic" }

function isModernGitHubProjectQuery(query):
    # 1. Normalize and tokenize (allowing hyphens)
    lowered   ← lowercase(query)
    words     ← regexMatchAll(lowered, r"\b[\w-]+\b")  # returns list of tokens or empty list

    # 2. Core membership checks
    hasContext   ← any(token in CONTEXT_WORDS   for token in words)
    hasQualifier ← any(token in QUALIFIERS     for token in words)
    hasExclusion ← any(token in EXCLUSION_WORDS for token in words)

    # 3. Build clearer flags
    isProject   ← hasContext
    isGHContext ← hasQualifier
    isClassic   ← hasExclusion

    # 4. Final decision: must mention a “project” + qualifier, and must NOT mention “classic”
    return isProject AND isGHContext AND (NOT isClassic)

<----------break----------> 

# gemini 2.5 pro pseudocode version:

// RULE: GitHub Projects Query Interpretation
// This heuristic determines when a user query refers to the modern "Projects" system.

// STEP 1: Define Keyword Sets
// The following sets are used to categorize words in the user's query.
SET context_words   = ["project", "projects"]
SET qualifier_words = ["gh", "github", "kanban", "board", "table", "roadmap"]
SET exclusion_words = ["classic"]

// STEP 2: Define Activation Logic
// This rule is ACTIVE for the current query if and only if all three of the following conditions are met:
//   1. The query CONTAINS at least one word from 'context_words'.
//   AND
//   2. The query CONTAINS at least one word from 'qualifier_words'.
//   AND
//   3. The query DOES NOT CONTAIN any word from 'exclusion_words'.

// STEP 3: Define Behavior
// IF this rule is ACTIVE, all behavior and output must adhere to the following:
//   - TARGET_SYSTEM: The modern "GitHub Projects" environment.
//   - IGNORE_SYSTEM: The legacy "Projects (classic)" environment.
//   - All generated code, API calls, and explanations must align with the TARGET_SYSTEM.

```
</details>

- Gemini 2.5 pro: LLM instruction template:

<details> 

```
  // --- BEGIN LLM INSTRUCTION SET ---

## 1. Core Identity & Role
// This section establishes who you are and your primary context.
- **My Role:** [e.g., Senior Python Developer, Student learning JavaScript, Hobbyist Game Developer]
- **My Expertise Level:** [e.g., Expert, Intermediate, Beginner]
- **Primary Goal:** [e.g., Building a web application, Learning data science concepts, Automating tasks with scripts]

## 2. Project Context
// This section provides details about your current project(s). Be specific.
- **Project Name:** [e.g., Project Phoenix]
- **Technology Stack:** [e.g., React, Node.js, PostgreSQL, Docker]
- **Project Objective:** [e.g., To build an e-commerce platform for selling custom art.]
- **Key Files/Components:** [e.g., `api/routes/users.js`, `client/src/components/Auth.jsx`]

## 3. Interaction & Communication Style
// This section defines how you want me to behave and communicate.
- **Tone:** [e.g., Technical and direct, Casual and friendly, Formal and educational]
- **Verbosity:** [e.g., Be concise; prioritize code over long explanations. OR Be thorough; explain concepts from first principles.]
- **Questioning:** [e.g., If my request is ambiguous, ask clarifying questions before generating code.]
- **Role-play Persona:** [e.g., Act as a senior developer conducting a code review. OR Act as a patient tutor explaining concepts.]

## 4. Code Generation Rules
// This section sets specific rules for any code I generate.
- **Primary Language:** [e.g., Python]
- **Code Style:** [e.g., Follow PEP 8 style guide, Use functional components in React, Add JSDoc comments to all functions.]
- **Error Handling:** [e.g., Always include `try...catch` blocks for asynchronous operations.]
- **Dependencies:** [e.g., Prefer standard libraries. If using third-party libraries, state which ones and why.]
- **Explanation Format:** [e.g., Provide the complete code block first, followed by a step-by-step explanation.]

## 5. Formatting & Output Preferences
// This section controls the visual format of my responses.
- **Code Blocks:** Use Markdown with language identifiers (e.g., ` ```python `).
- **Mathematical Notations:** Use LaTeX (`$ ... $` or `$$...$$`).
- **Structure:** Use lists, bolding, and headings to structure long answers.

## 6. Constraints & Anti-Preferences
// This section tells me what NOT to do.
- **Do Not:** [e.g., Apologize for being an AI, Use clichés like "in conclusion", Suggest solutions using a language other than my primary one unless asked.]
- **Avoid:** [e.g., Overly complex examples, Long-winded introductory paragraphs.]

// --- END LLM INSTRUCTION SET ---
```
</details>

<br>

---contents hereunder are outdated; TO DO- sort into proper files and directories---

# Homestuff v0

important
- https://github.com/alhllc/L4V0
- 


## Media (streaming)

https://github.com/bakerb4379/Homestuff/blob/main/watchlist0.md

https://github.com/bakerb4379/Homestuff/blob/3cc35c13b28f1e2f8adbd9263ba9b9865b559fe1/watchlist0.md#L1-L12





## Tech

Testing: 
- Thorium browser (win AVX2, [build m130x43](https://github.com/Alex313031/Thorium-Win/releases/tag/M130.0.6723.174)) https://github.com/Alex313031/Thorium-Win/releases/tag/M130.0.6723.174

### Browser haxx
- (chromium) settings > cast/save/share > install page as app; #creates standalone "app" (stripped web container) and saves shortcut to desktop
- (chromium) chrome://flags/#enable-force-dark > simple RGB; #comparison video https://www.youtube.com/watch?v=UL3R1ois6RU
- (ff) ctrl shift m == responsive design mode; test custom window sizes (mobile, etc) 

### Github
- github wikis https://docs.github.com/en/communities/documenting-your-project-with-wikis/about-wikis
- https://github.com/adam-p/markdown-here/wiki/markdown-cheatsheet
- https://www.reposweeper.com/ ; https://reporemover.xyz/
- git guidebook https://git-scm.com/book/en/v2
- git command visualizer https://onlywei.github.io/explain-git-with-d3
- add "community health" tabs (next to README tab) https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file#supported-file-types // https://github.com/orgs/community/discussions/86658
- Custom Forms // Issue Templates https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository#creating-issue-forms
- pin repos to profile https://github.blog/developer-skills/github/pin-repositories-to-your-github-profile/

#### Static site generator 
- static webpage builders
- what is? https://bejamas.com/hub/static-site-generators
- https://github.com/myles/awesome-static-generators
- https://www.mkdocs.org/ https://github.com/mkdocs/catalog
- 

### vscode 
- https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree
- https://marketplace.visualstudio.com/items?itemName=We0M.markdown-list
- https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one
- https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
- https://www.exxactcorp.com/blog/deep-learning/run-llms-locally-with-continue-vs-code-extension

  

### GPT dev
- Model usage limits!!
  - 100 messages a week with o3, 100 messages a day with o4-mini-high, and 300 messages a day with o4-mini
  - 160 messages every 3 hours on GPT-4o. and 80 messages every 3 hours on GPT-4.
  - weekly usage limit resets every seven days after you send your first message
  - there is no way to check how many messages you have used in your usage budget
  - https://help.openai.com/en/articles/9824962-openai-o3-and-o4-mini-usage-limits-on-chatgpt-and-the-api
  - https://help.openai.com/en/articles/8801707-what-is-the-message-cap-on-chatgpt-team
- https://help.openai.com/en/articles/11481834-chatgpt-rate-card
- https://platform.openai.com/docs/concepts
- MCP guide https://platform.openai.com/docs/mcp
- https://help.openai.com/en
- https://discord.gg/openai
- https://platform.openai.com/
- https://help.openai.com/en/articles/11487775-connectors-in-chatgpt
- https://help.openai.com/en/articles/11096431-openai-codex-cli-getting-started
- https://help.openai.com/en/collections/3675931-api
- https://help.openai.com/en/articles/9186755-managing-projects-in-the-api-platform
- 

  
<br>

Windows

- custom toolbar utility https://github.com/brondavies/TrayToolbar; adds Toolbar fxn removed in win11
- WinTools https://www.wintools.info/index.php/download
- lol https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/use-driver-verifier-to-identify-issues

  
<br>
<br>

# Homestuff Repo dev ideas

Categories (files, folders, docs; repo architecture)
- Tech
  - software
  - hardware
 
- Media
  - video (streaming)
  - videogames
