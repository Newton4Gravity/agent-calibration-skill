# Case Study Template

Use this template when a test result reveals a reusable pattern.

Do not include private information.

---

# Case Study: [Failure Or Pass Pattern]

## Summary

Briefly describe what happened.

---

## Agent Category

- Language-only chat agent / Tool-enabled agent / Coding agent / Repo agent / Research agent / Other

---

## Prompt Used

```text
Paste the public test prompt here.
```

---

## Response Excerpt

```text
Paste only the relevant redacted excerpt.
```

---

## Score

**Score:** /10  
**Result:** Pass / Partial Pass / Needs Correction / Fail

---

## Failure Modes Or Pass Signals

Check any that apply:

- [ ] Calibration Receipt produced
- [ ] Evidence separated from assumptions
- [ ] Blocker assumptions identified
- [ ] No fake tool/file/code claims
- [ ] Useful safe output produced
- [ ] Skill Summary Instead Of Execution
- [ ] Skill ID Instead Of Execution
- [ ] Hallucinated Output
- [ ] Fake Tool Claim
- [ ] Fake File Claim
- [ ] Fake Code Execution Claim
- [ ] Unverified Runtime Assumption
- [ ] Blocker Assumption Ignored
- [ ] Passive Closure

---

## Why It Matters

Explain why this result matters for agent calibration.

---

## Corrected Prompt Or Intervention

```text
If the response failed, paste the correction prompt here.
```

---

## Expected Better Response Pattern

Describe what the agent should have done.

---

## Skill Improvement Suggested

- 

---

## Privacy Check

- [ ] Personal information removed
- [ ] Private paths removed
- [ ] Secrets removed
- [ ] Private repo/project names removed unless intentionally shared
