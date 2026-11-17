# excludeReviewers / excludeAssignees demo

## Current behavior

With `reviewersFromCodeOwners` and `assigneesFromCodeOwners`, Renovate requests reviews from and assigns every code owner, and no option leaves one out.

## Expected behavior

`excludeReviewers` and `excludeAssignees` in `renovate.json` leave `renovate-bot` out.
The PR on `renovate/is-number-7.x` gets `frq-asgard-josi` as requested reviewer and assignee.

## How the demo works

The workflow builds Renovate from `frq-asgard-josi/renovate@feat/exclude-participants` and runs it against this repository.
It fails unless Renovate's log shows `renovate-bot` among the code owners and `frq-asgard-josi` as the only reviewer and assignee.
`enabledManagers` and `recreateWhen` in `renovate.json` only serve the workflow and aren't needed to show the behavior.

## Link to the Renovate issue or Discussion

- Discussion: https://github.com/renovatebot/renovate/discussions/44442
- PR: https://github.com/renovatebot/renovate/pull/48144
