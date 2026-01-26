# Project Setup Guide  
### How to Use `project_instructions.txt` and `INSTRUCTIONS.md` in Claude Projects

This repository defines a **two‑layer instruction system** that ensures Claude behaves predictably, consistently, and safely across all project types.  
It also includes handbooks, cheat sheets, and templates that support long‑term maintainability and drift‑free development.

This guide explains:

- What each file does  
- Where each file goes  
- How Claude interprets instructions  
- How to prevent drift  
- How to reset context safely  
- How to use the full project workflow  

---

# 1. Repository Structure

| File | Purpose |
|------|---------|
| **project_instructions.txt** | Behavioural rules Claude reads before every message |
| **INSTRUCTIONS.md** | Full specification, templates, workflows, versioning rules |
| **Projects Handbook.md** | Complete operational guide for Claude Projects |
| **Projects Cheatsheet.md** | Fast reference for project workflows |
| **Personal Chat Handbook.md** | Guide for non‑project chats |
| **Personal Chat Cheatsheet.md** | Fast reference for personal chat workflows |
| **README.md** | Setup guide (this file) |

---

# 2. Overview of the Two‑Layer Instruction System

Claude Projects use two complementary instruction layers:

## 2.1 `project_instructions.txt` — Behaviour Layer  
This file defines:

- Roles  
- Workflow logic  
- Guardrails  
- Code output rules  
- Clarification rules  
- Safety boundaries  
- Drift‑prevention rules  

Claude reads this **before every message**.  
It is the AI’s **operating system**.

**Location:**  
Paste into **Claude.ai → Project Instructions**.

---

## 2.2 `INSTRUCTIONS.md` — Specification Layer  
This file contains:

- Full templates  
- Architecture rules  
- Versioning rules  
- Brownfield workflows  
- Reverse‑engineering workflows  
- Redesign workflows  
- Improvements.md structure  
- Code output templates  

Claude does **not** auto‑load this file, but can reference it when asked.

**Location:**  
Upload to **Project Files**.

---

# 3. Why Both Files Are Required

| File | Behaviour | Purpose |
|------|-----------|---------|
| **project_instructions.txt** | Always active | Defines how Claude behaves |
| **INSTRUCTIONS.md** | Referenced on demand | Defines what Claude should produce |

They do not overlap — they work together.

---

# 4. Instruction Precedence Model (Important)

Claude resolves conflicting instructions in this order:

1. **In‑chat instructions** (highest priority)  
2. **project_instructions.txt**  
3. **Profile instructions**  
4. **Memory**  
5. **Model defaults** (lowest priority)

This ensures:

- Project rules override profile rules  
- Temporary overrides are respected  
- Memory never interferes with project logic  

---

# 5. Setup Steps

## Step 1 — Add `project_instructions.txt` to Claude.ai
1. Open your Claude Project  
2. Go to **Project Instructions**  
3. Paste the entire file  
4. Save  

This ensures Claude behaves correctly from the first message.

---

## Step 2 — Upload `INSTRUCTIONS.md` to Project Files
1. Upload the file  
2. Claude can now reference it when asked  
3. Do **not** paste it into the Project Instructions panel  

---

## Step 3 — Start the Project Using the Handbook Workflow

When beginning work:

```
Follow the workflow defined in project_instructions.txt.
```

When generating architecture:

```
Use the Design‑v1.md template from INSTRUCTIONS.md.
```

When updating Improvements.md:

```
Follow the Improvements.md structure in INSTRUCTIONS.md.
```

When writing code:

```
Follow the code output rules in project_instructions.txt.
```

---

# 6. Resetting Context (Critical for Stability)

Claude Projects require periodic resets to avoid:

- context window overload  
- drift  
- hallucinated architecture  
- token waste  

## When to reset:
- Every **20–30 messages**  
- After major task transitions  
- When Claude becomes inconsistent  
- When Claude forgets architecture  

## Reset workflow:
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

# 7. Drift Prevention Best Practices

These rules dramatically reduce errors and token usage:

### ✔ Diff‑First  
Claude must propose a diff plan before writing code.

### ✔ Explain‑Before‑You‑Change  
Claude must explain the change before generating output.

### ✔ Small Tasks  
Break work into micro‑tasks.

### ✔ No Brainstorming Inside Projects  
Use personal chats for exploration.

### ✔ Checkpoints  
Every 10–15 messages:

```
Give me a checkpoint summary.
```

### ✔ Portable Context Blocks  
Useful when resetting context.

---

# 8. File Handling Rules

### ✔ Files uploaded to the Project persist  
Claude can reference them across chats.

### ✔ Files uploaded in chat do NOT persist  
They are ephemeral.

### ✔ Claude cannot “remember” files  
It retrieves them from project knowledge only.

### ✔ Large projects may trigger RAG mode  
Claude retrieves relevant files automatically when needed.

---

# 9. Architecture Versioning (Design‑vX.md)

Architecture files must be:

- immutable  
- versioned  
- stored as `Design‑v1.md`, `Design‑v2.md`, etc.  
- updated only when architecture changes  

Claude should never overwrite a design file — it must create a new version.

---

# 10. Improvements.md Lifecycle

`Improvements.md` is:

- mutable  
- continuously updated  
- the source of truth for enhancements  
- linked to design versions  

Rules:

- Add entries after each sprint  
- Reference the design version  
- Never delete historical entries  
- Use it to drive redesign cycles  

---

# 11. Links to Handbooks & Cheatsheets

### 📘 Project Handbook  
Full operational guide for Claude Projects.

### 📘 Personal Chat Handbook  
How to use Claude outside Projects.

### 📄 Projects Cheatsheet  
Fast reference for project workflows.

### 📄 Personal Chat Cheatsheet  
Fast reference for personal chat workflows.

(All included in this repo.)

---

# 12. Summary Table

| File | Purpose | Location | Behaviour |
|------|----------|-----------|-----------|
| **project_instructions.txt** | Behavioural rules | Project Instructions panel | Always active |
| **INSTRUCTIONS.md** | Full specification & templates | Project Files | Referenced when needed |
| **Design‑vX.md** | Versioned architecture | Project Files | Immutable |
| **Improvements.md** | Continuous improvement log | Project Files | Mutable |
| **Handbooks & Cheatsheets** | Operational guidance | Repo | Human‑readable |

---

# 13. Final Notes

Follow this README exactly when:

- creating a new Claude Project  
- onboarding contributors  
- resetting context  
- updating architecture  
- performing redesign cycles  

This system ensures Claude remains stable, predictable, and aligned across the entire lifecycle of your project.