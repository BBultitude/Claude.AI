# Project Setup Guide  
How to Use `project_instructions.txt` and `INSTRUCTIONS.md`

This repository uses a two‑layer instruction system to ensure predictable, stable, and high‑quality behaviour from Claude across all project types.  
Both files serve different purposes and must be placed in specific locations.

---

## 1. Overview

This project uses:

1. **project_instructions.txt**  
   The behavioural rules that Claude reads *every time* inside the Claude.ai Project Instructions panel.

2. **INSTRUCTIONS.md**  
   The full, versioned, canonical specification for how Claude should operate across:
   - Greenfield projects  
   - Brownfield projects  
   - Reverse‑engineering  
   - Redesign cycles  
   - Continuous improvement  
   - Code implementation  

These two files work together to create a stable, repeatable workflow.

---

## 2. What Each File Is For

### `project_instructions.txt`  
**Purpose:**  
Defines Claude’s behaviour, guardrails, roles, and workflow logic.

**Where it goes:**  
Paste the entire contents into the **Claude.ai → Project Instructions** panel.

**Why:**  
Claude reads this field *before every message*.  
It cannot reliably follow external references, so the behavioural rules must be inline.

**This file controls:**
- Role switching  
- Workflow selection  
- Guardrails  
- Code output rules  
- Document lifecycle rules  
- Scope boundaries  
- Clarification requirements  

This is the AI’s “operating system.”

---

### `INSTRUCTIONS.md`  
**Purpose:**  
The full, richly formatted, canonical reference for all templates, workflows, and architectural rules.

**Where it goes:**  
Add it to the **project files** in the Claude.ai project (or your repo).

**Why:**  
Claude can open and reference this file when asked, but does not automatically load it.  
It provides:
- Full templates  
- Detailed workflows  
- Versioned design rules  
- Brownfield and legacy handling  
- Redesign templates  
- Improvements.md structure  
- Code output templates  

This is the AI’s “documentation and specification.”

---

## 3. Why Both Files Are Required

### `project_instructions.txt`  
- Always loaded  
- Always active  
- Defines behaviour  
- Enforces rules  
- Prevents drift  
- Prevents hallucination  
- Prevents scope creep  

### `INSTRUCTIONS.md`  
- Human‑readable  
- Version‑controlled  
- Complete and detailed  
- Used when you say “follow the template in INSTRUCTIONS.md”  
- Supports long‑term evolution of the system  

**They do not overlap — they complement each other.**

---

## 4. Setup Steps

### Step 1 — Add `project_instructions.txt` to Claude.ai
1. Open your Claude.ai project  
2. Go to **Project Instructions**  
3. Paste the entire contents of `project_instructions.txt`  
4. Save  

This ensures Claude behaves correctly from the first message.

---

### Step 2 — Add `INSTRUCTIONS.md` to the Project Files
1. Upload `INSTRUCTIONS.md` into the Claude.ai project file list  
2. Claude can now reference it when asked  
3. Do not paste it into the Project Instructions panel  

This ensures Claude has access to the full templates and workflows.

---

### Step 3 — Use the Files During Development

#### When starting a new task:
Tell Claude:
> “Follow the workflow defined in project_instructions.txt.”

#### When generating architecture:
> “Use the Design‑v1.md template from INSTRUCTIONS.md.”

#### When generating Improvements.md:
> “Use the Improvements.md template from INSTRUCTIONS.md.”

#### When implementing code:
> “Follow the code output rules in project_instructions.txt.”

---

## 5. Versioning

- `project_instructions.txt` changes rarely  
- `INSTRUCTIONS.md` evolves over time  
- Design documents (Design‑v1.md, Design‑v2.md, etc.) are versioned  
- Improvements.md is mutable and updated continuously  

---

## 6. Summary

| File | Purpose | Location | Behaviour |
|------|----------|-----------|-----------|
| **project_instructions.txt** | Behavioural rules | Claude.ai Project Instructions | Always active |
| **INSTRUCTIONS.md** | Full specification & templates | Project files / repo | Referenced when needed |

Both files are required for a stable, predictable, and maintainable AI‑assisted development workflow.

---

If you are onboarding a new contributor or setting up a new Claude project, follow this README exactly.