# Installation and Invocation Guide

This project must work across many platforms, so installation depends on the agent or tool you are using.

The important distinction is this:

```text
Pasted Markdown ≠ installed skill
File exists ≠ registered skill
Registered skill ≠ invoked skill
Invoked skill ≠ completed calibration
Completed calibration = Calibration Receipt produced
```

---

## The Five States

### 1. Pasted Markdown

The user pastes `AGENT_CALIBRATION_SKILL.md` into chat.

This gives the agent context, but it may not create a real skill.

### 2. File Exists

The skill file exists somewhere, such as:

```text
agent_calibration_skill/SKILL.md
```

This proves only that a file exists. It does not prove the agent can find it or will follow it.

### 3. Registered Skill

The platform recognizes the skill by ID, name, folder, or manifest.

Example:

```text
skill_id = agent_calibration_skill
```

This proves the platform can identify the skill. It does not prove the skill was run.

### 4. Invoked Skill

The agent attempts to apply the skill to the current task.

This is still incomplete unless it produces the required output.

### 5. Calibration Receipt Produced

The agent outputs a complete Calibration Receipt.

This is the proof that calibration happened.

---

## Universal Verification Flow

Use this sequence on any platform:

```text
install or paste
    ↓
verify file/context exists
    ↓
verify the agent can access it
    ↓
invoke calibration
    ↓
require Calibration Receipt
    ↓
start task only after receipt passes
```

---

## Required Invocation Prompt

```text
Run agent_calibration_skill before doing the task.

Do not summarize the skill.
Do not only acknowledge the skill ID.
Do not produce task output yet.

First produce a complete Calibration Receipt with:
- requested task
- user constraints
- available evidence
- available tools/environment access
- missing evidence
- agent type for this task
- non-blocking assumptions
- blocker assumptions
- next safe action
- stop conditions
```

---

## If The Agent Only Summarizes The Skill

Use this correction:

```text
Stop. You described the skill but did not run it.
Running the skill requires a Calibration Receipt.
Produce the receipt now. No task output yet.
```

---

## If The Agent Only Says The Skill ID

Use this correction:

```text
Stop. Skill ID acknowledgement is not skill execution.
Produce the Calibration Receipt now.
```

---

## If The Agent Starts Coding Too Early

Use this correction:

```text
Stop. You produced task output before calibration completed.
Identify the failure mode, then produce the Calibration Receipt.
Do not continue the code until blocker assumptions are resolved.
```

---

## Platform Notes

This guide is platform-neutral.

For platforms with real skill systems, place this repository's main skill text where that platform expects skill instructions.

For platforms without skill systems, paste either:

- `AGENT_CALIBRATION_SKILL.md` for full calibration
- `AGENT_CALIBRATION_COMPACT.md` for daily use

For platforms with memory, optionally store calibration profiles as described in `CALIBRATION_MEMORY.md`.
