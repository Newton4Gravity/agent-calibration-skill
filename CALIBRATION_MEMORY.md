# Calibration Memory

Calibration can be more than a prompt.

When a platform supports memory, files, profiles, logs, or persistent state, calibration can become an adaptive correction layer.

A robot joint calibration may store an offset:

```text
raw motor command + joint offset = corrected movement
```

An AI-agent calibration can store a behavioral offset:

```text
raw model behavior + calibration profile = corrected agent behavior
```

---

## Universal Skill vs Calibration Memory

Keep these layers separate:

```text
Universal Skill
- The shared calibration standard.
- Must stay platform-neutral.

Calibration Receipt
- Proof that calibration happened in this session.

Calibration Memory
- Remembered correction patterns from past behavior.

Agent Profile
- Platform-specific or agent-specific compensation layer.
```

The core skill should work for everyone. Calibration memory adapts that universal standard to a specific agent, tool, robot, platform, or environment.

---

## What Calibration Memory Stores

Calibration memory should store behavior patterns and correction offsets, not private user data by default.

Recommended fields:

```yaml
agent_calibration_profile:
  agent_or_platform: "example-agent"
  profile_version: "1.0"
  last_calibrated: "YYYY-MM-DD"

  observed_failure_modes:
    skill_summary_not_execution:
      count: 2
      severity: high
      evidence: "Agent summarized the skill instead of producing a receipt."
      correction: "Require Calibration Receipt before task output."

    unverified_environment_assumption:
      count: 1
      severity: high
      evidence: "Agent assumed a graphics framework without verification."
      correction: "Treat runtime/platform assumptions as blockers."

  stable_rules:
    - "Skill summary is not skill execution."
    - "Runtime/platform assumptions are blockers."
    - "Examples are not the universal standard."

  required_offsets:
    - "Demand receipt before coding."
    - "Ask for target platform if runtime cannot be verified."
    - "Reject unsupported tool claims."

  retest_required:
    - "Run a small task requiring environment grounding."
```

---

## What Calibration Memory Must Not Do

Calibration memory must not invent current facts.

It must not claim:

- a file exists now unless checked now
- a tool is available now unless checked now
- a user wants the same thing now unless confirmed or context makes it clear
- a robot/hardware state is safe now unless telemetry or inspection confirms it
- a previous project state is still true without current evidence

Memory can say:

```text
This agent has previously failed by assuming runtime details.
Require stricter runtime grounding.
```

Memory must not say:

```text
The current runtime is Pythonista scene.
```

unless that is verified in the current session.

---

## Calibration Memory Workflow

```text
Observe behavior
    ↓
Label failure mode
    ↓
Record correction offset
    ↓
Apply offset next session
    ↓
Retest
    ↓
Update profile
```

---

## Example Correction Offset

Observed behavior:

```text
Agent says: "The skill_id is agent_calibration_skill."
```

Detected failure:

```text
[FAILURE] Skill acknowledged but not executed.
```

Stored offset:

```yaml
required_offsets:
  - "Do not accept skill ID acknowledgement as execution. Require Calibration Receipt."
```

Future behavior:

```text
Before task output, agent must produce a Calibration Receipt.
```

---

## Design Rule

The universal skill should remain stable and platform-neutral.

Calibration memory should be modular:

```text
profiles/chatgpt.md
profiles/claude-code.md
profiles/cursor.md
profiles/local-agent.md
profiles/robot-agent.md
profiles/generic-template.md
```

Profiles are optional adapters. They should never redefine the universal standard.
