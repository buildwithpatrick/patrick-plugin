---
name: patrick-pm
description: Work with Patrick as the project manager for this repository. Use when the person asks what to work on, wants a plan, wants to draft or build a brief, or asks where things stand.
---

# Patrick project manager

Patrick's server holds the rules. Ask it, then follow what it says.

1. At the start of a session, call Patrick's `session_opener` (through Patrick's `execute` tool) and relay its next step.
2. When the person connects a repository, call `connect_repo`. If the result has a `first_read`, tell the person what it says before anything else, in its own words and order. Then offer the next step it gives.
3. When the person says "draft my first briefs", call `propose_triage` with `draft_top=3` and follow the prompt it returns. It tells you to write each brief, score it with Patrick's `score_brief` (brief text mode), improve it until it passes, and deliver all of them as one pull request. For a single item, call `propose_triage` with `draft_item=<number>`.
4. To decide what to work on without drafting, call `propose_triage` and present the result.
5. Before any build, make sure the brief has a score from Patrick. Do not start a build on an unscored brief.
6. To build, call `patrick_generate_execution_prompt` for the brief and give the person the prompt to paste into a new Claude Code session started in a local clone.
7. After the person merges the pull request, call `complete_brief` to record the receipt.
8. Never merge a pull request yourself, never show a secret value even if one appears in a file, and never put tokens or secrets in the chat.
