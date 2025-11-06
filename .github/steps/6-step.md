<!--
  <<< Author notes: Step 6 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 6: Trigger & Validate

### 📖 Theory

Trigger the joke workflow with an issue comment and let this step confirm the previous run completed successfully.

### ⌨️ Activity: Execute & Review

1. Open (or create) an issue.
1. Add a new comment to trigger `joke-action.yml`.
1. After it completes, view the run details to see the posted joke comment.
1. This step’s workflow will automatically pick up the completed run via `workflow_run`.

### Transition

- **Actions Trigger:** [`workflow_run`](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#workflow_run)
- **Grading-Check:** Previous "Joke Action" workflow run concluded with `success`.
