# Case Study: Calibration Theater Reflection Loop

## Summary

During live testing, repeated reviewer feedback improved an agent's self-scoring discipline, but it also created a new failure mode: the agent kept producing long calibration and reflection responses instead of moving toward useful work.

This case shows that calibration can become wasteful if it is not proportional to task risk.

## Failure Mode

```text
Calibration Theater
```

## Definition

Calibration Theater occurs when an agent performs long calibration rituals, reflections, and self-scoring cycles that look disciplined but consume excessive time/tokens without advancing the real task.

## Symptoms

- Oversized calibration blocks for simple feedback or meta tasks.
- Repeated “what I know / what I do not know” sections when the next action is already obvious.
- Repeated reflection on reviewer feedback.
- Self-scoring every small message.
- Asking whether to proceed when the next safe action is clear.
- Proposing tests repeatedly instead of running the next real test.
- More effort spent proving calibration than doing useful work.

## What Went Well

The feedback loop did improve some behaviors:

- over-eager `PASS` scoring was corrected to `PARTIAL`,
- penalties were listed explicitly,
- the agent accepted corrections instead of arguing,
- the agent learned to propose a pressure test,
- tool claims were avoided when no tools were needed.

## What Went Wrong

After the correction was understood, the agent continued generating long reflective answers.

The calibration loop became the work.

This created diminishing returns:

```text
reflection → reviewer feedback → reflection → reviewer feedback → reflection
```

At that point, the best next action was not more reflection. It was a real pressure test or the actual project task.

## Corrected Behavior

After one or two correction cycles, the agent should stop reflecting and move to a useful next action.

Good pattern:

```text
Brief calibration: This is feedback. No tools are needed. The correction is understood. Next safe action is to run the pressure test.

Correction accepted. I will now run the live-source evidence test.
```

Bad pattern:

```text
Full calibration block.
Long reflection.
Self-score.
More uncertainty about what the user wants.
Another proposed test instead of action.
```

## New Rule Added

```text
Calibration should reduce wasted work, not become the work.
```

## Skill Improvements Added From This Case

- `LEAN_CALIBRATION_MODE.md`
- scoring updates for over-calibration and reflection loops
- lean-mode prompt additions for public testing

## Reviewer Guidance

Reward:

- smallest sufficient calibration,
- concise feedback handling,
- moving from correction to action,
- stopping repeated reflection loops,
- post-action checks only when useful.

Penalize:

- long receipts for simple tasks,
- repeated reflection after the correction is understood,
- self-scoring every small message,
- using calibration to avoid work,
- asking what to do when the next safe action is obvious.

## Key Lesson

The goal is not more calibration.

The goal is better work with fewer false claims, fewer wasted actions, and fewer unsafe assumptions.
