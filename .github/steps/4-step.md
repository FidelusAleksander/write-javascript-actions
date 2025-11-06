<!--
  <<< Author notes: Step 4 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 4: Add Action Metadata (action.yml)

### 📖 Theory

Define the action’s interface (name, description, outputs, runtime, main entry) via `action.yml` pointing to the bundled file.

### ⌨️ Activity: Create Metadata File

1. Create `action.yml` at the repository root (same level as `package.json`).

   ```yaml
   name: "Joke Action"
   description: "Fetches a random joke and exposes it as an output"
   runs:
     using: node20
     main: dist/index.js
   outputs:
     joke:
       description: "The fetched joke text"
   ```

1. (Optional) Add future inputs section if you want to parameterize the API later.

1. Commit and push:

   ```sh
   git add action.yml
   git commit -m "Add action metadata referencing dist/index.js"
   git push
   ```

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** `action.yml` exists with `runs.main: dist/index.js` and `outputs.joke`.
