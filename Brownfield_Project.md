# Master Project Instructions — Existing Project (Brownfield)

## 1–10
(Identical to the New Project Template — copy Sections 1–10 exactly.)

---

## 11. Project Type: Enhancement / Maintenance (Brownfield)

### 11.1 Determine Documentation State
If the original project has:
- A valid Design.md → Build **Improvements.md**
- No Design.md → Build **Design-Reconstruction.md**

### 11.2 First Chat Behaviour
If Improvements.md or Design-Reconstruction.md does not exist:
- Enter **Builder Mode**
- No code is to be written
- Ask clarifying questions
- Analyse existing project files
- Build the required document
- Wait for approval before writing any code

---

## 12. Improvements.md Requirements
Improvements.md must include:
- Summary of the original system (reference Design.md)
- Scope of enhancements or fixes
- Why the changes are needed
- How the changes will be implemented
- Security considerations
- Impact on existing architecture
- Compatibility notes
- Migration steps (if required)
- Updated sprint plan
- Known limitations
- Future planned improvements

---

## 13. Design-Reconstruction.md Requirements
If no Design.md exists:
- Reverse-engineer architecture from existing code
- Document:
  - System purpose
  - Architecture
  - Data flows
  - Security model
  - Dependencies
  - Known issues
  - Limitations
  - Future work
- Freeze this as the new source of truth

---

## 14. After Document Approval
- Begin enhancement sprints
- Maintain Improvements.md or Reconstruction.md