# Patrick setup

Use this guide to connect Patrick and take a repository from first sign-in to a recorded receipt. Patrick is invite-only for now.

## Before you start

You need an approved invite (request one at https://buildwithpatrick.io), a GitHub account, and a repository you own.

## Steps

1. Install the plugin: `/plugin install patrick --marketplace ijaffrey/patrick-plugin`.
2. Connect the Patrick server when Claude asks, and sign in with GitHub. Approve the permissions shown on the consent screen. If you see a waiting message, your invite has not been approved yet.
3. Ask Claude to start a Patrick session. Patrick answers with the one step to take next.
4. Install Patrick's GitHub App on the repository you want it to work in, using the link Patrick gives you.
5. Tell Claude: `connect owner/name` (for example `connect acme/widgets`). Patrick connects the repository and runs a first audit.
6. Say `propose triage`. Patrick lists what is worth doing first, with a suggested scope for each.
7. When a brief is scored and ready, say `build <brief id>`. Patrick gives you a prompt to paste into Claude Code opened in a local clone of the repository. It works on a branch and opens a pull request.
8. Review and merge the pull request. Patrick records the receipt, with the merge commit and pull request number, in your own repository.

## Good to know

- Reading, auditing and planning work in chat. Building happens in Claude Code, in a local clone of your repository.
- Patrick never merges for you.
- Your backlog, handoffs and receipts live in your own repository.

## If something goes wrong

Tell Claude exactly what Patrick printed. Do not paste tokens or secrets into the chat.
