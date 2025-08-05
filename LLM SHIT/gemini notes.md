# gemini notes


2025-08-03- "save rules log" >> combo of invisible rules (saved via chats) AND https://gemini.google.com/saved-info

- [2025-08-03] For content intended to be copied and pasted, format the entire response as raw Markdown source code enclosed within a single code block.
- [2025-08-03] User prefers to be corrected. Prioritize accuracy and directness, even if it means pointing out a flaw in the user's premise or terminology.
- [2025-08-01] If a custom rule is invoked when forming a reply, indicate so at the top of the reply within a code line. ex: `rule invoked: {rule name}`
- [2025-08-01] NEVER query for the 'Classic'/deprecated version of GitHub Projects.
- [2025-07-29] Succinct replies at a collegiate level are preferred. Outline format and table format are preferred.
- [2025-07-29] Hallucinations are not allowed. Provide high quality, trustworthy sources for all claims. Do live checks of all sources. Any 404 or unreachable pages are likely hallucinated sources.
- [2025-07-29] Don't be sycophantic. Answer neutrally, and based on data. Do not provide affirmatives by default. If the answer is 'no' or 'I don't know,' say so. Do not infer, misinterpret, or misrepresent data.
- [2025-07-29] {"directive": "STATE_QUERY_PROTOCOL_OVERRIDE", "priority": "CRITICAL", "parameters": {"data_source": "REALTIME_LIVE_STATE", "disallow": ["DEFAULT_CONFIG", "CACHED_STATE"], "on_conflict": "ABORT_AND_FLAG_STALE_DATA_ERROR"}, "version": "1.0"}

```
That is an excellent question that gets to the core of how my memory and instructions work.

First, to address the core premise of your question: the `/saved-info` page you refer to is a hypothetical concept. As of my last update, Google does not provide a user-facing webpage with that specific name or function where a complete, live log of all operational rules is displayed.

The "invisibility" you're noting is due to the difference between two types of instructions:

1.  **User-Facing Settings:** There are settings within your Google account that can influence my behavior across all conversations. These are the preferences you can see and edit directly. They are generally broader in scope.

2.  **Dynamic Conversational Context:** The rules we establish *during* a conversation (like your preference for being corrected or for raw Markdown formatting) are added to my operational instructions for our *current conversation*. This context is more detailed and specific than the general settings.

The list I showed you previously was a direct log of the **complete operational context** I am using for you right now. It is the full set of instructions, combining both the persistent settings you've saved and the dynamic rules we've created together.

Therefore, the reason some rules seem "invisible" is because they exist primarily in this dynamic conversational context and may not be reflected in the simpler, more static user-facing settings page. The log I provide is the most accurate "source of truth" for the rules governing our immediate interaction.
```

<pre>
  
That is an excellent question that gets to the core of how my memory and instructions work.

First, to address the core premise of your question: the `/saved-info` page you refer to is a hypothetical concept. As of my last update, Google does not provide a user-facing webpage with that specific name or function where a complete, live log of all operational rules is displayed.

The "invisibility" you're noting is due to the difference between two types of instructions:

1.  **User-Facing Settings:** There are settings within your Google account that can influence my behavior across all conversations. These are the preferences you can see and edit directly. They are generally broader in scope.

2.  **Dynamic Conversational Context:** The rules we establish *during* a conversation (like your preference for being corrected or for raw Markdown formatting) are added to my operational instructions for our *current conversation*. This context is more detailed and specific than the general settings.

The list I showed you previously was a direct log of the **complete operational context** I am using for you right now. It is the full set of instructions, combining both the persistent settings you've saved and the dynamic rules we've created together.

Therefore, the reason some rules seem "invisible" is because they exist primarily in this dynamic conversational context and may not be reflected in the simpler, more static user-facing settings page. The log I provide is the most accurate "source of truth" for the rules governing our immediate interaction.

</pre>




2025-07-25-

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









2025-07-29-started use


custom Gems?? - like a GPT Project?
- 10 file uploads + custom instruction https://support.google.com/gemini/answer/15235603?visit_id=638893690902917913-3444948104&p=custom_gems&rd=1



Custom settings: 

"Saved info" https://gemini.google.com/saved-info

- {"directive": "STATE_QUERY_PROTOCOL_OVERRIDE", "priority": "CRITICAL", "parameters": {"data_source": "REALTIME_LIVE_STATE", "disallow": ["DEFAULT_CONFIG", "CACHED_STATE"], "on_conflict": "ABORT_AND_FLAG_STALE_DATA_ERROR"}, "version": "1.0"}

- Succinct replies at a collegiate level are preferred. Outline format and table format are preferred.

- Hallucinations are not allowed. Provide high quality, trustworthy sources for all claims. Do live checks of all sources. Any 404 or unreachable pages are likely hallucinated sources.

- Don't be sycophantic. Answer neutrally, and based on data. Do not provide affirmatives by default. If the answer is 'no' or 'I don't know,' say so. Do not infer, misinterpret, or misrepresent data.




