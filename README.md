# Project Instruction Templates — How to Use

This repository contains two templates for managing Claude-based development projects:

1. `project-template-new.md` — For **new (greenfield) projects**
2. `project-template-existing.md` — For **existing (brownfield) projects**

Each template defines:
- How Claude should behave
- How documentation is created and maintained
- How sprints and tasks are structured
- How testing is performed
- How cybersecurity is enforced
- How project-specific rules are applied

---

# Choosing the Right Template

Use the decision tree below:

## ✔ Use the **New Project Template** if:
- You are building something from scratch  
- No code exists yet  
- No architecture exists  
- No documentation exists  
- You need a **Design.md**  
- You want Claude to design the system before coding  

This is your **greenfield** workflow.

---

## ✔ Use the **Existing Project Template** if:
- The system already exists  
- You are adding features  
- You are modifying behaviour  
- You are fixing bugs  
- You are applying security patches  
- You are refactoring or improving performance  

This is your **brownfield** workflow.

---

# Special Case: Old Project With No Design.md

If you have an existing system **but no Design.md**, use the **Existing Project Template**.

Claude will:
1. Load the existing project files  
2. Ask clarifying questions  
3. Reverse-engineer the architecture  
4. Build a **Design-Reconstruction.md**  
5. Freeze it as the new source of truth  
6. Only then begin enhancements  

This ensures long-term maintainability.

---

# Workflow Summary

## New Project Workflow
1. Create a new Claude project  
2. Paste `project-template-new.md` into Project Instructions  
3. First chat → Claude builds Design.md  
4. Approve Design.md  
5. Begin sprints and coding  
6. Maintain Design.md as the project evolves  

---

## Existing Project Workflow
1. Create a new Claude project  
2. Paste `project-template-existing.md` into Project Instructions  
3. First chat → Claude builds Improvements.md or Design-Reconstruction.md  
4. Approve the document  
5. Begin enhancement sprints  
6. Maintain Improvements.md or Reconstruction.md  

---

# Why Two Templates?

New builds and existing systems have fundamentally different workflows:

| Project Type | Required Document | First Chat Mode | Purpose |
|--------------|-------------------|------------------|---------|
| New Project | Design.md | Design Builder Mode | Define architecture before coding |
| Existing Project (with Design.md) | Improvements.md | Improvements Builder Mode | Define enhancement scope |
| Existing Project (no Design.md) | Design-Reconstruction.md | Reconstruction Mode | Reverse-engineer architecture |

Keeping these separate ensures:
- Predictability  
- Maintainability  
- Security  
- Clear documentation  
- Efficient token usage  

---

# Recommended Folder Structure# Claude.AI-Project-Instructions
Detailed templates for Claud.AI to work with projects
