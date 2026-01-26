### *A complete operational guide for using Claude effectively outside Projects*

---

## Table of Contents

1. [Introduction](#1-introduction)  
2. [How Personal Chats Work](#2-how-personal-chats-work)  
   - [2.1 No Persistent Files](#21-no-persistent-files)  
   - [2.2 No Project Instructions](#22-no-project-instructions)  
   - [2.3 No Workflow Modes](#23-no-workflow-modes)  
   - [2.4 No Architectural Anchors](#24-no-architectural-anchors)  
   - [2.5 Faster Drift](#25-faster-drift)

3. [Understanding Instructions in Personal Chats](#3-understanding-instructions-in-personal-chats)  
   - [3.1 Profile Instructions](#31-profile-instructions)  
   - [3.2 In‑Chat Instructions](#32-in-chat-instructions)  
   - [3.3 Memory](#33-memory)  
   - [3.4 Instruction Precedence](#34-instruction-precedence)  
   - [3.5 When to Use Each Instruction Type](#35-when-to-use-each-instruction-type)  
   - [3.6 How to Override Instructions Safely](#36-how-to-override-instructions-safely)  
   - [3.7 How to Avoid Instruction Overload](#37-how-to-avoid-instruction-overload)

4. [Resetting Context in Personal Chats](#4-resetting-context-in-personal-chats)  
   - [4.1 Why Resets Are Necessary](#41-why-resets-are-necessary)  
   - [4.2 When to Reset](#42-when-to-reset)  
   - [4.3 Reset Workflow](#43-reset-workflow)  
   - [4.4 Portable Context Blocks](#44-portable-context-blocks)  
   - [4.5 Checkpoint Habit](#45-checkpoint-habit)

5. [Preventing Long‑Chat Drift](#5-preventing-long-chat-drift)  
   - [5.1 Warning Signs](#51-warning-signs)  
   - [5.2 How to Prevent Drift](#52-how-to-prevent-drift)  
   - [5.3 How to Recover From Drift](#53-how-to-recover-from-drift)

6. [Working With Claude Effectively](#6-working-with-claude-effectively)  
   - [6.1 Task‑First Workflow](#61-task-first-workflow)  
   - [6.2 Explain‑Before‑You‑Change](#62-explain-before-you-change)  
   - [6.3 Format‑First Requests](#63-format-first-requests)  
   - [6.4 Creative Workflows](#64-creative-workflows)  
   - [6.5 Data & Excel Workflows](#65-data--excel-workflows)  
   - [6.6 Image Workflows](#66-image-workflows)

7. [Safe Request Templates](#7-safe-request-templates)  
   - [7.1 Writing Tasks](#71-writing-tasks)  
   - [7.2 Planning Tasks](#72-planning-tasks)  
   - [7.3 Data Tasks](#73-data-tasks)  
   - [7.4 Excel Tasks](#74-excel-tasks)  
   - [7.5 Creative Tasks](#75-creative-tasks)  
   - [7.6 Image Tasks](#76-image-tasks)

8. [Token‑Safe Practices](#8-token-safe-practices)

9. [Never‑Do List](#9-never-do-list)

10. [Glossary (Personal‑Chat‑Specific)](#10-glossary-personal-chat-specific)

---

# 1. Introduction

This handbook explains how to use Claude effectively in **personal chats**, where:

- there are no persistent files  
- there is no project instruction system  
- there is no architecture  
- there is no workflow mode  
- everything is user‑centric and task‑specific  

Personal chats are flexible and powerful, but they drift faster and require different operational habits than Projects.

This guide teaches you how to:

- give effective instructions  
- prevent drift  
- reset context safely  
- carry information between chats  
- avoid losing work  
- structure tasks  
- use Claude for writing, planning, data, Excel, and creative work  

---

# 2. How Personal Chats Work

Personal chats are **ephemeral**. Claude only has access to:

- your current message  
- the conversation history  
- your profile instructions  
- your memory (if enabled)

There is no persistent project state.

---

## 2.1 No Persistent Files

Claude cannot store or recall files across chats.  
If you need Claude to reference a file, you must upload it again.

---

## 2.2 No Project Instructions

There is no `project_instructions.txt`.  
There is no persistent workflow.  
There are no roles.

---

## 2.3 No Workflow Modes

Claude does not automatically enter:

- ARCHITECT  
- STRATEGIST  
- ENGINEER  

These modes do not exist in personal chats.

---

## 2.4 No Architectural Anchors

Claude does not maintain:

- file maps  
- system architecture  
- design versions  
- improvements lists  

Everything must be provided manually if needed.

---

## 2.5 Faster Drift

Because there is no persistent structure, personal chats:

- drift faster  
- compress earlier  
- lose detail sooner  
- require more frequent resets  

---

# 3. Understanding Instructions in Personal Chats

Personal chats have **three instruction layers**:

1. **Profile Instructions** (persistent)  
2. **In‑Chat Instructions** (temporary)  
3. **Memory** (long‑term preferences)

---

## 3.1 Profile Instructions

These are:

- global  
- persistent  
- always loaded  
- always active  
- survive across chats  
- define your default tone, behaviour, and preferences  

Use profile instructions for:

- tone  
- formatting preferences  
- reasoning preferences  
- general behaviour  
- stable expectations  

---

## 3.2 In‑Chat Instructions

These are:

- temporary  
- local to the current chat  
- override profile instructions  
- lost when you start a new chat  

Use in‑chat instructions for:

- task‑specific formatting  
- temporary tone changes  
- workflow preferences  
- output constraints  

Examples:

```
Use a concise tone for this task.
Format the output as a table.
Explain your reasoning step-by-step.
```

---

## 3.3 Memory

Memory stores:

- stable preferences  
- personal details  
- long‑term patterns  

Memory does **not** store instructions, but it influences how Claude interprets them.

---

## 3.4 Instruction Precedence

When instructions conflict, Claude follows this order:

1. **In‑chat instructions**  
2. **Profile instructions**  
3. **Memory**  
4. **Model defaults**

---

## 3.5 When to Use Each Instruction Type

### Use profile instructions for:
- tone  
- formatting defaults  
- reasoning defaults  
- stable preferences  

### Use in‑chat instructions for:
- task‑specific behaviour  
- temporary overrides  
- formatting for this output only  

### Use memory for:
- long‑term personal preferences  
- identity‑level details  

---

## 3.6 How to Override Instructions Safely

To override profile instructions:

```
For this task only, use a friendly tone.
```

To override memory‑based behaviour:

```
Ignore previous preferences for this task.
```

To reset overrides:

```
Start a new chat.
```

---

## 3.7 How to Avoid Instruction Overload

- Don’t stack too many instructions  
- Don’t mix conflicting instructions  
- Don’t give global instructions inside a chat  
- Don’t try to recreate project‑style workflows  

---

# 4. Resetting Context in Personal Chats

## 4.1 Why Resets Are Necessary

Personal chats drift because:

- context compresses  
- details are lost  
- instructions blur  
- Claude begins guessing  

---

## 4.2 When to Reset

Reset every:

- **15–25 messages**  
- after long reasoning chains  
- after major topic changes  
- when drift is detected  

---

## 4.3 Reset Workflow

### Step 1 — Ask for a structured summary

```
Summarise what we’re doing, the decisions made, constraints, and next steps.
Make it concise and suitable for starting a new chat.
```

### Step 2 — Start a new chat

### Step 3 — Paste the summary

```
Here is the context from the previous chat. Use this as the starting point.
```

---

## 4.4 Portable Context Blocks

Ask Claude to generate a portable block:

```
Create a portable context block summarising:
- the goal
- decisions made
- constraints
- examples
- next steps
```

Paste this into the new chat.

---

## 4.5 Checkpoint Habit

Every 10–15 messages:

```
Give me a checkpoint summary of what we’ve done and what’s next.
```

This prevents losing information.

---

# 5. Preventing Long‑Chat Drift

## 5.1 Warning Signs

Claude:

- repeats questions  
- forgets earlier details  
- contradicts itself  
- becomes generic  
- asks for context you already gave  
- loses track of the task  

---

## 5.2 How to Prevent Drift

- reset frequently  
- use checkpoints  
- avoid long back‑and‑forths  
- avoid brainstorming in the same thread  
- avoid pasting huge blocks of text  
- keep messages short  

---

## 5.3 How to Recover From Drift

```
Summarise the task, decisions, constraints, and next steps.
Make it suitable for starting a new chat.
```

Then reset.

---

# 6. Working With Claude Effectively

## 6.1 Task‑First Workflow

Always start with:

- the goal  
- the constraints  
- the format  
- the audience  

---

## 6.2 Explain‑Before‑You‑Change

For multi‑step tasks:

```
Explain your approach before producing the final output.
```

---

## 6.3 Format‑First Requests

Examples:

```
Format the output as:
- a table
- bullet points
- a numbered list
- a 200-word summary
```

---

## 6.4 Creative Workflows

```
Write in a noir detective style.
Use vivid sensory detail.
Keep it under 300 words.
```

---

## 6.5 Data & Excel Workflows

```
Provide only the formula.
No explanation.
```

or

```
Explain the logic first, then give the formula.
```

---

## 6.6 Image Workflows

```
Describe the concept in one paragraph.
```

---

# 7. Safe Request Templates

## 7.1 Writing Tasks

```
Write a concise explanation of <topic>.
Audience: <audience>.
Tone: <tone>.
Format: <format>.
```

---

## 7.2 Planning Tasks

```
Create a step-by-step plan for <goal>.
Include risks, dependencies, and next actions.
```

---

## 7.3 Data Tasks

```
Analyse the following data:
<dataset>

Provide:
- summary
- insights
- anomalies
- recommendations
```

---

## 7.4 Excel Tasks

```
I need an Excel formula for:
<goal>

Provide:
- the formula
- a short explanation
```

---

## 7.5 Creative Tasks

```
Write a short story in <style>.
Length: <limit>.
Constraints: <constraints>.
```

---

## 7.6 Image Tasks

```
Describe an image concept based on:
<idea>
```

---

# 8. Token‑Safe Practices

- keep tasks small  
- reset often  
- avoid long chats  
- avoid re‑explaining context  
- use portable context blocks  
- use checkpoints  
- avoid unnecessary detail  

---

# 9. Never‑Do List

- never let chats run too long  
- never rely on Claude to remember past chats  
- never give global instructions inside a chat  
- never mix multiple tasks in one message  
- never paste huge blocks of text unless necessary  

---

# 10. Glossary (Personal‑Chat‑Specific)

**Profile instructions** — Persistent global instructions that define Claude’s default behaviour.  
**In‑chat instructions** — Temporary instructions that apply only to the current chat.  
**Memory** — Stored long‑term preferences and personal details.  
**Reset context (personal chat)** — Starting a brand‑new chat and manually providing a summary of the previous conversation.  
**Checkpoint** — A summary of progress and next steps.  
**Portable context block** — A structured summary designed to be pasted into a new chat.  
**Drift** — Loss of accuracy due to context compression.  

---