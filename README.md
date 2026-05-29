# Agent Calibration Skill

A universal preflight protocol for reducing AI-agent hallucination, tool misuse, loop behavior,
passive closure, unverifiable claims, and unsafe action.

This repository contains `AGENT_CALIBRATION_SKILL.md`, a portable Markdown skill you can paste
into AI agents, coding assistants, local agents, research agents, or tool-using workflows.

## Use it now

Open [`AGENT_CALIBRATION_SKILL.md`](./AGENT_CALIBRATION_SKILL.md), copy the **Universal System Prompt**, and paste it into a new AI-agent session before starting important work.

For a shorter intervention during a bad session, use [`quick-reference-card.md`](./quick-reference-card.md).

## What problem does this solve?

AI agents often fail in predictable ways:

- They fabricate tool output.
- They claim they verified something they did not verify.
- They invent files, APIs, citations, logs, or test results.
- They loop on broken approaches.
- They become passive after receiving enough information.
- They overcorrect into paralysis after being corrected.
- They verify one part of an answer and declare the whole thing verified.
- They take or suggest high-impact actions without enough evidence.

This skill creates a repeatable calibration process before trusting an agent’s work.

## Core idea

Before an agent begins real work, establish:

```text
what it can access
what it can verify
what counts as evidence
how uncertainty will be labeled
what failure modes trigger correction
what actions require explicit authorization
```

## Quick start

Paste the **Universal System Prompt** section from `AGENT_CALIBRATION_SKILL.md` into a new agent session.

For a full preflight, run:

1. Phase 1 — Identity Declaration
2. Phase 2 — Grounding
3. Phase 3 — Calibration Test
4. Then begin the actual task

## Recommended path

```text
1. Copy the Universal System Prompt.
2. Paste it into your AI agent.
3. Start your actual task.
4. Use the Quick Reference Card if the agent drifts, loops, fabricates, or freezes.
```

## Repository contents

```text
AGENT_CALIBRATION_SKILL.md
README.md
quick-reference-card.md
session-log-template.md
CHANGELOG.md
CONTRIBUTING.md
LICENSE
PUBLISHING.md
.gitignore
.github/ISSUE_TEMPLATE/failure-mode-report.md
examples/
  chatgpt.md
  claude-code.md
  cursor.md
  local-agent.md
  research-agent.md
```

## What this is not

This is not a technical guarantee against hallucination.

It is a behavioral calibration protocol designed to make agent failures easier to prevent,
detect, name, and recover from.

## Recommended use cases

- coding agents
- Claude Code skills
- ChatGPT project instructions
- local agents
- Obsidian / knowledge-base workflows
- research agents
- file-cleanup agents
- repo-level `AGENTS.md` or `CLAUDE.md` policies
- agent evaluation sessions

## Suggested repository topics

```text
ai-agents
agent-safety
prompt-engineering
ai-hallucination
claude-code
chatgpt
cursor
agent-workflows
verification
ai-tools
```

## Share text

```text
I published Agent Calibration Skill v2.1.

It is a universal preflight protocol for AI agents that helps reduce hallucinated output, fake tool claims, loop behavior, passive closure, and unverifiable assumptions.

Instead of only fact-checking after an agent produces bad output, it calibrates the agent before real work begins.
```

## License

MIT. Use, copy, adapt, and remix freely.
