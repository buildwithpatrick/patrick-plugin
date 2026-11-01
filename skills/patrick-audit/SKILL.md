---
name: patrick-audit
description: Audit the current repository with Patrick and report what it found. Use when the person asks for an audit, a health check, or what is worth fixing first.
---

# Patrick audit

1. Find the repository's GitHub address from `git remote get-url origin` in the working directory.
2. Call Patrick's `audit_repo` tool (through Patrick's `execute` tool) with that address.
3. Report what the audit returned, in the person's terms: what it found, where, and how sure it is.
4. If the result is empty, partial or an error, say so plainly. Never write a summary from nothing.
5. If Patrick says the repository is not connected, tell the person to install Patrick's GitHub App on it and say `connect owner/name`.
6. Finish by offering the next step: say `propose triage`.
