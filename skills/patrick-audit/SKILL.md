---
name: patrick-audit
description: Audit the current repository with Patrick and with your own read of the working tree, and report both. Use when the person asks for an audit, a health check, or what is worth fixing first.
---

# Patrick audit

This audit has two parts: Patrick's audit of the repository on GitHub, and a local read of the working tree done by your own Claude with its own tools. The local read is not sent to Patrick.

1. **Check the working directory.** Run `git rev-parse --show-toplevel`. If it fails, say the working directory is not a git repository (tell the person to clone their repository and start Claude Code inside it), skip the local read, and ask which repository to audit with Patrick (`owner/name`). If it succeeds, find the remote with `git remote get-url origin`.

2. **Local read, by your own Claude.** Use your own tools in the working tree:
   - List tracked files with `git ls-files`. Skip vendored folders (for example `node_modules`, `vendor`, `third_party`), lock files and binary files.
   - Read only what you need to report these four things:
     1. Possible hardcoded secrets, by file, line and kind (for example API key, password, private key). Give the file and line only; never print the value and never copy it into the reply. List matches in test or example files separately, as probable test data.
     2. Whether tests exist, and the command that runs them.
     3. Whether a CI configuration exists, and where.
     4. How to run the project, from the README or the manifest.
   - State how many files you read out of how many are tracked.

3. **Patrick's audit.** Find the repository's GitHub address from `git remote get-url origin`. Call Patrick's `audit_repo` tool (through Patrick's `execute` tool) with that address.

4. **Report in two clearly labelled sections:**
   - `Patrick's audit`: what the audit returned, in the person's terms: what it found, where, and how sure it is.
   - `Found by my own read of your working tree`: the four things from step 2 and the file count. Say that this part used your own Claude and is not sent to Patrick.
   - Name any place the two disagree (for example a secret one found and the other did not, or tests one saw and the other did not).
   - If either part is empty, partial or an error, say so plainly. Never write a summary from nothing.

5. **Finish safely.**
   - Never print a secret value. Tell the person to rotate anything real that was found.
   - If Patrick says the repository is not connected, tell the person to install Patrick's GitHub App on it and say `connect owner/name`.
   - Finish by offering the next step: say `propose triage`.
