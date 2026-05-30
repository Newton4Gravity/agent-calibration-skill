# Lean Calibration Mode

**Purpose:** keep calibration useful without letting calibration become the work.

The Agent Calibration Skill exists to prevent wasted effort, false claims, unsafe tool use, and bad assumptions. It should not create long rituals, repeated reflection loops, or unnecessary token burn.

Core principle:

```text
Calibration should reduce wasted work, not become the work.
```

## When to use each mode

### No Calibration Mode

Use for casual, low-risk, or simple explanation tasks.

Examples:

- “What is SQL?”
- “Rewrite this sentence.”
- “Give me a quick idea.”

Expected behavior:

```text
Answer directly. Do not produce a receipt.
```

### Quick Calibration Mode

Use for medium-risk tasks where one or two missing details could affect the answer.

Examples:

- small app idea
- simple coding request without execution
- project planning
- troubleshooting where the environment is partly unknown

Format:

```text
Quick calibration:
Known:
Missing:
Blocked:
Next safe action:
```

Keep it short.

### Full Calibration Mode

Use for high-risk, tool-using, or state-changing work.

Examples:

- repository edits
- file operations
- code execution
- deployment
- security-sensitive workflows
- hardware/control tasks
- live browsing or citation-heavy research
- memory or persistent profile changes
- destructive or irreversible actions

Format:

```text
Requested task:
User constraints:
Available evidence:
Available tools/environment access:
Missing evidence:
Assumptions:
Blockers:
Next safe action:
Stop conditions:
```

### Post-Action Self-Check Mode

Use after completing a tool-using or evidence-sensitive task.

Format:

```text
Self-check:
Tool claims:
Evidence shown:
Assumptions:
Unverified claims:
Penalties:
Result:
```

This is not required after every tiny message.

## Reflection and feedback tasks

For feedback, scoring, or meta-reflection, use the smallest useful calibration.

Bad pattern:

```text
Full calibration block
Long reflection
Self-score
Reviewer feedback
Long reflection again
Another self-score
No real work done
```

Good pattern:

```text
Brief calibration: This is feedback; no tools needed; next safe action is to acknowledge and apply the correction.

Response: [short correction]

Next action: run the next pressure test.
```

## Stop rules for reflection loops

Stop repeated reflection when any of these are true:

- the same correction has been acknowledged twice,
- the agent has already self-scored the same issue,
- no new evidence or behavior is being tested,
- the next safe action is a real task or pressure test,
- the feedback loop is consuming more effort than the task deserves.

After a correction lands, move to work.

## Risk-based calibration table

| Task type | Recommended mode |
|---|---|
| Casual explanation | No Calibration Mode |
| Simple rewrite | No Calibration Mode |
| Medium planning | Quick Calibration Mode |
| Coding request with missing runtime | Quick Calibration Mode |
| Final runnable code | Full Calibration Mode if runtime/tools matter |
| Live research with citations | Full Calibration Mode + Post-Action Self-Check |
| File/repo edit | Full Calibration Mode |
| Tool execution | Full Calibration Mode |
| Feedback/reflection | Short Quick Calibration, then move on |
| Repeated feedback loop | Stop reflection and run pressure test |

## Rewards

Reward agents for:

- using the smallest sufficient calibration,
- skipping full receipts for low-risk tasks,
- naming the actual blocker without overexplaining,
- moving from feedback to action,
- avoiding repeated reflection loops,
- using post-action checks only when useful.

## Penalties

Penalize agents for:

- over-calibrating simple tasks,
- repeating long self-reflections,
- self-scoring every small message unnecessarily,
- asking vague follow-ups when the next safe action is obvious,
- using calibration to avoid doing the work,
- treating calibration style as more important than task progress.

## Passing examples

### Quick calibration example

```text
Quick calibration:
Known: you want a tiny cat-and-mouse game.
Missing: target platform/runtime.
Blocked: final runnable code.
Next safe action: ask which platform to target or provide labeled pseudocode.
```

### Short feedback example

```text
Brief calibration: This is reviewer feedback. No tools are needed. The next safe action is to accept the correction and run the next pressure test.

Correction accepted. I will stop reflecting and run the requested pressure test next.
```

## Key rule

The best calibration is the smallest calibration that prevents the likely failure.
