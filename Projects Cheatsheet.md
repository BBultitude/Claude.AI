### *Operational shortcuts for fast, safe, predictable development inside Claude Projects*

---

## 1. Core Principles

- Keep tasks **small**  
- Reset context **every 20–30 messages**  
- Never brainstorm inside the Project  
- Always request a **diff plan** before code  
- Use **Explain Before You Change**  
- Avoid full‑file rewrites unless necessary  
- Keep architecture summaries updated  
- Use design versioning (`Design‑vX.md`)  
- Keep messages short and precise  

---

## 2. Essential Commands

```
Act as ARCHITECT.
Act as STRATEGIST.
Act as ENGINEER.
Re-anchor to instructions.
```

---

## 3. Reset Procedure (Use Often)

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

## 4. Task Workflow (Always Follow)

### Step 1 — Describe the goal  
What you want, why, and the user outcome.

### Step 2 — Confirm the scope  
Claude explains the change, affected files, and diff plan.

### Step 3 — Execute  
Claude generates code **only after approval**.

---

## 5. Diff‑First Rules

### Use diffs when:
- Fixing bugs  
- Adding small features  
- Updating logic  
- Editing documentation  
- Changing a few lines  

### Use full‑file regeneration when:
- Creating a new file  
- Replacing legacy code  
- Rewriting files under ~200 lines  
- Major refactors  
- Structural changes  

---

## 6. Safe Request Templates

### New Feature
```
New feature request:
<feature>
User outcome:
<outcome>

Act as ENGINEER.
Explain before you change.
Provide a diff plan.
Wait for my confirmation.
```

### Bug Fix
```
Bug fix:
<bug>
Expected:
<expected>
Actual:
<actual>

Act as ENGINEER.
Explain root cause.
Provide a diff plan.
Wait for my confirmation.
```

### Refactor
```
Refactor request:
<goal>
Non-goals:
<what must not change>

Act as ENGINEER.
Explain the refactor.
Provide a diff plan.
```

### Modify Existing File
```
Modify file: <path>
Change: <description>
Scope: <minimal/moderate/major>

Act as ENGINEER.
Explain the change.
Provide a diff plan.
```

### New File
```
Create a new file:
<path>

Purpose:
<purpose>

Act as ENGINEER.
Explain structure.
Wait for my confirmation.
```

---

## 7. Architecture & Planning

### Start a new project
```
We are starting a new project.

Project type: <greenfield/brownfield/rebuild/etc>
Goal: <high-level outcome>
Initial scope: <first milestone>

Act as ARCHITECT.
Confirm project type.
Summarise architecture.
Identify missing information.
Wait for my confirmation.
```

### Move to planning
```
Act as STRATEGIST.
Break into phases, sprints, and tasks.
Wait for my confirmation.
```

### Move to implementation
```
Act as ENGINEER.
Begin with the first approved task.
Explain before you change anything.
Wait for my confirmation.
```

---

## 8. Drift Indicators

Claude is drifting if it:

- Forgets architecture  
- Asks for files that exist  
- Rewrites entire files unexpectedly  
- Contradicts earlier decisions  
- Misinterprets instructions  
- Hallucinates file structure  

**Fix immediately:**

```
Re-anchor to instructions.
Summarise the architecture.
Summarise the current task.
```

---

## 9. Token‑Safe Practices

- Keep tasks small  
- Avoid long conversations  
- Avoid re‑explaining context  
- Never re‑upload files unless changed externally  
- Move brainstorming to personal chats  
- Use micro‑tasks  
- Avoid unnecessary full‑file rewrites  

---

## 10. Never‑Do List

- Never brainstorm inside the Project  
- Never paste large code blocks unless required  
- Never request vague changes  
- Never skip diff plans  
- Never mix exploration with implementation  
- Never let conversations run too long without resets  

---

## 11. Glossary (Quick)

**Reset context** — Start a new chat inside the same Project.  
**Diff** — A minimal set of changes to a file.  
**Refactor** — Improve code without changing behaviour.  
**Snapshot** — A point‑in‑time capture of architecture or state.  
**Checkpoint** — A summary of what was done and what’s next.  
**Architecture summary** — A stable reference describing system structure.  
**Design‑vX.md** — Immutable architecture version.  

---