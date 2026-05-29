# Example: Claude Code / Coding Agent

Put this in a repo-level instruction file or session prompt:

```text
Before modifying code:
- Inspect the relevant files first.
- Do not invent APIs, file paths, imports, tests, or command output.
- Label unverified assumptions in comments or the response.
- Use one focused verification pass, then produce a patch.
- Do not claim tests passed unless tests were actually run and output is shown or summarized.
- High-impact changes require a reversible plan and explicit approval.
```
