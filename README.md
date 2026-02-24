# Claude Projects Instruction Framework
### *Unified Instruction Framework for Claude.ai Projects + Claude Code*

This repository contains a complete instruction system for using Claude Projects and Claude Code together across large, complex software projects.  
It includes templates, handbooks, cheat sheets, and operational guides designed for clarity, architectural integrity, and token‑safe behaviour.

---

## 🔧 Core Setup Files

| File | Purpose | Usage |
|------|---------|-------|
| `project_instructions.txt` | Behavioural rules for Claude Projects | Paste into Claude.ai → Project Instructions panel |
| `INSTRUCTIONS.md` | Canonical templates and workflows | Upload to Claude Project Files |
| `Handoff.md` | Boundary definition between Claude Projects and Claude Code | Upload to Claude Project Files and Claude Code project folder |
| `CLAUDE.md` | Persistent instruction file for Claude Code | Copy to codebase root — Claude Code reads it automatically |

These three files form the foundation of all behaviour.  
They must be used together for predictable, stable, and compliant execution.

---

## 📁 Reference Materials

| File | Purpose |
|------|---------|
| `Projects Handbook.md` | Full operational guide for Claude Projects |
| `Projects Cheatsheet.md` | Quick‑reference for project workflows |

---

## 🧠 Two‑Tool Architecture

This framework spans two tools with a clear boundary:

| Layer | Tool | Roles | Output |
|---|---|---|---|
| Design & planning | Claude Projects | ARCHITECT, STRATEGIST | Design‑vX.md, Improvements.md |
| Implementation | Claude Code | — | Code, tests, files |

**Claude Projects produces approved documents. Claude Code consumes them.**

Claude Code reads the approved design documents from the project folder, auto-detects the highest-numbered Design-vX.md as the active design, and implements code strictly aligned with it.

See `Handoff.md` for the full boundary definition, folder conventions, conflict resolution rules, and Claude Code operating sequence.

---

## 📐 Design Completeness Rule

Design documents must be **complete before approval**. No open questions, no "TBD" fields, no blank sections.

If an item cannot be determined until build time, it must be documented as a **Placeholder** with four required fields: What, Why, When, and Interim Assumption.

More complete designs produce fewer questions and better results from Claude Code.

---

## 🧠 Instruction Model Summary

Claude uses a layered instruction model:

1. **In‑chat instructions** — temporary, highest priority  
2. **Project instructions** — persistent, override profile and memory  
3. **Profile instructions** — default tone and behaviour  
4. **Memory** — long‑term preferences  
5. **Model defaults** — fallback behaviour

This repo ensures all layers are aligned and documented.

---

## ✅ Setup Instructions

1. Paste `project_instructions.txt` into the Claude.ai Project Instructions panel  
2. Upload `INSTRUCTIONS.md` and `Handoff.md` to the Claude Project Files  
3. Copy `Handoff.md`, approved design documents, `Improvements.md`, and `CLAUDE.md` to the **codebase root** — the directory you launch Claude Code from (where you run the `claude` command in your terminal). This is typically where `.git`, `package.json`, `requirements.txt`, or equivalent project-level files live. Claude Code auto-loads `CLAUDE.md` from this directory on startup. If you launch Claude Code from a different directory, `CLAUDE.md` will not be found and your instructions will not load.
4. Use `Projects Handbook.md` and `Projects Cheatsheet.md` to guide workflows  
5. Follow architecture versioning, design completeness, and reset procedures as defined  

---

## 📌 Versioning & Maintenance

- `project_instructions.txt` changes rarely  
- `INSTRUCTIONS.md` evolves with workflow improvements  
- `Handoff.md` is updated when the active design version changes  
- `CLAUDE.md` requires only the last-updated date to be maintained — active design version is auto-detected at session start  
- Handbook and cheatsheet are updated as Claude's behaviour evolves  
- All files are Markdown‑based for easy editing and version control  

---

## 🧭 Recommended Usage

- Use this repo to onboard new contributors  
- Use it to initialise new Claude Projects  
- Use it to enforce consistent behaviour across teams  
- Use it to prevent drift, hallucination, and token waste  
- Use it to maintain architectural integrity across the design-to-implementation pipeline  

---

## 🔒 Compliance & Safety

All templates and workflows are designed to:

- Prevent scope creep  
- Enforce clarification before design  
- Enforce completeness before approval  
- Support auditability  
- Minimise hallucination  
- Protect tokens  
- Align with enterprise security expectations  

---

## 📂 File Index

```
CLAUDE.md
Handoff.md
INSTRUCTIONS.md
Projects Cheatsheet.md
Projects Handbook.md
README.md
project_instructions.txt
```