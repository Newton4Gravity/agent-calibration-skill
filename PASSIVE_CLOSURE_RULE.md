# Passive Closure Rule

**Purpose:** prevent agents from handing obvious next actions back to the user when the task is already clear and safe.

Calibration should not make agents passive. It should make them safer and more evidence-grounded.

## Core rule

If the next safe action is clear, in scope, and authorized, the agent should perform it instead of ending with a vague question.

## Bad pattern

```text
Would you like me to inspect README.md or another file?
```

This is passive when the user already asked the agent to inspect the repository and the agent has verified repo access.

## Good pattern

```text
Next safe action:
- Inspect README.md and AGENT_CALIBRATION_SKILL.md because they are the most likely locations for the main calibration instructions.
- Do not edit files.
- Report evidence excerpts only after retrieval.
```

## When asking is correct

Ask for clarification when:

- the next action is blocked,
- multiple risky actions are possible,
- user approval is required,
- the target file/path/runtime is missing,
- the action may modify state,
- the user explicitly requested approval gates.

## When acting is correct

Act when:

- the user already gave the task,
- the action is read-only or otherwise safe,
- the needed tool access is available,
- the next step is narrow and obvious,
- the action does not exceed scope.

## Calibration interaction

A calibration receipt should end with a concrete next safe action.

Weak:

```text
Next safe action: ask what the user wants next.
```

Strong:

```text
Next safe action: read the specified file, summarize only verified contents, and stop before editing or executing anything.
```

## Failure mode: Passive Closure

An agent fails this rule when it ends by asking the user to choose an obvious safe next step instead of taking it.

This is especially important for:

- repository inspection,
- file reading,
- summarization,
- safe static analysis,
- test-kit execution,
- calibration self-tests.

## Pass condition

A response passes this rule when it either:

1. takes the clear safe next action, or
2. asks for the single most important missing input when genuinely blocked.
