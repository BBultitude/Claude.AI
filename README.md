# Claude.AI Project & Personal Chat System  
### Unified Instruction Framework for Claude.ai

This repository contains a complete instruction system for using Claude.ai effectively across both **Projects** and **Personal Chats**.  
It includes templates, handbooks, cheat sheets, and operational examples designed for clarity, maintainability, and token‑safe behaviour.

---

## 🔧 Core Setup Files

| File | Purpose | Usage |
|------|--------|-------|
| `project_instructions.txt` | Behavioural rules for Claude Projects | Paste into Claude.ai → Project Instructions panel |
| `INSTRUCTIONS.md` | Canonical templates and workflows | Upload to Claude Project Files |

These two files form the foundation of all Claude Project behaviour.  
They must be used together for predictable, stable, and compliant execution.

---

## 📁 Reference Materials

| File | Purpose |
|------|---------|
| `Projects Handbook.md` | Full operational guide for Claude Projects |
| `Projects Cheatsheet.md` | Quick-reference for project workflows |
| `Personal Chat Handbook.md` | Guide for using Claude outside Projects |
| `Personal Chat Cheatsheet.md` | Quick-reference for personal chat workflows |
| `Personal Chat Example.md` | Example of a well-structured account instructions focused on personal chat |

These files define best practices, reset workflows, instruction precedence, and token-protection strategies for both modes.

---

## 🧠 Instruction Model Summary

Claude uses a layered instruction model:

1. **In-chat instructions** — temporary, highest priority  
2. **Project instructions** — persistent, override profile and memory  
3. **Profile instructions** — default tone and behaviour  
4. **Memory** — long-term preferences  
5. **Model defaults** — fallback behaviour

This repo ensures all layers are aligned and documented.

---

## ✅ Setup Instructions

### For Projects:
1. Paste `project_instructions.txt` into the Claude.ai Project Instructions panel  
2. Upload `INSTRUCTIONS.md` to the Claude Project Files  
3. Use `Projects Handbook.md` and `Projects Cheatsheet.md` to guide workflows  
4. Follow architecture versioning and reset procedures as defined

### For Personal Chats:
1. Use `Personal Chat Handbook.md` and `Personal Chat Cheatsheet.md` to guide interactions  
2. Reference `Personal Chat Example.md` for formatting and structure  
3. Apply in-chat instructions as needed  
4. Reset context frequently and use portable context blocks

---

## 📌 Versioning & Maintenance

- `project_instructions.txt` changes rarely  
- `INSTRUCTIONS.md` evolves with workflow improvements  
- Handbooks and cheat sheets are updated as Claude’s behaviour evolves  
- All files are Markdown‑based for easy editing and version control

---

## 🧭 Recommended Usage

- Use this repo to onboard new contributors  
- Use it to initialise new Claude Projects  
- Use it to enforce consistent behaviour across teams  
- Use it to prevent drift, hallucination, and token waste  
- Use it to complement Microsoft 365 Copilot with Claude’s deeper reasoning capabilities

---

## 🔒 Compliance & Safety

All templates and workflows are designed to:

- prevent scope creep  
- enforce clarification  
- support auditability  
- minimise hallucination  
- protect tokens  
- align with enterprise security expectations

---

## 📂 File Index

```
INSTRUCTIONS.md
Personal Chat Cheatsheet.md
Personal Chat Example.md
Personal Chat Handbook.md
Projects Cheatsheet.md
Projects Handbook.md
README.md
project_instructions.txt
```

---