# Projects Handbook
### *Unified Operational Guide for CIOs, Engineers, and Non‑Developers*  
### *Using `project_instructions.txt` + `INSTRUCTIONS.md`*

---

## Table of Contents

1. [Introduction](#1-introduction)

2. [How Claude Projects Actually Works](#2-how-claude-projects-actually-works)  
   - [2.1 Files Are Stored Server‑Side](#21-files-are-stored-server-side)  
   - [2.2 Project Instructions Are Auto‑Loaded](#22-project-instructions-are-auto-loaded)  
   - [2.3 Claude Uses a Prioritised Context Model](#23-claude-uses-a-prioritised-context-model)  
   - [2.4 Claude Does Not "Remember Everything"](#24-claude-does-not-remember-everything)  
   - [2.5 Claude Is Most Efficient When Tasks Are Small](#25-claude-is-most-efficient-when-tasks-are-small)

3. [Understanding Token Usage](#3-understanding-token-usage)  
   - [3.1 Full‑File Regeneration](#31-full-file-regeneration)  
   - [3.2 Brainstorming Inside the Project](#32-brainstorming-inside-the-project)  
   - [3.3 Long Conversations](#33-long-conversations)  
   - [3.4 Re‑Explaining Context](#34-re-explaining-context)  
   - [3.5 Re‑Uploading Files](#35-re-uploading-files)

4. [Understanding the Context Window](#4-understanding-the-context-window)  
   - [4.1 What the Context Window Is](#41-what-the-context-window-is)  
   - [4.2 How Claude Manages Context](#42-how-claude-manages-context)  
   - [4.3 How Context Overload Increases Token Usage](#43-how-context-overload-increases-token-usage)  
   - [4.4 Warning Signs of Context Overload](#44-warning-signs-of-context-overload)  
   - [4.5 How to Reset Context Safely](#45-how-to-reset-context-safely)  
   - [4.6 How to Prevent Context Overload](#46-how-to-prevent-context-overload)  
   - [4.7 Best Practices for Long‑Running Projects](#47-best-practices-for-long-running-projects)

5. [Your Instruction System](#5-your-instruction-system)  
   - [5.1 `project_instructions.txt`](#51-project_instructionstxt)  
   - [5.2 `INSTRUCTIONS.md`](#52-instructionsmd)  
   - [5.3 Roles](#53-roles)  
   - [5.4 Workflow Modes](#54-workflow-modes)  
   - [5.5 Design Versioning](#55-design-versioning)  
   - [5.6 Improvements Tracking](#56-improvements-tracking)  
   - [5.7 Architecture Summaries](#57-architecture-summaries)  
   - [5.8 Claude Code Handoff](#58-claude-code-handoff)

6. [Design Completeness Rule](#6-design-completeness-rule)  
   - [6.1 Why This Rule Exists](#61-why-this-rule-exists)  
   - [6.2 What Must Be Resolved Before Design](#62-what-must-be-resolved-before-design)  
   - [6.3 How to Handle Genuinely Unknown Items](#63-how-to-handle-genuinely-unknown-items)  
   - [6.4 What Is Not Permitted](#64-what-is-not-permitted)  
   - [6.5 How This Affects the Architect Workflow](#65-how-this-affects-the-architect-workflow)

7. [Starting a New Project](#7-starting-a-new-project)  
   - [7.1 Upload Your Files](#71-upload-your-files)  
   - [7.2 Confirm Project Instructions Are Loaded](#72-confirm-project-instructions-are-loaded)  
   - [7.3 Send the First Message](#73-send-the-first-message)  
   - [7.4 Confirm the Architecture](#74-confirm-the-architecture)  
   - [7.5 Move to STRATEGIST Mode](#75-move-to-strategist-mode)  
   - [7.6 Initiate the Claude Code Handoff](#76-initiate-the-claude-code-handoff)

8. [Working With Claude Effectively](#8-working-with-claude-effectively)  
   - [8.1 The "Feature‑First" Workflow](#81-the-feature-first-workflow)  
   - [8.2 The "Explain Before You Change" Rule](#82-the-explain-before-you-change-rule)  
   - [8.3 Keeping Claude Anchored to Instructions](#83-keeping-claude-anchored-to-instructions)

9. [Requesting Changes](#9-requesting-changes)  
   - [9.1 New Feature Request](#91-new-feature-request)  
   - [9.2 Reverse‑Engineering](#92-reverse-engineering)  
   - [9.3 Architecture Changes](#93-architecture-changes)  
   - [9.4 Documentation Updates](#94-documentation-updates)

10. [Managing Large Projects](#10-managing-large-projects)  
    - [10.1 Architecture Summaries](#101-architecture-summaries)  
    - [10.2 Design Versioning](#102-design-versioning)  
    - [10.3 Improvements Tracking](#103-improvements-tracking)  
    - [10.4 Snapshots](#104-snapshots)  
    - [10.5 Checkpoints](#105-checkpoints)  
    - [10.6 Resetting Context Safely](#106-resetting-context-safely)  
    - [10.7 Avoiding Drift in Large Projects](#107-avoiding-drift-in-large-projects)

11. [Troubleshooting & Recovery](#11-troubleshooting--recovery)  
    - [11.1 Claude Rewrote a Document Unexpectedly](#111-claude-rewrote-a-document-unexpectedly)  
    - [11.2 Claude Forgot the Architecture](#112-claude-forgot-the-architecture)  
    - [11.3 Claude Hallucinated File Structure](#113-claude-hallucinated-file-structure)  
    - [11.4 Claude Is Asking for Files That Exist](#114-claude-is-asking-for-files-that-exist)  
    - [11.5 Claude Is Contradicting Earlier Decisions](#115-claude-is-contradicting-earlier-decisions)  
    - [11.6 Claude Is Drifting From Instructions](#116-claude-is-drifting-from-instructions)  
    - [11.7 Claude Left Open Questions in a Design](#117-claude-left-open-questions-in-a-design)

12. [Working With Claude Code](#12-working-with-claude-code)  
    - [12.1 What Claude Code Receives](#121-what-claude-code-receives)  
    - [12.2 Setting Up CLAUDE.md](#122-setting-up-claudemd)  
    - [12.3 Starting a Claude Code Session](#123-starting-a-claude-code-session)  
    - [12.4 Assigning a Task](#124-assigning-a-task)  
    - [12.5 Reviewing Claude Code Output](#125-reviewing-claude-code-output)  
    - [12.6 When Claude Code Discovers a Gap](#126-when-claude-code-discovers-a-gap)  
    - [12.7 Keeping CLAUDE.md Current](#127-keeping-claudemd-current)  
    - [12.8 The Full Lifecycle Loop](#128-the-full-lifecycle-loop)

13. [Glossary](#13-glossary)

---

# 1. Introduction

This handbook is a **complete operational guide** for using Claude Projects to build, rebuild, customise, and maintain software systems — even if you are not a developer.

It is written for:

- **CIOs** who need predictable, efficient AI‑assisted development  
- **Engineers** who want a structured, low‑risk workflow  
- **Non‑developers** who want to build applications without drowning in code  

This document explains:

- How Claude Projects works  
- How to use your instruction system correctly  
- How to avoid hitting weekly limits  
- How to avoid context‑window drift  
- How to request changes safely  
- How to manage large projects  
- How to troubleshoot issues  
- How to keep Claude predictable and efficient  
- How Claude Code receives and uses the approved design documents  

It is designed to work **100% in tandem** with:

- `project_instructions.txt`  
- `INSTRUCTIONS.md`  
- `Handoff.md`  

These files define how Claude behaves.  
This handbook defines how **you** use Claude.

Together, they form a complete, repeatable, scalable development workflow.

---

# 2. How Claude Projects Actually Works

Claude Projects is not just a chat.  
It is a **persistent workspace** where Claude:

- Stores files  
- Remembers project structure  
- Loads instructions automatically  
- Maintains context across sessions  
- Understands the codebase holistically  

Understanding how Projects mode works helps you avoid unnecessary token usage and prevents Claude from drifting.

---

## 2.1 Files Are Stored Server‑Side

When you upload files to a Project:

- Claude stores them permanently  
- Claude can reference them without re‑uploading  
- Claude does not need you to paste content repeatedly  

This is why Projects mode is dramatically more efficient than normal chats.

---

## 2.2 Project Instructions Are Auto‑Loaded

Claude automatically loads:

- `project_instructions.txt` every message  
- Any files you explicitly reference  
- Any files Claude needs to complete a task  

This means:

- You do not need to restate instructions  
- You do not need to remind Claude of roles  
- You do not need to re‑explain workflow modes  

But it also means:

- If the conversation gets too long, Claude may re‑interpret instructions  
- If context overload occurs, Claude may drift  

---

## 2.3 Claude Uses a Prioritised Context Model

Claude prioritises:

1. Your latest message  
2. The active task  
3. Relevant files  
4. Project instructions  
5. Recent conversation history  
6. Older conversation history (compressed)

This is why short, clear messages work best and long conversations cause drift.

---

## 2.4 Claude Does Not "Remember Everything"

Claude does **not** store:

- Past conversations  
- Past chats  
- Past Projects  
- Past instructions outside the Project  

Only the **current Project** persists.

This is why:

- You must keep all important information inside the Project  
- Architecture summaries matter  
- Design documents matter  
- Improvements.md matters  

---

## 2.5 Claude Is Most Efficient When Tasks Are Small

Claude performs best when:

- Tasks are broken into micro‑tasks  
- Only relevant files are touched  
- Only necessary content is generated  

---

# 3. Understanding Token Usage

Token usage is influenced by:

- How much text Claude reads  
- How much text Claude writes  
- How often Claude re‑reads files  
- How often Claude re‑summarises context  
- How often Claude re‑anchors to instructions  

---

## 3.1 Full‑File Regeneration

**High cost.** Use only when:

- Creating new files  
- Replacing legacy files  
- Rewriting files under ~200 lines  
- Performing major refactors  

Avoid when making small changes.

---

## 3.2 Brainstorming Inside the Project

**Very high cost.** When you brainstorm inside a Project, Claude loads the entire project context and tries to relate ideas to existing documents.

**Solution:** Do all brainstorming in a **separate chat**, then bring the final decision into the Project.

---

## 3.3 Long Conversations

**High cost.** As conversations grow, Claude compresses older messages, re‑summarises context, and may re‑read files.

**Solution:** Reset context every **20–30 messages**.

---

## 3.4 Re‑Explaining Context

**Moderate to high cost.** Use:

```
<task>Re-anchor to instructions.</task>
<constraints>
- Summarise the architecture
- Summarise the current task
</constraints>
```

---

## 3.5 Re‑Uploading Files

**Very high cost.** Never re‑upload files unless they changed outside Claude.

---

# 4. Understanding the Context Window

The context window is the **maximum amount of information Claude can hold at once**. When the window fills, Claude must compress older content, which leads to drift, mistakes, and token spikes.

---

## 4.1 What the Context Window Is

Claude can only hold a certain amount of text in memory at once — your messages, Claude's messages, loaded files, instructions, summaries, and code. When the window fills, Claude compresses older content, losing detail and causing drift.

---

## 4.2 How Claude Manages Context

Claude prioritises:

1. Your latest message  
2. The active task  
3. Relevant files  
4. Project instructions  
5. Recent conversation  
6. Older conversation (compressed)

---

## 4.3 How Context Overload Increases Token Usage

When Claude's context window fills, Claude must re‑summarise, re‑interpret instructions, re‑read files, and re‑anchor architecture. Each operation consumes tokens.

---

## 4.4 Warning Signs of Context Overload

You will notice overload when Claude:

- Asks questions it already asked  
- Forgets architecture  
- Misinterprets instructions  
- Asks for files that exist  
- Contradicts earlier decisions  
- Starts hallucinating file structure  

When you see these signs, reset context immediately.

---

## 4.5 How to Reset Context Safely

```
<task>Reset context.</task>
<constraints>
- Reload project_instructions.txt
- Do not re-read all files
- Ask me what we are working on before proceeding
</constraints>
```

Then:

```
<task>Re-anchor to instructions.</task>
<constraints>
- Summarise the architecture
- Summarise the current task
- Wait for my confirmation before proceeding
</constraints>
```

---

## 4.6 How to Prevent Context Overload

- Reset every 20–30 messages  
- Keep tasks small  
- Avoid long back‑and‑forths  
- Move brainstorming to a separate chat  
- Keep architecture summaries updated  

---

## 4.7 Best Practices for Long‑Running Projects

- Use snapshots before major changes  
- Keep Design‑vX.md updated  
- Keep Improvements.md updated  
- Reset context regularly  
- Re‑anchor Claude after resets  
- Avoid mixing exploration with planning  
- Keep messages short and clear  

---

# 5. Your Instruction System

Your instruction system is the backbone of your workflow. It ensures Claude behaves consistently, predictably, and safely.

---

## 5.1 `project_instructions.txt`

This file is:

- Loaded automatically every message  
- The "operating system" for Claude  
- The source of truth for roles and workflow  
- The behavioural contract Claude must follow  

---

## 5.2 `INSTRUCTIONS.md`

This file is:

- Loaded only when you tell Claude to use it  
- A detailed reference for templates and workflows  
- A library of reusable structures  

Invoke it with:

```
Use the template from INSTRUCTIONS.md.
```

---

## 5.3 Roles

### **ARCHITECT**
- No code  
- High‑level design  
- System structure  
- Architecture decisions  
- Data models  
- Security model  

### **STRATEGIST**
- No code  
- Task planning  
- Feature breakdown  
- Prioritisation and sequencing  
- Dependency mapping  

Switch roles with:

```
Act as ARCHITECT.
Act as STRATEGIST.
```

---

## 5.4 Workflow Modes

Claude determines the mode at project start:

- Greenfield  
- Brownfield (design exists)  
- Brownfield (no design — reverse‑engineering)  
- Redesign  
- Continuous Improvement  

---

## 5.5 Design Versioning

Design documents follow:

- `Design‑v1.md`  
- `Design‑v2.md`  
- `Design‑v3.md`  

Each version is a stable, locked reference. Never modified after approval.

---

## 5.6 Improvements Tracking

`Improvements.md` tracks:

- Feature requests  
- Bug fixes  
- Refactors  
- Technical debt  
- Architecture changes  

Claude Code reads this for task‑level execution.

---

## 5.7 Architecture Summaries

Architecture summaries:

- Keep Claude anchored  
- Reduce context load  
- Prevent drift  
- Provide a stable reference  

Update them after major changes.

---

## 5.8 Claude Code Handoff

When design and planning documents are approved, they are handed off to Claude Code for implementation. Claude Code reads the approved documents from the project folder and derives all architectural context from them.

See `Handoff.md` for the full boundary definition, folder structure, and Claude Code operating sequence.

---

# 6. Design Completeness Rule

This is one of the most important rules in the system. More complete designs produce better results in Claude Code with fewer questions and corrections.

---

## 6.1 Why This Rule Exists

A design document with open questions or vague placeholders produces:

- More clarification questions from Claude Code during implementation  
- Higher risk of Claude Code making incorrect assumptions  
- More back-and-forth between Projects and Claude Code  
- Lower quality output  

Every question resolved at the design stage saves multiple questions and corrections at the implementation stage.

---

## 6.2 What Must Be Resolved Before Design

The ARCHITECT must resolve **all** of the following before producing a design document for approval:

- All functional requirements  
- All non‑functional requirements  
- Technology choices  
- Security model  
- Data model  
- API contracts  
- Deployment model  
- Integration points  
- Constraints  

If any of these are unknown, the ARCHITECT must continue asking questions until they are resolved.

---

## 6.3 How to Handle Genuinely Unknown Items

Some items genuinely cannot be determined until the build begins — for example, exact performance thresholds that will be measured during load testing, or third-party API response formats that will be confirmed during integration.

These are the only items permitted in the **Placeholders** section of a design document.

Each placeholder **must** include all four fields:

| Field | Description |
|---|---|
| **What** | Exactly what is unknown or deferred |
| **Why** | Why it cannot be resolved before the build begins |
| **When** | The specific build stage or trigger that will resolve it |
| **Interim assumption** | The assumption the design makes until it is resolved |

If the user cannot provide an answer, the ARCHITECT must:

1. Propose a concrete, reasoned recommendation  
2. State the rationale clearly  
3. Ask the user to accept or reject it  

The design proceeds with the accepted recommendation. It does not proceed with a blank.

---

## 6.4 What Is Not Permitted

The following are **not permitted** in any design document:

- "TBD"  
- "To be determined"  
- "To be confirmed"  
- "This will be decided later"  
- Blank fields  
- Vague references to future decisions  

A design with any of these is incomplete and must not be approved or locked.

---

## 6.5 How This Affects the Architect Workflow

The requirements-gathering phase is the primary mechanism for resolving all questions. The ARCHITECT must not begin writing a design document until the requirements phase is complete and all ambiguities are resolved.

If a new question arises during drafting, the ARCHITECT must pause, ask the user, and wait for a response before continuing.

This may feel slower at the design stage. It is significantly faster overall.

---

# 7. Starting a New Project

---

## 7.1 Upload Your Files

Upload:

- Existing codebase (if any)  
- Documentation  
- Architecture diagrams  
- Requirements  
- Design documents  
- Data samples  
- Anything Claude must reference  

**Do NOT upload:**

- Large binaries  
- Node_modules or vendor folders  
- Build artifacts  
- Logs  
- Temporary files  

---

## 7.2 Confirm Project Instructions Are Loaded

Claude automatically loads `project_instructions.txt` every message. You do not need to paste instructions manually.

---

## 7.3 Send the First Message

```
<context>
We are starting a new project.
Project type: [greenfield / brownfield / rebuild / reverse-engineering]
High-level goal: [describe the outcome]
Initial scope: [describe what we want to achieve first]
Files uploaded: [list them or say "uploaded"]
</context>

<role>ARCHITECT</role>

<task>Confirm the project type and begin requirements gathering.</task>

<constraints>
- Do not produce a design document until all requirements are resolved
- Ask clarifying questions until every requirement is known
- Wait for my confirmation before proceeding
</constraints>
```

---

## 7.4 Confirm the Architecture

Claude will respond with a requirements summary and questions. Answer all questions. Claude will not produce a design document until all questions are resolved.

Once the design is produced:

- Review carefully  
- Check that no "TBD" or open questions appear  
- Confirm or correct  

If correct:

```
<task>Confirmed. Lock Design-v1.md as the approved baseline architecture.</task>
```

---

## 7.5 Move to STRATEGIST Mode

```
<role>STRATEGIST</role>
<task>Review the approved Design-v1.md and produce Improvements.md.</task>
<constraints>
- Align all items with the active design
- Wait for my confirmation before finalising
</constraints>
```

---

## 7.6 Initiate the Claude Code Handoff

```
<context>Design and planning documents are approved and locked.</context>
<task>Confirm the handoff folder is ready for Claude Code.</task>
<constraints>Follow the process defined in Handoff.md.</constraints>
```

Claude Code will then read the documents from the project folder.

---

# 8. Working With Claude Effectively

---

## 8.1 The "Feature‑First" Workflow

Every task should begin with:

- The feature  
- The behaviour  
- The user outcome  
- The acceptance criteria  

Never begin with implementation details. Claude must understand the intent before touching any document.

---

## 8.2 The "Explain Before You Change" Rule

Before Claude modifies any document, it must:

1. Explain the change  
2. Identify the affected sections  
3. Wait for your approval  

This prevents accidental rewrites and misinterpretation.

---

## 8.3 Keeping Claude Anchored to Instructions

If Claude drifts:

```
<task>Re-anchor to instructions.</task>
<constraints>
- Summarise the architecture
- Summarise the current task
- Wait for my confirmation before proceeding
</constraints>
```

---

# 9. Requesting Changes

---

## 9.1 New Feature Request

```
<context>
Feature: [describe the feature]
User outcome: [describe what the user experiences]
Acceptance criteria:
- [criterion 1]
- [criterion 2]
</context>

<role>STRATEGIST</role>

<task>Assess the architectural impact and add this feature to Improvements.md.</task>

<constraints>
- Align with the active Design-vX.md
- Do not treat as approved until I confirm
- Wait for my confirmation
</constraints>
```

---

## 9.2 Reverse‑Engineering

```
<context>File to analyse: [file path]</context>

<role>ARCHITECT</role>

<task>Reverse-engineer the specified file.</task>

<format>
- Summary of the file
- Purpose and how it fits the system
- Identified risks or issues
</format>
```

---

## 9.3 Architecture Changes

```
<context>
Change: [describe the change]
Reason: [why this change is needed]
Expected impact: [what will be affected]
</context>

<role>ARCHITECT</role>

<task>Assess the architectural implications and propose an updated architecture.</task>

<constraints>
- Resolve all questions before producing a draft
- Do not submit a design with unresolved questions
- Wait for my confirmation
</constraints>
```

---

## 9.4 Documentation Updates

```
<context>
File: [path]
Change required: [describe the change]
</context>

<task>Explain the proposed change and wait for my confirmation before modifying anything.</task>
```

---

# 10. Managing Large Projects

---

## 10.1 Architecture Summaries

Architecture summaries should include:

- High‑level system overview  
- Module breakdown  
- Data flow  
- Key dependencies  
- Integration points  
- Known constraints  
- Known risks  

Update when major features are added, redesigns occur, or new design versions are created.

---

## 10.2 Design Versioning

Design documents are **immutable snapshots** of the system's architecture at a point in time.

- `Design‑v1.md` — initial architecture  
- `Design‑v2.md` — after major refactor  
- `Design‑v3.md` — after new subsystem added  

Never modify a design document after approval. Always create a new version for major architectural changes.

---

## 10.3 Improvements Tracking

`Improvements.md` tracks features, fixes, refactors, technical debt, and architecture changes. Each entry should include description, priority, impact, dependencies, and status. Claude Code uses this for task‑level execution.

---

## 10.4 Snapshots

Snapshots are point‑in‑time captures of architecture, key files, requirements, and decisions. Use before major changes, refactors, or subsystem rewrites.

---

## 10.5 Checkpoints

Checkpoints are lightweight summaries of what was done, what is next, what changed, and what remains. Use at the end of each task or sprint, and after context resets.

---

## 10.6 Resetting Context Safely

```
<task>Reset context.</task>
<constraints>
- Reload project_instructions.txt
- Do not re-read all files
- Ask me what we are working on before proceeding
</constraints>
```

Then:

```
<task>Re-anchor to instructions.</task>
<constraints>
- Summarise the architecture
- Summarise the current task
- Wait for my confirmation before proceeding
</constraints>
```

---

## 10.7 Avoiding Drift in Large Projects

- Keep messages short  
- Keep tasks small  
- Use architecture summaries  
- Use design versioning  
- Use checkpoints  
- Reset context regularly  

---

# 11. Troubleshooting & Recovery

---

## 11.1 Claude Rewrote a Document Unexpectedly

**Symptoms:** Entire document replaced, unrelated sections modified.

**Fix:**
```
Stop.
Re-anchor to instructions.
Revert to the approved version.
Summarise the intended change only.
```

**Prevention:** Always request a summary of changes before Claude modifies any document.

---

## 11.2 Claude Forgot the Architecture

**Symptoms:** Incorrect assumptions, missing components, wrong file references.

**Fix:**
```
<task>Re-anchor to instructions.</task>
<constraints>
- Summarise the architecture
- Summarise the current task
- Wait for my confirmation before proceeding
</constraints>
```

**Prevention:** Reset context every 20–30 messages. Maintain architecture summaries.

---

## 11.3 Claude Hallucinated File Structure

**Symptoms:** References to files that don't exist, incorrect paths, invented modules.

**Fix:**
```
List all files in the project.
Correct the file map.
Re-anchor to instructions.
```

**Prevention:** Keep file maps updated. Use architecture summaries.

---

## 11.4 Claude Is Asking for Files That Exist

**Symptoms:** "Please upload X", "I cannot find Y".

**Fix:**
```
Reset context.
Reload project_instructions.txt.
Ask me what we are working on.
```

---

## 11.5 Claude Is Contradicting Earlier Decisions

**Symptoms:** Changing requirements, changing architecture, changing naming conventions.

**Fix:**
```
Refer to Design-vX.md.
Re-anchor to instructions.
Summarise the architecture.
```

---

## 11.6 Claude Is Drifting From Instructions

**Symptoms:** Ignoring workflow rules, generating content prematurely, skipping approval steps.

**Fix:**
```
Re-anchor to instructions.
Summarise the workflow rules.
Wait for my confirmation.
```

---

## 11.7 Claude Left Open Questions in a Design

**Symptoms:** "TBD" fields, blank sections, vague statements like "to be decided later".

**Cause:** ARCHITECT did not complete requirements gathering before drafting.

**Fix:**
```
Stop.
This design is incomplete.
Return to requirements gathering.
Resolve all open questions before producing a new draft.
Do not resubmit until all fields are complete or marked as explicit placeholders
with What, Why, When, and Interim Assumption fields completed.
```

**Prevention:** Never approve a design with unresolved questions. Enforce the Design Completeness Rule before locking any document.

---

# 12. Quick‑Use Cheat Sheet

See `Projects Cheatsheet.md` for the fast-reference operational guide.

---

# 12. Working With Claude Code

This section explains how to operate Claude Code once the handoff documents are ready. It covers session setup, task assignment, how to handle discoveries, and how the two tools work together across a project lifecycle.

---

## 12.1 What Claude Code Receives

Claude Code reads the following files from the project folder. These are produced and approved in Claude Projects before any implementation begins:

| File | What Claude Code uses it for |
|---|---|
| Design-vX.md (active version) | Architecture source of truth — governs all implementation decisions |
| Improvements.md | Task list, sequencing, and acceptance criteria |
| CLAUDE.md | Persistent operating instructions for Claude Code |
| Handoff.md | Boundary rules and conflict resolution |
| Supporting docs | Additional context (gap analysis, migration plans) |

Claude Code does not accept verbal architecture instructions. It derives all context from documents. If the documents are incomplete or ambiguous, Claude Code will ask — not assume.

---

## 12.2 Setting Up CLAUDE.md

`CLAUDE.md` is Claude Code's equivalent of `project_instructions.txt`. It is loaded at the start of every Claude Code session and defines how it behaves, what it reads, and what it must not do without user approval.

**To set it up:**

1. Copy `CLAUDE.md` from the Claude Projects file set into the root of your codebase
2. Update the `<version_reference>` block at the bottom to reflect the current active Design-vX.md version
3. Keep it updated whenever the active design version changes

`CLAUDE.md` must be in the same folder as the codebase root — Claude Code reads it automatically.

---

## 12.3 Starting a Claude Code Session

Use the session start prompt from CLAUDE.md at the beginning of every new session:

```
<context>
Project documents are in this folder. Read them before proceeding.
Active design: [Design-vX.md — specify the version]
</context>

<task>
Read all project documents in the following order:
1. Design-vX.md (active version)
2. Improvements.md
3. CLAUDE.md
4. Handoff.md
5. Any supporting documents

Then confirm your understanding of the architecture and ask me which task to begin.
</task>

<constraints>
- Do not write any code until I confirm the task and approach
- Ask if anything in the documents is ambiguous or conflicting
</constraints>
```

Claude Code will read the documents, summarise its understanding of the architecture, and ask which task to begin. Confirm or correct before proceeding.

---

## 12.4 Assigning a Task

Use the ongoing task prompt from CLAUDE.md when assigning work:

```
<context>
Active design: [Design-vX.md — specify version]
Current Improvements.md status: [note any recent changes if relevant]
</context>

<task>Implement the following approved task from Improvements.md: [task title]</task>

<constraints>
- Follow the active Design-vX.md exactly
- Follow the acceptance criteria in Improvements.md for this task
- State your intended approach and affected files before writing any code
- Wait for my confirmation before proceeding
</constraints>
```

Claude Code will state its approach and affected files. **Do not let it proceed until you have confirmed.** This prevents wasted effort from misinterpretation.

---

## 12.5 Reviewing Claude Code Output

Before accepting any output from Claude Code:

- Confirm the changed files match what was agreed
- Confirm no files outside the task scope were modified
- Confirm the implementation matches the acceptance criteria in Improvements.md
- Confirm no architectural deviations were made without your approval

If something looks wrong:

```
<task>Stop. Explain the deviation from the agreed approach.</task>
<constraints>Do not make further changes until I confirm the correct path.</constraints>
```

---

## 12.6 When Claude Code Discovers a Gap

During implementation, Claude Code may discover something that requires an architectural decision — a missing design detail, a conflict between documents, or an assumption that needs to be made explicit.

When this happens, Claude Code should stop and report. If it does not, prompt it:

```
<task>Stop the current implementation.</task>
<constraints>
- Document the issue clearly: what was discovered, why it requires a decision, and what the options are
- Do not proceed until I decide
</constraints>
```

Once you have the issue documented, return to Claude Projects:

```
<context>Claude Code discovered the following issue during implementation: [paste the issue]</context>

<role>ARCHITECT</role>

<task>Assess whether this requires a design change.</task>

<constraints>
- If a design change is needed, produce an updated Design-vX.md or initiate a redesign
- If it can be resolved within Improvements.md, update that document
- Wait for my confirmation before any document is locked
</constraints>
```

Once the design is updated and approved, return to Claude Code with the updated documents.

---

## 12.7 Keeping CLAUDE.md Current

Update CLAUDE.md whenever:

- The active Design-vX.md version changes (redesign approved)
- Improvements.md is significantly restructured
- Operating rules or constraints change

Always update the `<version_reference>` block at the bottom of CLAUDE.md after any design version change. Claude Code uses this to confirm it is reading the correct documents.

---

## 12.8 The Full Lifecycle Loop

```
Claude Projects (ARCHITECT)
  → Requirements gathering
  → Design-vX.md approved and locked

Claude Projects (STRATEGIST)
  → Improvements.md approved

Handoff
  → Documents copied to codebase folder
  → CLAUDE.md version reference updated

Claude Code
  → Reads documents
  → Confirms understanding
  → Implements task by task
  → Flags gaps back to user

If gap requires architecture change:
  → Return to Claude Projects (ARCHITECT)
  → Update or version the design
  → Return to Claude Code with updated documents

Repeat until delivery.
```

---

# 13. Glossary


**Architecture** — The structure of the system.  
**Placeholder** — A design entry that cannot be resolved until build time, requiring all four fields: What, Why, When, Interim Assumption.  
**Refactor** — Improve structure without changing behaviour.  
**Context window** — How much Claude can hold in memory at once.  
**Reset context** — Start a new chat inside the same Claude Project, clearing conversation history while preserving all project files, instructions, and structure.  
**Snapshot** — A point‑in‑time capture of the project.  
**Checkpoint** — A summary of recent progress and next steps.  
**Workflow mode** — The project type (greenfield, brownfield, etc.).  
**Role** — ARCHITECT or STRATEGIST.  
**Micro‑task** — A very small, focused task.  
**Handoff** — The point at which approved design documents are passed to Claude Code for implementation.  
**Design Completeness Rule** — The requirement that no design document may be approved or locked while it contains unresolved questions or unpopulated fields.