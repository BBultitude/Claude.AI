### *Fast, safe, predictable workflows for everyday use with Claude*

---

## 1. Core Principles

- Personal chats have **no persistent files**  
- Personal chats have **no project instructions**  
- Personal chats drift **faster**  
- Reset context **often**  
- Keep tasks **small**  
- Use **portable context blocks**  
- Use **checkpoints** every 10–15 messages  
- Instructions are **task‑specific**, not global  

---

## 2. Instruction Layers (Know the Hierarchy)

### 1. **In‑Chat Instructions** (highest priority)
Temporary, task‑specific, override everything else.

### 2. **Profile Instructions**
Persistent defaults for tone, behaviour, formatting.

### 3. **Memory**
Long‑term preferences and personal details.

### 4. **Model Defaults** (lowest priority)

---

## 3. Reset Context (Personal Chats)

### When to reset:
- Every **15–25 messages**  
- After long reasoning chains  
- After major topic changes  
- When drift is detected  

### Reset workflow:
```
Summarise what we’re doing, the decisions made, constraints, and next steps.
Make it concise and suitable for starting a new chat.
```

Then:

1. Start a **new chat**  
2. Paste the summary  
3. Continue cleanly  

---

## 4. Portable Context Blocks

Ask Claude to generate a block you can paste into a new chat:

```
Create a portable context block summarising:
- the goal
- decisions made
- constraints
- examples
- next steps
Make it concise.
```

---

## 5. Checkpoint Habit

Every 10–15 messages:

```
Give me a checkpoint summary of what we’ve done and what’s next.
```

This prevents losing information during resets.

---

## 6. Drift Indicators

Claude is drifting if it:

- repeats questions  
- forgets earlier details  
- contradicts itself  
- becomes generic  
- asks for context you already gave  
- loses track of the task  

**Fix immediately:**

```
Summarise the task, decisions, constraints, and next steps.
Make it suitable for starting a new chat.
```

---

## 7. Safe Instruction Patterns

### Tone
```
Use a concise, technical tone for this task.
```

### Format
```
Format the output as a table.
```

### Reasoning
```
Explain your reasoning before giving the final answer.
```

### Output constraints
```
Keep the answer under 200 words.
```

### Override profile instructions
```
For this task only, ignore previous tone preferences.
```

---

## 8. Task‑First Workflow

Always specify:

- the goal  
- the constraints  
- the format  
- the audience  

Example:
```
Write a concise explanation of <topic>.
Audience: <audience>.
Format: bullet points.
Tone: neutral and technical.
```

---

## 9. Safe Request Templates

### Writing
```
Write a clear explanation of <topic>.
Tone: <tone>.
Format: <format>.
Length: <limit>.
```

### Planning
```
Create a step-by-step plan for <goal>.
Include risks, dependencies, and next actions.
```

### Data
```
Analyse the following data:
<dataset>

Provide:
- summary
- insights
- anomalies
- recommendations
```

### Excel
```
I need an Excel formula for:
<goal>

Provide:
- the formula
- a short explanation
```

### Creative
```
Write a short story in <style>.
Length: <limit>.
Constraints: <constraints>.
```

### Images
```
Describe an image concept based on:
<idea>
```

---

## 10. Token‑Safe Practices

- keep tasks small  
- reset often  
- avoid long chats  
- avoid re‑explaining context  
- use portable context blocks  
- use checkpoints  
- avoid unnecessary detail  
- avoid multi‑task messages  

---

## 11. Never‑Do List

- never let chats run too long  
- never rely on Claude to remember past chats  
- never give global instructions inside a chat  
- never mix multiple tasks in one message  
- never paste huge blocks of text unless necessary  
- never brainstorm endlessly in the same thread  

---

## 12. Glossary (Personal‑Chat‑Specific)

**Profile instructions** — Persistent global defaults for tone, behaviour, and formatting.  
**In‑chat instructions** — Temporary instructions that apply only to the current chat.  
**Memory** — Long‑term preferences and personal details.  
**Reset context (personal)** — Start a new chat and paste a summary from the previous one.  
**Checkpoint** — A summary of progress and next steps.  
**Portable context block** — A structured summary designed to be pasted into a new chat.  
**Drift** — Loss of accuracy due to context compression.  

---
