# excludeReviewers / excludeAssignees demo

This repository runs Renovate from `frq-asgard-josi/renovate@feat/exclude-participants` against itself.
`.github/CODEOWNERS` names `@frq-asgard-josi` and `@renovate-bot`, and `renovate.json` excludes `renovate-bot` as reviewer and assignee.
The workflow opens a PR on `renovate/is-number-7.x` with `frq-asgard-josi` as requested reviewer and assignee.
It fails unless Renovate's log shows `renovate-bot` among the code owners and `frq-asgard-josi` as the only reviewer and assignee.

## Setup

1. Push `feat/exclude-participants` to `frq-asgard-josi/renovate`.
2. Create the repository from this directory:

   ```sh
   gh repo create frq-asgard-josi/renovate-exclude-participants-demo --public --source . --remote origin
   ```

3. Allow GitHub Actions to create pull requests:

   ```sh
   gh api -X PUT 'repos/{owner}/{repo}/actions/permissions/workflow' -f default_workflow_permissions=read -F can_approve_pull_request_reviews=true
   ```

4. Push, which starts the first run:

   ```sh
   git push -u origin main
   ```

## Re-run

Start the workflow with "Run workflow" in the Actions tab, optionally with another Renovate repository or ref.
Each run closes the previous demo PR and deletes its branch first.
