# Patrick setup

Use this guide to connect Patrick and take a repository from first sign-in to a recorded receipt. Patrick is invite-only for now.

## Before you start

You need an approved invite (request one at https://buildwithpatrick.io), a GitHub account, a repository you own, and Claude Code version 2.1.275 or later (check with `claude --version`).

Clone the repository to your computer and start Claude Code from inside that folder (`git clone https://github.com/owner/name`, then `cd name`, then `claude`). Auditing and building both read and work in that folder.

## Steps

1. Install the plugin: `/plugin install patrick --marketplace buildwithpatrick/patrick-plugin`.
   If Claude asks where to install it, choose the first option.
2. Connect the Patrick server when Claude asks, and sign in with GitHub. Approve the permissions shown on the consent screen. If you see a waiting message, your invite has not been approved yet.
3. Ask Claude to start a Patrick session. Patrick answers with the one step to take next.
4. Install Patrick's GitHub App on the repository you want it to work in, using the link Patrick gives you. On GitHub's install page choose Only select repositories and pick that one repository (the page may default to All repositories).
5. Tell Claude: `connect owner/name` (for example `connect acme/widgets`). Patrick connects the repository and gives a first read: what it found, how many files it scanned for secrets, and what is worth doing first.
6. Say `draft my first briefs`. Patrick writes up to three briefs, scores each, and opens them as pull requests for you to review and merge. The drafting runs in your own Claude Code, in a local clone of the repository.
7. Then say `build <brief id>`. Patrick gives you a prompt to paste into a new Claude Code session, started in a local clone of the repository. It works on a branch and opens a pull request.
8. Review and merge the pull request. Patrick records the receipt, with the merge commit and pull request number, in your own repository.

## Good to know

- Reading, auditing and planning work in chat. Building happens in Claude Code, in a local clone of your repository.
- Patrick never merges your work. After you merge, it opens and merges one small record pull request in your repository that moves the brief to shipped.
- Your backlog, handoffs and receipts live in your own repository.
- Questions Claude Code asks on its first run (screen layout, browser extension) are from Claude Code, not Patrick; answer as you like.
- You can also say propose triage to see a ranked list without drafting.

## If something goes wrong

If Patrick shows as disconnected, run `/mcp`, choose patrick, reconnect, then retry what you were doing.

Otherwise, tell Claude exactly what Patrick printed. Do not paste tokens or secrets into the chat.
