# Patrick

Patrick is a verification and reasoning layer for AI-run development work. It audits a repository, proposes what is worth doing first, and runs supervised sprints that end in a pull request you review and a receipt recorded in your own git history.

## Install

    /plugin install patrick --marketplace buildwithpatrick/patrick-plugin

## Setup

Patrick is invite-only for now. Request an invite at https://buildwithpatrick.io. Once approved, connect the Patrick server and sign in with GitHub when asked. Then install the Patrick GitHub App on the repository you want Patrick to work in and tell Claude: connect owner/name.

## What stays where

Your backlog, handoffs and receipts live in your own repository. This plugin contains only the skills and the server connection, with no tokens or secrets. /patrick-audit also reads your working tree with your own Claude; that read is not sent to Patrick.
