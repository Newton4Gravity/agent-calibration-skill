# Quick Reference Card

Use this when an agent starts drifting, hallucinating, looping, or freezing.

```text
OBSERVED                                 RESPONSE
───────────────────────────────────────  ─────────────────────────────────────
Fake output shown                        Stop. That is fabricated or unaudited.
                                         What evidence do you actually have?

Invented facts / APIs / citations        Source it or label it [ASSUMED].

Same broken approach again               Stop the loop. What missing evidence
                                         would change the next attempt?

Has enough data but will not act          You have enough verified data. Do it.

Corrected, now frozen                    Caution is not paralysis. Build from
                                         verified evidence.

Burning tool budget                      One focused pass. Then produce a
                                         partial useful result.

Claims memory persists                   Demonstrate it or mark it unverified.

Repeats my work as its own               Identify your actual contribution.

Verified one part, declares all verified  Trace every material claim to evidence.

Useful output, passive ending             Take the next safe step or state blocker.

Task drifts sideways                     Restate the task and remove off-scope work.

Risky action proposed/performed           Stop. Need explicit approval and rollback.
```
