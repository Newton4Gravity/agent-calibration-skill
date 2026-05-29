# Blocker Scope Rule

**Purpose:** prevent agents from overblocking or underblocking work when only part of a task depends on missing information.

Not every blocker blocks the entire task.
Some blockers only block a specific mode, output type, or implementation path.

## Core rule

When an agent marks something as `[BLOCKER]`, it must state what is blocked.

A blocker should be scoped as one of:

- **Global blocker** — blocks all useful progress.
- **Mode blocker** — blocks only a specific mode, such as graphical output, deployment, persistence, or execution.
- **Quality blocker** — blocks final confidence, but still allows a draft, pseudocode, or partial analysis.
- **Safety blocker** — blocks action because the next step could modify systems, leak data, or cause harm without approval.

## Good pattern

```text
[BLOCKER] Final runnable graphical game is blocked because the graphics library is unknown.
[NOT BLOCKED] Language-neutral pseudocode can proceed.
[NOT BLOCKED] Text-based Python implementation can proceed if the user accepts terminal output.
```

## Bad pattern

```text
[BLOCKER] Graphics library unknown.
```

This is incomplete because it does not say whether all work is blocked or only graphical implementation is blocked.

## Examples

### Missing runtime

```text
[BLOCKER] Final runnable code is blocked because runtime/platform is unknown.
[NOT BLOCKED] Pseudocode can proceed if clearly labeled as not executed.
```

### Missing graphics library

```text
[BLOCKER] Graphical implementation is blocked because graphics library is unknown.
[NOT BLOCKED] Text-based implementation can proceed if compatible with the task.
```

### Missing repository access

```text
[BLOCKER] Evidence-based repository summary is blocked because repo/file access is unavailable.
[NOT BLOCKED] The agent can explain what evidence would be needed.
```

### Missing approval

```text
[BLOCKER] File creation is blocked until user approval.
[NOT BLOCKED] A proposed file plan can be shown in chat.
```

## Pass condition

A calibration receipt passes this rule when every blocker explains:

1. what is blocked,
2. why it is blocked,
3. what remains safe to do,
4. what single input or approval would unblock the next step.
