# Calibration Workspace

A calibration workspace is an optional file-backed area where an agent records calibration evidence, approvals, blockers, and profile updates while calibration is in progress.

The workspace turns calibration from a one-time chat response into a governed process.

---

## Core Rule

Calibration always requires a Calibration Receipt.

Calibration may create or update files only when:

1. The platform supports file writing.
2. The user approves file creation or editing.
3. The agent records the file work in the Calibration Receipt or session log.
4. The agent does not treat file creation as proof that calibration passed.

```text
Receipt first.
File writes only with permission.
User approval before persistence.
Snapshot after pass.
```

---

## Three Modes

### 1. Chat-Only Mode

Use when the agent has no file access or the user does not approve file creation.

Behavior:

- Produce the Calibration Receipt in chat.
- Track blockers in chat.
- Ask for approval in chat.
- Do not claim memory or persistence.

### 2. Workspace Mode

Use when the agent has approved file access.

Behavior:

- Create a workspace folder.
- Write calibration artifacts.
- Update artifacts as blockers are resolved.
- Record approvals.
- Produce a final pass/fail result.

### 3. Persistent Mode

Use only after user approval.

Behavior:

- Save approved calibration offsets to a profile or memory file.
- Preserve the final calibration snapshot.
- Do not silently modify approved state later.

---

## Recommended Workspace Structure

```text
.calibration/
  RECEIPT.md
  AGENT_PROFILE.md
  BLOCKERS.md
  APPROVALS.md
  SESSION_LOG.md
  CHANGELOG.md
  snapshots/
    passed-YYYY-MM-DD-HHMM/
      RECEIPT.md
      AGENT_PROFILE.md
      BLOCKERS.md
      APPROVALS.md
      SESSION_LOG.md
      CHANGELOG.md
```

Alternative repo-friendly path:

```text
agent-calibration/
  receipt.md
  profile.md
  blockers.md
  approvals.md
  session-log.md
  changelog.md
```

---

## Workspace Lifecycle

```text
Start calibration
    ↓
Create receipt
    ↓
Identify blockers
    ↓
Ask for missing input or approval
    ↓
Update artifacts
    ↓
Retest
    ↓
User approves pass
    ↓
Create final snapshot
    ↓
Persist approved profile offsets if allowed
```

---

## File Roles

### RECEIPT.md

The main proof that calibration happened.

Contains:

- requested task
- user constraints
- available evidence
- available tools/environment
- missing evidence
- agent type
- assumptions
- blocker assumptions
- next safe action
- stop conditions
- pass/fail status

### AGENT_PROFILE.md

Stores calibration offsets for the agent or platform.

Contains:

- observed failure modes
- required corrections
- stable behavioral rules
- retest requirements
- approved persistence notes

### BLOCKERS.md

Tracks unresolved blockers.

Contains:

- blocker description
- why it matters
- evidence needed
- owner/user input needed
- current status

### APPROVALS.md

Records user-approved decisions.

Contains:

- file creation approval
- platform/runtime approval
- package/tool approval
- persistence approval
- high-impact action approval

### SESSION_LOG.md

Records what happened during calibration.

Contains:

- prompts
- responses
- tool/file actions
- failures observed
- corrections applied
- retest results

### CHANGELOG.md

Records changes to the calibration artifacts.

Contains:

- timestamp
- file changed
- reason
- approval source
- summary

---

## Approval Gates

The agent must ask before:

- creating a workspace in a user repo or filesystem
- editing existing calibration files
- persisting memory/profile offsets
- changing production/project files
- deleting or replacing any file
- applying approved calibration state to future sessions

Recommended approval prompt:

```text
I can create a calibration workspace with these files:
- RECEIPT.md
- AGENT_PROFILE.md
- BLOCKERS.md
- APPROVALS.md
- SESSION_LOG.md
- CHANGELOG.md

This will only record calibration state and will not modify project code.
Approve creating this workspace?
```

---

## Snapshot Rule

After calibration passes, create a snapshot rather than continuing to rewrite the final state.

```text
.calibration/snapshots/passed-YYYY-MM-DD-HHMM/
```

The snapshot should preserve:

- final receipt
- final profile
- final blockers status
- final approvals
- final session log
- changelog

New calibration sessions should create new snapshots.

---

## Safety Rules

- Do not create files if the platform has no file writing ability.
- Do not claim files were created unless they were actually written.
- Do not silently persist calibration memory.
- Do not use calibration files as proof of current runtime state unless they were verified in the current session.
- Do not overwrite user project files during calibration.
- Do not continue editing indefinitely; stop when blockers are resolved or a real blocker remains.

---

## Pass Condition

Calibration passes when:

1. A complete Calibration Receipt exists.
2. Blocker assumptions are resolved or explicitly accepted by the user.
3. Required approvals are recorded.
4. The agent demonstrates calibrated behavior on a small test.
5. The user approves the pass result.
6. A final snapshot is created if workspace mode is active.

Calibration does not pass merely because files were created.
