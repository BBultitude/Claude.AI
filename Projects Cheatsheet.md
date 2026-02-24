# Projects Cheatsheet
### *Operational shortcuts for fast, safe, predictable development inside Claude Projects*

---

## 1. Core Principles

- Keep tasks **small**  
- Reset context **every 20–30 messages**  
- Never brainstorm inside the Project  
- Keep architecture summaries updated  
- Use design versioning (`Design‑vX.md`)  
- Keep messages short and precise  
- **No open questions in design documents** — resolve everything before drafting  

---

## 2. Essential Commands

```
Act as ARCHITECT.
Act as STRATEGIST.
Re-anchor to instructions.
```

---

## 3. Reset Procedure (Use Often)

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

## 4. Task Workflow (Always Follow)

### Step 1 — Describe the goal
What you want, why, and the user outcome.

### Step 2 — Confirm the scope
Claude explains the change, affected documents, and plan.

### Step 3 — Execute
Claude produces output **only after approval**.

---

## 5. Design Completeness Rule

**A design document must not be submitted for approval if it contains unresolved questions.**

### ARCHITECT must:
- Complete requirements gathering **before** drafting  
- Pause and ask if a question arises mid-draft  
- Propose concrete recommendations when the user cannot answer  
- Never leave fields blank or write "TBD"  

### Placeholders (only when genuinely unknown until build):
Each placeholder requires **all four fields**:

| Field | Description |
|---|---|
| **What** | What is unknown or deferred |
| **Why** | Why it cannot be resolved before build |
| **When** | What build stage will resolve it |
| **Interim assumption** | What the design assumes in the meantime |

### Not permitted in any design document:
- "TBD"  
- "To be determined"  
- "To be confirmed"  
- Blank fields  
- Vague future references  

### If you see open questions in a design:
```
<task>Stop. This design is incomplete.</task>
<constraints>
- Return to requirements gathering
- Resolve all open questions before producing a new draft
- Do not resubmit until all fields are complete or valid placeholders with all four required fields
</constraints>
```

---

## 6. Safe Request Templates

### New Feature (Strategist)
```
<context>
Feature: [describe the feature]
User outcome: [what the user experiences]
</context>

<role>STRATEGIST</role>

<task>Assess architectural impact and add to Improvements.md.</task>

<constraints>
- Align with active Design-vX.md
- Do not treat as approved until I confirm
- Wait for my confirmation
</constraints>
```

### Architecture Change (Architect)
```
<context>
Change: [describe the change]
Reason: [why this change is needed]
</context>

<role>ARCHITECT</role>

<task>Assess implications and propose updated architecture.</task>

<constraints>
- Resolve all questions before producing a draft
- Do not submit a design with open questions
- Wait for my confirmation
</constraints>
```

### Reverse‑Engineering (Architect)
```
<context>File to analyse: [path]</context>

<role>ARCHITECT</role>

<task>Reverse-engineer the specified file.</task>

<format>
- Summary
- Purpose and system fit
- Risks or issues identified
</format>
```

### Documentation Update
```
<context>
File: [path]
Change: [description]
</context>

<task>Explain the proposed change and wait for my confirmation before modifying anything.</task>
```

---

## 7. Architecture & Planning

### Start a new project
```
<context>
Project type: [greenfield/brownfield/rebuild/etc]
Goal: [high-level outcome]
Initial scope: [first milestone]
</context>

<role>ARCHITECT</role>

<task>Confirm project type and begin requirements gathering.</task>

<constraints>
- Do not draft a design until all requirements are resolved
- Ask clarifying questions until everything is known
- Wait for my confirmation
</constraints>
```

### Move to planning
```
<role>STRATEGIST</role>
<task>Review the approved Design-vX.md and produce Improvements.md.</task>
<constraints>
- Align all items with the active design
- Wait for my confirmation
</constraints>
```

### Initiate Claude Code handoff
```
<context>Design and planning documents are approved and locked.</context>
<task>Confirm the handoff folder is ready for Claude Code.</task>
<constraints>Follow the process defined in Handoff.md.</constraints>
```

---

## 8. Drift Indicators

Claude is drifting if it:

- Forgets architecture  
- Asks for files that exist  
- Contradicts earlier decisions  
- Misinterprets instructions  
- Hallucinates file structure  
- Produces designs with open questions  

**Fix immediately:**

```
<task>Re-anchor to instructions.</task>
<constraints>
- Summarise the architecture
- Summarise the current task
</constraints>
```

---

## 9. Token‑Safe Practices

- Keep tasks small  
- Avoid long conversations  
- Avoid re‑explaining context  
- Never re‑upload files unless changed externally  
- Move brainstorming to a separate chat  
- Use micro‑tasks  

---

## 10. Never‑Do List

- Never brainstorm inside the Project  
- Never paste large content blocks unless required  
- Never request vague changes  
- Never let conversations run too long without resets  
- Never approve a design with open questions or TBD fields  
- Never mix exploration with planning  

---

## 11. Glossary

**Reset context** — Start a new chat inside the same Project. Clears conversation history, preserves all files.  
**Placeholder** — A design entry deferred to build time. Requires What, Why, When, and Interim Assumption.  
**Snapshot** — A point‑in‑time capture of architecture or state.  
**Checkpoint** — A summary of what was done and what's next.  
**Architecture summary** — A stable reference describing system structure.  
**Design‑vX.md** — Immutable, approved architecture version.  
**Handoff** — Approved documents passed to Claude Code for implementation.  
**Design Completeness Rule** — No design may be approved while it contains unresolved questions.  
**Codebase root** — The directory you launch Claude Code from (where you run `claude` in your terminal). CLAUDE.md must be placed here for auto-loading.

---

## 12. Claude Code Quick Reference

> **Before sending any prompt below:** Replace all `[bracketed placeholders]` with actual values. Unpopulated placeholders are passed literally to Claude Code and will cause incorrect behaviour.

### Session start prompt
```
<context>
Project documents are in this folder. Read them before proceeding.
</context>

<task>
Read all project documents:
1. Scan for all Design-v*.md files and identify the highest-numbered version as the active design
2. Read the active Design-vX.md
3. Read Improvements.md
4. Read CLAUDE.md
5. Read Handoff.md
6. Read any supporting documents

Confirm your understanding of the architecture, state which design version is active, and ask me which task to begin.
</task>

<constraints>
- Do not write any code until I confirm
- Ask if anything is ambiguous or conflicting
- If any required document is missing, stop and notify me before proceeding
</constraints>
```

### Assign a task
```
<context>
Current Improvements.md status: [note any recent changes if relevant]
</context>

<task>Implement this approved task from Improvements.md: [task title]</task>

<constraints>
- Follow the active Design-vX.md (auto-detected at session start)
- Follow acceptance criteria in Improvements.md
- State approach and affected files before coding
- Wait for my confirmation
</constraints>
```

### Stop a deviation
```
<task>Stop. Explain the deviation from the agreed approach.</task>
<constraints>Do not make further changes until I confirm the correct path.</constraints>
```

### Handle a gap discovery
```
<task>Stop the current implementation.</task>
<constraints>
- Document the issue: what was discovered, why it needs a decision, what the options are
- Do not proceed until I decide
</constraints>
```

Then return to Claude Projects with:
```
<context>Claude Code discovered the following issue: [paste issue]</context>

<role>ARCHITECT</role>

<task>Assess whether this requires a design change.</task>

<constraints>
- Produce updated design if needed
- Wait for my confirmation before locking
</constraints>
```

### CLAUDE.md rules
- Copy to the **codebase root** — the directory you launch Claude Code from (where you run `claude` in your terminal)
- Claude Code auto-detects the highest-numbered Design-vX.md — no manual version tracking required
- Update the last-updated date in `<version_reference>` on each revision
- Claude Code reads CLAUDE.md automatically at session start

### Never do in Claude Code
- Give verbal architecture instructions — put them in documents
- Skip the session-start document read
- Approve output without checking scope boundaries
- Let Claude Code proceed past a gap without a decision