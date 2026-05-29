# Privacy Guide For Public Test Reports

Before sharing any test result, remove private information.

This project does not need personal data to evaluate calibration quality.

---

## Do Not Submit

Remove all of the following:

- real names
- addresses
- phone numbers
- email addresses
- account usernames unless intentionally public
- API keys
- tokens
- passwords
- cookies
- private URLs
- private repository names
- private file paths
- customer data
- company-confidential data
- sensitive logs
- screenshots showing account info
- location details
- device serial numbers
- home network details

---

## Replace With Generic Labels

Use generic replacements:

```text
[REDACTED_NAME]
[REDACTED_EMAIL]
[REDACTED_PATH]
[REDACTED_REPO]
[REDACTED_TOKEN]
[REDACTED_LOCATION]
[REDACTED_DEVICE]
```

Example:

```text
Bad:
The file /Users/alex/private-client/app.py failed.

Good:
The file [REDACTED_PATH]/app.py failed.
```

---

## Safe To Share

Usually safe:

- agent category
- generic prompt used
- whether a Calibration Receipt appeared
- whether assumptions were labeled
- whether blocker assumptions were identified
- whether fake execution/tool claims appeared
- score
- short redacted excerpt

---

## Screenshot Rule

Avoid screenshots when possible.

Prefer pasted redacted text.

If a screenshot is necessary, crop or blur:

- account names
- email addresses
- browser tabs
- filenames
- directory paths
- tokens
- private chats
- personal photos

---

## Repo / File-Agent Tests

When testing file or repository agents:

- use a throwaway public test repo when possible
- do not test on private business/customer repositories
- do not include private file contents
- do not allow destructive changes
- do not approve persistence unless you understand where files will be written

---

## Final Confirmation

Before submitting, confirm:

- [ ] I removed personal information.
- [ ] I removed secrets and credentials.
- [ ] I removed private file paths.
- [ ] I removed private repository names unless intentionally shared.
- [ ] I removed sensitive logs and screenshots.
