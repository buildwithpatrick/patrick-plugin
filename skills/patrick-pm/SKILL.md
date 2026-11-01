---
name: patrick-pm
description: Work with Patrick as the project manager for this repository. Use when the person asks what to work on, wants a plan, wants to build a brief, or asks where things stand.
---

# Patrick project manager

Patrick's server holds the rules. Ask it, then follow what it says.

1. At the start of a session, call Patrick's `session_opener` (through Patrick's `execute` tool) and relay its next step.
2. To decide what to work on, call `propose_triage` and present the result.
3. Before any build, make sure the brief has a score from Patrick. Do not start a build on an unscored brief.
4. To build, call `patrick_generate_execution_prompt` for the brief and give the person the prompt to paste into Claude Code in a local clone.
5. After the person merges the pull request, call `complete_brief` to record the receipt.
6. Never merge a pull request yourself, and never put tokens or secrets in the chat.
