### *Unified Operational Guide for CIOs, Engineers, and Non‑Developers*  
### *Using `project_instructions.txt` + `INSTRUCTIONS.md`*

---

## Table of Contents  
*(Links will work once all parts are combined into a single file.)*

1. [Introduction](#1-introduction)  
2. [How Claude Projects Actually Works](#2-how-claude-projects-actually-works-medium-depth-overview)  
3. [Understanding Token Usage](#3-understanding-token-usage)  
4. [Understanding the Context Window (Chat Length Limit)](#4-understanding-the-context-window-chat-length-limit)  
   - [4.1 What the context window is](#41-what-the-context-window-is)  
   - [4.2 How Claude manages context](#42-how-claude-manages-context)  
   - [4.3 How context overload increases token usage](#43-how-context-overload-increases-token-usage)  
   - [4.4 Warning signs of context overload](#44-warning-signs-of-context-overload)  
   - [4.5 How to reset context safely](#45-how-to-reset-context-safely)  
   - [4.6 How to prevent context overload](#46-how-to-prevent-context-overload)  
   - [4.7 Best practices for long-running projects](#47-best-practices-for-long-running-projects)  
5. [Your Instruction System (How It Works)](#5-your-instruction-system-how-it-works)  
   - [5.1 `project_instructions.txt`](#51-project_instructionstxt)  
   - [5.2 `INSTRUCTIONS.md`](#52-instructionsmd)  
   - [5.3 Roles](#53-roles)  
   - [5.4 Workflow modes](#54-workflow-modes)  
   - [5.5 Design versioning](#55-design-versioning)  
   - [5.6 Improvements tracking](#56-improvements-tracking)  
   - [5.7 Architecture summaries](#57-architecture-summaries)  

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

It is designed to work **100% in tandem** with:

- `project_instructions.txt`  
- `INSTRUCTIONS.md`  

These two files define how Claude behaves.  
This handbook defines how **you** use Claude.

Together, they form a complete, repeatable, scalable development workflow.

---

# 2. How Claude Projects Actually Works (Medium‑Depth Overview)

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
- Claude does not need you to paste code repeatedly  
- Claude can regenerate files without re‑reading the entire project  

This is why Projects mode is dramatically more efficient than normal chats.

---

## 2.2 Project Instructions Are Auto‑Loaded

Claude automatically loads:

- `project_instructions.txt` **every message**  
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

This is why:

- Short, clear messages work best  
- Long conversations cause drift  
- Resetting context periodically is essential  

---

## 2.4 Claude Does Not “Remember Everything”

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
- Snapshots matter  

---

## 2.5 Claude Is Most Efficient When Tasks Are Small

Claude performs best when:

- Tasks are broken into micro‑tasks  
- Only relevant files are touched  
- Only necessary code is generated  
- You avoid full‑file rewrites unless needed  

This handbook teaches you how to structure tasks to maximise efficiency.

---

# 3. Understanding Token Usage

Token usage is influenced by:

- How much text Claude reads  
- How much text Claude writes  
- How often Claude re‑reads files  
- How often Claude re‑summarises context  
- How often Claude re‑anchors to instructions  
- How often Claude rewrites entire files  

Below is a breakdown of what consumes tokens and how to avoid unnecessary usage.

---

## 3.1 Full‑File Regeneration

**High cost.**

Claude must:

- Read the entire file  
- Generate the entire file  
- Validate the file  
- Re‑anchor the file into the project  

Use only when:

- Creating new files  
- Replacing legacy files  
- Rewriting files under ~200 lines  
- Performing major refactors  

Avoid when:

- Making small changes  
- Fixing bugs  
- Adding small features  

---

## 3.2 Brainstorming Inside the Project

**Very high cost.**

When you brainstorm inside a Project:

- Claude loads the entire project context  
- Claude tries to relate ideas to the codebase  
- Claude may re‑read files  
- Claude may re‑interpret instructions  

This burns tokens rapidly.

**Solution:**  
Do all brainstorming in a **separate personal chat**, then bring the final decision into the Project.

---

## 3.3 Long Conversations

**High cost.**

As conversations grow:

- Claude compresses older messages  
- Claude re‑summarises context  
- Claude re‑anchors to instructions  
- Claude may re‑read files  

This increases token usage and risk of drift.

**Solution:**  
Reset context every **20–30 messages**.

---

## 3.4 Re‑Explaining Context

**Moderate to high cost.**

If Claude forgets something and you re‑explain it:

- You burn tokens  
- Claude burns tokens re‑processing it  

**Solution:**  
Use:

```
Re-anchor to instructions.
Summarise the architecture.
Summarise the current task.
```

---

## 3.5 Re‑Uploading Files

**Very high cost.**

Uploading files forces Claude to:

- Re‑read them  
- Re‑index them  
- Re‑anchor them  

This is unnecessary in Projects mode.

**Solution:**  
Never re‑upload files unless they changed outside Claude.

---

# 4. Understanding the Context Window (Chat Length Limit)

The context window is the **maximum amount of information Claude can hold at once**.  
When the window fills, Claude must compress older content, which leads to:

- Drift  
- Mistakes  
- Token spikes  
- Unnecessary rewrites  
- Confusion  
- Loss of architectural understanding  

This section explains how to manage it safely.

---

## 4.1 What the Context Window Is

Claude can only “hold” a certain amount of text in memory at once.

This includes:

- Your messages  
- Claude’s messages  
- Loaded files  
- Instructions  
- Summaries  
- Code  
- Explanations  

When the window fills:

- Claude compresses older content  
- Compression removes detail  
- Loss of detail causes drift  

---

## 4.2 How Claude Manages Context

Claude prioritises:

1. Your latest message  
2. The active task  
3. Relevant files  
4. Project instructions  
5. Recent conversation  
6. Older conversation (compressed)

This means:

- Long chats cause drift  
- Large messages cause drift  
- Large files cause drift  
- Repeated brainstorming causes drift  

---

## 4.3 How Context Overload Increases Token Usage

When Claude’s context window fills, Claude must:

- Re‑summarise older content  
- Re‑interpret instructions  
- Re‑read files  
- Re‑anchor architecture  
- Re‑anchor workflow modes  

Each of these operations consumes tokens.

This is why long chats burn through weekly limits.

---

## 4.4 Warning Signs of Context Overload

You will notice overload when Claude:

- Asks questions it already asked  
- Forgets architecture  
- Misinterprets instructions  
- Rewrites entire files instead of diffing  
- Asks for files that exist  
- Contradicts earlier decisions  
- Loses track of workflow mode  
- Loses track of role  
- Starts hallucinating file structure  

When you see these signs, reset context immediately.

---

## 4.5 How to Reset Context Safely

Use this exact message:

```
Reset context.
Reload project_instructions.txt.
Do not re-read all files.
Ask me what we are working on.
```

Then follow with:

```
Re-anchor to instructions.
Summarise the architecture.
Summarise the current task.
Wait for my confirmation.
```

---

## 4.6 How to Prevent Context Overload

- Reset every 20–30 messages  
- Keep tasks small  
- Use micro‑tasks  
- Avoid long back‑and‑forths in ENGINEER mode  
- Move brainstorming to a separate chat  
- Keep architecture summaries updated  
- Use “Explain Before You Change”  
- Use “Diff‑First”  
- Avoid unnecessary full‑file rewrites  

---

## 4.7 Best Practices for Long‑Running Projects

- Use snapshots before major changes  
- Keep Design‑vX.md updated  
- Keep Improvements.md updated  
- Reset context regularly  
- Re‑anchor Claude after resets  
- Avoid mixing exploration with implementation  
- Keep messages short and clear  
- Avoid pasting large code blocks unless necessary  

---

# 5. Your Instruction System (How It Works)

Your instruction system is the backbone of your workflow.  
It ensures Claude behaves consistently, predictably, and safely.

It consists of:

- `project_instructions.txt`  
- `INSTRUCTIONS.md`  
- Roles  
- Workflow modes  
- Design versioning  
- Improvements tracking  
- Architecture summaries  

---

## 5.1 `project_instructions.txt`

This file is:

- Loaded automatically every message  
- The “operating system” for Claude  
- The source of truth for roles and workflow  
- The behavioural contract Claude must follow  

It defines:

- Roles (ARCHITECT, STRATEGIST, ENGINEER)  
- Workflow modes  
- Safety rules  
- Output rules  
- Change‑request rules  
- Diff rules  
- Confirmation rules  

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
- File maps  
- Data models  

### **STRATEGIST**
- No code  
- Task planning  
- Sprint planning  
- Feature breakdown  
- Dependency mapping  

### **ENGINEER**
- Writes code  
- Generates diffs  
- Regenerates files when needed  
- Implements tasks  

Switch roles with:

```
Act as ARCHITECT.
Act as STRATEGIST.
Act as ENGINEER.
```

---

## 5.4 Workflow Modes

Claude determines the mode at project start:

- Greenfield  
- Brownfield  
- Rebuild  
- Customisation  
- Reverse‑engineering  

---

## 5.5 Design Versioning

Design documents follow:

- `Design‑v1.md`  
- `Design‑v2.md`  
- `Design‑v3.md`  

Each version is:

- A snapshot of architecture  
- A stable reference  
- Never modified after approval  

---

## 5.6 Improvements Tracking

`Improvements.md` tracks:

- Feature requests  
- Bug fixes  
- Refactors  
- Technical debt  
- Architecture changes  

Claude uses this to plan work.

---

## 5.7 Architecture Summaries

Architecture summaries:

- Keep Claude anchored  
- Reduce context load  
- Prevent drift  
- Provide a stable reference  

Update them after major changes.

---

# 6. Starting a New Project (Step‑by‑Step)

This section provides a clear, repeatable workflow for starting any new Claude Project, regardless of whether it is greenfield, brownfield, a rebuild, or a reverse‑engineering effort.

The goal is to ensure Claude:

- Loads your instruction system correctly  
- Anchors itself to the correct workflow mode  
- Understands the project scope  
- Avoids unnecessary token usage  
- Begins in a predictable, controlled state  

---

## 6.1 Upload Your Files

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

These waste tokens and slow Claude down.

---

## 6.2 Confirm Project Instructions Are Loaded

Claude automatically loads:

- `project_instructions.txt` every message  
- Any files you reference explicitly  

You do **not** need to paste instructions manually.

---

## 6.3 Send the First Message (Template)

Use this exact template:

```
We are starting a new project.

Here is the project type: <greenfield / brownfield / rebuild / reverse-engineering / customisation>.
Here is the high-level goal: <describe the outcome>.
Here is the initial scope: <describe what we want to achieve first>.
Here are the files I uploaded: <list them or say “uploaded”>.

Act as ARCHITECT.
Confirm the project type.
Summarise the initial architecture.
Identify missing information.
Wait for my confirmation before proceeding.
```

This ensures Claude:

- Anchors to the correct role  
- Anchors to the correct workflow mode  
- Does not generate code prematurely  
- Does not assume missing details  
- Starts with architecture, not implementation  

---

## 6.4 Confirm the Architecture

Claude will respond with:

- A project type confirmation  
- A high‑level architecture  
- A file map  
- A list of unknowns or missing information  

Review this carefully.

If correct, respond:

```
Confirmed. Proceed.
```

If incorrect, respond:

```
Correct the architecture as follows:
<list corrections>
```

---

## 6.5 Move to STRATEGIST Mode

Once architecture is confirmed:

```
Act as STRATEGIST.
Break the project into phases, sprints, and tasks.
Wait for my confirmation.
```

Claude will produce:

- A multi‑phase plan  
- Sprint breakdowns  
- Task lists  
- Dependencies  
- Priorities  

Confirm or correct as needed.

---

## 6.6 Move to ENGINEER Mode

Once planning is approved:

```
Act as ENGINEER.
Begin with the first approved task.
Explain before you change anything.
Wait for my confirmation before generating code.
```

This ensures:

- No premature code generation  
- No accidental full‑file rewrites  
- No misinterpretation of scope  

---

## 6.7 Establish the First Task

Claude will propose:

- The first task  
- The files involved  
- The expected changes  
- The diff plan  

Confirm with:

```
Approved. Proceed.
```

Or correct with:

```
Adjust the task as follows:
<corrections>
```

---

# 7. Working With Claude Effectively

This section defines the operational rules that keep Claude predictable, efficient, and aligned with your instruction system.

---

## 7.1 The “Feature‑First” Workflow

Every task should begin with:

- The feature  
- The behaviour  
- The user outcome  
- The acceptance criteria  

Never begin with:

- “Write code to…”  
- “Modify file X…”  
- “Add a function…”  

Claude must understand the **intent** before touching code.

---

## 7.2 The “Explain Before You Change” Rule

Before Claude modifies any file, it must:

1. Explain the change  
2. Identify the affected files  
3. Provide a diff plan  
4. Wait for your approval  

This prevents:

- Accidental rewrites  
- Misinterpretation  
- Token spikes  
- Architecture drift  

---

## 7.3 The “Diff‑First” Rule

Claude must always:

- Provide diffs for small or moderate changes  
- Only regenerate full files when necessary  

Use this command:

```
Provide a diff plan before generating code.
```

---

## 7.4 When to Regenerate Full Files

Full regeneration is appropriate when:

- Creating a new file  
- Replacing a legacy file  
- Rewriting a file under ~200 lines  
- Performing a major refactor  
- Fixing structural issues  
- Cleaning up inconsistent formatting  

Avoid full regeneration when:

- Fixing small bugs  
- Adding small features  
- Making minor adjustments  
- Updating a few lines  

---

## 7.5 When to Request Partial Changes

Use partial changes when:

- Only a function needs updating  
- Only a block of logic changes  
- Only a few lines need modification  
- Only documentation needs updating  

Use:

```
Show me the diff for only the affected sections.
```

---

## 7.6 How to Avoid Accidental Full Rewrites

Never say:

- “Rewrite this file”  
- “Replace this file”  
- “Update this file” (too vague)  
- “Fix this file” (too vague)  

Instead say:

```
Modify only the following sections:
<list sections>
```

Or:

```
Provide a diff for the minimal required changes.
```

---

## 7.7 Keeping Claude Anchored to Instructions

If Claude drifts:

```
Re-anchor to instructions.
Summarise the architecture.
Summarise the current task.
Wait for my confirmation.
```

This resets Claude’s internal state without resetting the entire context.

---

# 8. Requesting Changes (Templates & Examples)

This section provides **copy‑ready templates** for every type of change request.

---

## 8.1 New Feature Request

```
New feature request.

Feature: <describe the feature>.
User outcome: <describe what the user experiences>.
Acceptance criteria:
- <criterion 1>
- <criterion 2>
- <criterion 3>

Act as ENGINEER.
Explain the change.
Identify affected files.
Provide a diff plan.
Wait for my confirmation.
```

---

## 8.2 Bug Fix

```
Bug fix request.

Bug: <describe the bug>.
Expected behaviour: <describe correct behaviour>.
Actual behaviour: <describe incorrect behaviour>.
Steps to reproduce:
1. …
2. …
3. …

Act as ENGINEER.
Explain the root cause.
Identify affected files.
Provide a diff plan.
Wait for my confirmation.
```

---

## 8.3 Refactor

```
Refactor request.

Goal: <describe the purpose>.
Scope: <describe what should change>.
Non-goals: <describe what must NOT change>.

Act as ENGINEER.
Explain the refactor.
Identify affected files.
Provide a diff plan.
Wait for my confirmation.
```

---

## 8.4 New File

```
Create a new file.

File path: <path>.
Purpose: <describe purpose>.
Contents: <describe what should be inside>.

Act as ENGINEER.
Explain the file structure.
Wait for my confirmation before generating the file.
```

---

## 8.5 Modify Existing File

```
Modify an existing file.

File: <path>.
Change required: <describe change>.
Scope: <minimal / moderate / major>.

Act as ENGINEER.
Explain the change.
Provide a diff plan.
Wait for my confirmation.
```

---

## 8.6 Reverse‑Engineering

```
Reverse-engineering request.

Goal: Understand the following file:
<file path>

Act as ARCHITECT.
Summarise the file.
Explain its purpose.
Explain how it fits into the system.
Identify risks or issues.
```

---

## 8.7 Architecture Changes

```
Architecture change request.

Change: <describe change>.
Reason: <why>.
Impact: <expected impact>.

Act as ARCHITECT.
Explain the architectural implications.
Propose updated architecture.
Wait for my confirmation.
```

---

## 8.8 Documentation Updates

```
Documentation update request.

File: <path>.
Change required: <describe change>.

Act as ENGINEER.
Provide a diff plan.
Wait for my confirmation.
```

---

# 9. Managing Large Projects

Large or long‑running projects require additional structure to prevent drift, maintain clarity, and keep Claude operating efficiently. This section provides the operational practices that ensure stability over weeks or months of development.

---

## 9.1 Architecture Summaries

Architecture summaries are the backbone of long‑term stability.

They should include:

- High‑level system overview  
- Module breakdown  
- File map  
- Data flow  
- Key dependencies  
- Integration points  
- Known constraints  
- Known risks  

Update the summary when:

- A major feature is added  
- A major refactor occurs  
- A subsystem changes  
- A new design version is created  

Claude uses this summary to stay anchored and avoid drift.

---

## 9.2 Design Versioning (Design‑vX.md)

Design documents are **immutable snapshots** of the system’s architecture at a point in time.

Rules:

- Never modify a design document after approval  
- Always create a new version for major architectural changes  
- Reference the design version in conversations when needed  
- Keep versions small and focused  

Example versioning:

- `Design‑v1.md` — initial architecture  
- `Design‑v2.md` — after major refactor  
- `Design‑v3.md` — after new subsystem added  

Claude relies on these documents to understand architectural evolution.

---

## 9.3 Improvements Tracking (Improvements.md)

This file tracks:

- Feature requests  
- Bug fixes  
- Refactors  
- Technical debt  
- Architecture changes  
- Performance improvements  
- Documentation needs  

Each entry should include:

- Description  
- Priority  
- Impact  
- Dependencies  
- Status  

Claude uses this file to plan sprints and tasks.

---

## 9.4 Snapshots

Snapshots are point‑in‑time captures of:

- Architecture  
- Key files  
- Requirements  
- Decisions  
- Constraints  

Use snapshots:

- Before major changes  
- Before refactors  
- Before subsystem rewrites  
- Before switching tasks  

Snapshots help Claude recover if drift occurs.

---

## 9.5 Checkpoints

Checkpoints are lightweight summaries of:

- What was done  
- What is next  
- What changed  
- What remains  

Use checkpoints:

- At the end of each task  
- At the end of each sprint  
- After context resets  

Claude uses checkpoints to re‑anchor itself quickly.

---

## 9.6 Resetting Context Safely

Reset context every:

- 20–30 messages  
- After major architectural discussions  
- After long brainstorming sessions  
- When drift is detected  

Use:

```
Reset context.
Reload project_instructions.txt.
Do not re-read all files.
Ask me what we are working on.
```

Then:

```
Re-anchor to instructions.
Summarise the architecture.
Summarise the current task.
Wait for my confirmation.
```

---

## 9.7 Avoiding Drift in Large Projects

To prevent drift:

- Keep messages short  
- Keep tasks small  
- Avoid mixing exploration and implementation  
- Use architecture summaries  
- Use design versioning  
- Use checkpoints  
- Reset context regularly  
- Avoid long back‑and‑forths in ENGINEER mode  
- Avoid unnecessary full‑file rewrites  

---

# 10. Troubleshooting & Recovery

This section provides clear, actionable procedures for diagnosing and fixing common issues in Claude Projects.

Each issue includes:

- Symptoms  
- Cause  
- Fix  
- Prevention  

---

## 10.1 Claude Rewrote a File Unexpectedly

### Symptoms
- Entire file replaced  
- Formatting changed  
- Unrelated sections modified  

### Cause
- Claude misinterpreted the request  
- Context overload  
- Missing diff plan  

### Fix
```
Stop.
Re-anchor to instructions.
Summarise the architecture.
Summarise the intended change.
Provide a minimal diff.
```

### Prevention
- Always request a diff plan  
- Use “Explain Before You Change”  
- Keep tasks small  

---

## 10.2 Claude Forgot the Architecture

### Symptoms
- Incorrect assumptions  
- Missing components  
- Wrong file references  

### Cause
- Context window overload  
- Long conversation without resets  

### Fix
```
Re-anchor to instructions.
Summarise the architecture.
Summarise the current task.
Wait for my confirmation.
```

### Prevention
- Reset context every 20–30 messages  
- Maintain architecture summaries  

---

## 10.3 Claude Hallucinated File Structure

### Symptoms
- References to files that don’t exist  
- Incorrect paths  
- Invented modules  

### Cause
- Context compression  
- Missing architecture summary  

### Fix
```
List all files in the project.
Correct the file map.
Re-anchor to instructions.
```

### Prevention
- Keep file maps updated  
- Use architecture summaries  

---

## 10.4 Claude Is Asking for Files That Exist

### Symptoms
- “Please upload X”  
- “I cannot find Y”  

### Cause
- Context overload  
- Misalignment between memory and conversation  

### Fix
```
Reset context.
Reload project_instructions.txt.
Ask me what we are working on.
```

### Prevention
- Reset context regularly  
- Avoid long chats  

---

## 10.5 Claude Is Contradicting Earlier Decisions

### Symptoms
- Changing requirements  
- Changing architecture  
- Changing naming conventions  

### Cause
- Context compression  
- Missing design version reference  

### Fix
```
Refer to Design‑vX.md.
Re-anchor to instructions.
Summarise the architecture.
```

### Prevention
- Use design versioning  
- Keep decisions documented  

---

## 10.6 Claude Is Drifting From Instructions

### Symptoms
- Ignoring workflow rules  
- Generating code prematurely  
- Skipping diff plans  

### Cause
- Context overload  
- Missing re‑anchoring  

### Fix
```
Re-anchor to instructions.
Summarise the workflow rules.
Wait for my confirmation.
```

### Prevention
- Reset context  
- Keep instructions stable  

---

## 10.7 Claude Is Generating Too Much Code

### Symptoms
- Full‑file rewrites  
- Large blocks of code  
- Unnecessary regeneration  

### Cause
- Vague requests  
- Missing diff plan  
- ENGINEER mode over‑engaged  

### Fix
```
Provide only the minimal diff.
Do not regenerate full files.
```

### Prevention
- Use precise change requests  
- Always request a diff plan  

---

## 10.8 Claude Is Burning Tokens Too Fast

### Symptoms
- Weekly limit approaching  
- Large responses  
- Frequent resets  
- Re‑reading files  

### Cause
- Long conversations  
- Brainstorming inside the project  
- Full‑file rewrites  
- Re‑explaining context  

### Fix
- Move exploration to personal chats  
- Reset context  
- Use micro‑tasks  
- Use diff‑first workflows  

### Prevention
- Follow the cheat sheet rules  
- Keep tasks small  
- Avoid unnecessary regeneration  

---

# 11. Quick‑Use Cheat Sheet

This section provides a fast‑reference operational guide for daily use.

---

## 11.1 The 10 Token‑Safe Rules

1. Keep tasks small  
2. Reset context every 20–30 messages  
3. Never brainstorm inside the project  
4. Always request a diff plan  
5. Use “Explain Before You Change”  
6. Avoid full‑file rewrites unless necessary  
7. Keep architecture summaries updated  
8. Use design versioning  
9. Use micro‑tasks  
10. Keep messages short and clear  

---

## 11.2 The 3‑Step Task Workflow

1. Describe the goal  
2. Confirm scope  
3. Execute in ENGINEER mode  

---

## 11.3 The 4 Most Important Commands

```
Act as ARCHITECT.
Act as STRATEGIST.
Act as ENGINEER.
Re-anchor to instructions.
```

---

## 11.4 Regenerate vs Diff Decision Tree

- **Small change?** → Diff  
- **Moderate change?** → Diff  
- **Major change?** → Full file  
- **New file?** → Full file  
- **Refactor?** → Diff + partial regeneration  

---

## 11.5 Safe Message Templates

### New Feature
```
New feature request:
<feature>
Act as ENGINEER.
Explain before you change.
Provide a diff plan.
```

### Bug Fix
```
Bug fix:
<bug>
Act as ENGINEER.
Explain root cause.
Provide a diff plan.
```

### Refactor
```
Refactor request:
<goal>
Act as ENGINEER.
Explain the refactor.
Provide a diff plan.
```

---

## 11.6 Context Window Rules

- Reset every 20–30 messages  
- Keep tasks small  
- Avoid long chats  
- Move exploration to personal chats  
- Use architecture summaries  

---

## 11.7 Drift Indicators

- Claude forgets architecture  
- Claude rewrites entire files  
- Claude asks for files that exist  
- Claude contradicts earlier decisions  

---

## 11.8 Reset Procedure

```
Reset context.
Reload project_instructions.txt.
Do not re-read all files.
Ask me what we are working on.
```

---

## 11.9 Never‑Do List

- Never brainstorm inside the project  
- Never paste large code blocks unnecessarily  
- Never request vague changes  
- Never skip diff plans  
- Never mix exploration with implementation  

---

# 12. Glossary (Non‑Developer Friendly)

**Architecture** — The structure of the system.  
**Diff** — A list of changes to a file.  
**Refactor** — Improve code without changing behaviour.  
**Context window** — How much Claude can remember at once.
**Reset context** — Starting a new chat inside the same Claude Project, which clears the conversational history while preserving all project files, instructions, and structure. This prevents context‑window overload and keeps Claude aligned without requiring re‑uploads or re‑explanations.
**Snapshot** — A point‑in‑time capture of the project.  
**Checkpoint** — A summary of recent progress.  
**Workflow mode** — The project type (greenfield, rebuild, etc.).  
**Role** — ARCHITECT, STRATEGIST, ENGINEER.  
**Regenerate** — Rewrite an entire file.  
**Micro‑task** — A very small, focused task.  

---

# 13. Final Notes

- Keep this document updated as your workflow evolves  
- Update design versions when architecture changes  
- Use Improvements.md to track work  
- Reset context regularly  
- Keep Claude anchored to instructions  
- Maintain architecture summaries  

---