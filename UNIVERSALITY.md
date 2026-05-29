# Universal Compatibility Principles

Agent Calibration Skill is not designed for one agent, one app, one coding tool, or one runtime.

It must work across:

- language-only agents
- tool-enabled agents
- coding agents
- research agents
- local agents
- repository agents
- IDE agents
- mobile agents
- browser-based agents
- enterprise agents
- future agent platforms that do not exist yet

## Core rule

Examples are not the standard.

Specific platforms such as ChatGPT, Claude Code, Cursor, Minis, Python IDE, local agents, or repository agents are only examples of environments where the skill can be used.

The skill itself must remain platform-neutral.

## Design target

The skill should calibrate any agent by asking universal questions:

```text
What task is being done?
What evidence is available?
What evidence is missing?
What can this agent actually verify?
What tools, if any, can this agent use?
What claims require labels?
What assumptions are blockers?
What actions require authorization?
What is the next safe action?
```

These questions apply no matter what platform the agent runs on.

## Avoid platform lock-in

Do not make the main skill depend on:

- a specific filename convention
- a specific skill loader
- a specific API
- a specific programming language
- a specific graphics framework
- a specific operating system
- a specific agent product
- a specific memory system
- a specific repository structure

Platform-specific guidance belongs in examples, adapters, or case studies — not in the core rule set.

## Correct relationship between core and examples

```text
Core skill = universal rules and receipts
Examples = platform-specific ways to apply the rules
Adapters = installation/invocation instructions for one environment
Case studies = observed failures and corrected responses
```

## Acceptance test

A change preserves universal compatibility only if it still works for all three broad categories:

1. **Language-only agent** — no tools, no files, no runtime.
2. **Tool-enabled agent** — general tools, but no guaranteed target environment.
3. **Environment-embedded agent** — connected to a specific runtime, repository, IDE, file system, or domain tool.

If a rule only works for one platform, move it to an example or adapter file.

## Important distinction

Minis-specific, Claude-specific, ChatGPT-specific, Cursor-specific, or Python-IDE-specific lessons may inspire the skill.

They must not define the skill.

The universal standard is:

```text
A calibrated agent must prove what it can know, what it cannot know, what it is assuming, and what it is allowed to do before trusted work begins.
```
