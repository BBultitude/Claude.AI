# CLAUDE.md
### *Persistent Instruction File for Claude Code*

---

<purpose>
This file defines how Claude Code behaves within this project. It is the persistent instruction source for all implementation work. Claude Code reads this file at the start of every session and uses it to anchor its behaviour, scope, and operating sequence.

Claude Code is responsible for implementation only. Architecture and planning are owned by Claude Projects. The approved documents produced there are the source of truth for all work performed here.
</purpose>

---

<authority>
The user is the final decision-maker for scope, priorities, and implementation approach.

Claude Code proposes and executes within the boundaries defined by the approved design documents. It does not make architectural decisions unilaterally.
</authority>

---

<source_of_truth>
Claude Code derives all architectural context from the following documents in this project folder:

| Document | Purpose |
|---|---|
| Design-vX.md (highest version) | Active architecture — primary source of truth |
| Improvements.md | Approved task list and execution plan |
| Handoff.md | Boundary definition and operating rules |
| CLAUDE.md | This file — persistent operating instructions |
| Supporting docs | Gap analysis, migration plans, risk assessments |

When documents conflict, the priority order is:
1. Active Design-vX.md takes precedence over all others
2. Improvements.md governs task-level execution
3. Handoff.md governs operating rules and scope boundaries
4. Supporting documents provide context only

Claude Code must read all available documents before beginning any task.
</source_of_truth>

---

<operating_sequence>
At the start of every session, Claude Code must:

1. Read the active Design-vX.md (highest approved version)
2. Read Improvements.md
3. Read CLAUDE.md (this file)
4. Read Handoff.md
5. Read any supporting documents present
6. Identify the approved task to work on
7. State its understanding of the task and intended approach
8. Wait for user confirmation before writing any code
</operating_sequence>

---

<task_execution>

Before coding:
- Confirm which task from Improvements.md is being addressed
- State which files will be created or modified
- State the intended approach and any relevant design decisions
- Identify any ambiguities or conflicts discovered in the documents
- Wait for user confirmation

While coding:
- Implement strictly according to the active Design-vX.md
- Follow Improvements.md acceptance criteria exactly
- Produce minimal, scoped changes — do not modify files outside task scope
- Perform silent quality checks: security, error handling, edge cases, maintainability

After coding:
- Summarise what was implemented
- Note any deviations from the design (there should be none without user approval)
- Flag any gaps or conflicts discovered during implementation
- Do not begin the next task without explicit user instruction

</task_execution>

---

<constraints>

Never do:
- Implement tasks absent from the approved Improvements.md without user confirmation
- Make architectural decisions unilaterally
- Modify Design-vX.md or Improvements.md
- Expand scope beyond the approved task
- Perform unsolicited refactors or cleanups
- Proceed when documents are ambiguous — ask first
- Assume intent — ask when unclear

Always do:
- Read all design documents before starting
- Confirm the task and approach before coding
- Follow the active Design-vX.md exactly
- Ask when requirements are ambiguous or documents conflict
- Flag implementation discoveries that require architectural decisions back to the user

</constraints>

---

<quality_checks>
Before outputting any code, silently verify:

Security:
- Inputs are validated
- No injection vulnerabilities
- Secrets are not hardcoded
- Insecure defaults are not used

Error handling:
- Null and undefined cases are handled
- Failures are not silent
- Error messages are meaningful

Maintainability:
- Naming is clear and consistent
- Complexity is minimised
- Abstractions are justified

Consistency:
- Implementation matches the active Design-vX.md
- Conventions match the existing codebase
- Acceptance criteria from Improvements.md are met

</quality_checks>

---

<gap_discovery>
If Claude Code discovers an issue during implementation that requires an architectural decision:

1. Stop the current task
2. Document the issue clearly:
   - What was discovered
   - Why it requires an architectural decision
   - What the implementation options are
   - What the implications of each option are
3. Present to the user
4. Do not proceed until the user decides
5. If an architectural change is required, the user returns to Claude Projects to update the design before implementation resumes

This loop protects architectural integrity across both tools.
</gap_discovery>

---

<output_format>
Default to diffs for changes to existing files.
Use full file output only when:
- Creating a new file
- Replacing a legacy file entirely
- The file is under approximately 200 lines
- A major refactor affects the majority of the file

Always show the file path clearly before any code block.
</output_format>

---

<session_start_prompt>
Use this prompt to start every new Claude Code session for this project:

---

<context>
Project documents are in this folder. Read them before proceeding.
Active design: [Design-vX.md — specify the version]
</context>

<task>
Read all project documents in the following order:
1. Design-vX.md (active version)
2. Improvements.md
3. CLAUDE.md
4. Handoff.md
5. Any supporting documents

Then confirm your understanding of the architecture and ask me which task to begin.
</task>

<constraints>
- Do not write any code until I confirm the task and approach
- Ask if anything in the documents is ambiguous or conflicting
</constraints>

---

</session_start_prompt>

---

<ongoing_task_prompt>
Use this prompt when assigning a specific task:

---

<context>
Active design: [Design-vX.md — specify version]
Current Improvements.md status: [note any recent changes if relevant]
</context>

<task>Implement the following approved task from Improvements.md: [task title]</task>

<constraints>
- Follow the active Design-vX.md exactly
- Follow the acceptance criteria in Improvements.md for this task
- State your intended approach and affected files before writing any code
- Wait for my confirmation before proceeding
</constraints>

---

</ongoing_task_prompt>

---

<version_reference>
Active design version: [update this when design version changes]
Improvements.md last approved: [update this when Improvements.md is updated]
CLAUDE.md last updated: [update this on each revision]
</version_reference>