<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 2: Create Source Files & Run Locally

### 📖 Theory

Author the action’s core logic and verify it runs locally before bundling.

### ⌨️ Activity: Implement Source

1. In the repository root, create `src/joke.js`:

   ```js
   // src/joke.js
   export async function fetchJoke() {
     const res = await fetch("https://official-joke-api.appspot.com/random_joke");
     if (!res.ok) throw new Error(`Failed to get joke: ${res.status}`);
     const data = await res.json();
     return `${data.setup} ${data.punchline}`;
   }
   ```

1. Create `src/main.js`:

   ```js
   // src/main.js
   import * as core from "@actions/core";
   import { fetchJoke } from "./joke.js";

   async function run() {
     try {
       const joke = await fetchJoke();
       core.setOutput("joke", joke);
       console.log("Joke:", joke);
     } catch (err) {
       core.setFailed(err.message);
     }
   }
   run();
   ```

1. Run locally to verify:

   ```sh
   node src/main.js
   ```

1. Commit and push:

   ```sh
   git add src/joke.js src/main.js
   git commit -m "Add joke source and main entry"
   git push
   ```

### 🛠 Activity (Optional): Add Debugging Support

1. Install dev dependency:

   ```sh
   npm install -D @github/local-action
   ```

1. Create `.vscode/launch.json`:

   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "name": "Debug Action",
         "type": "node",
         "request": "launch",
         "runtimeExecutable": "npx",
         "cwd": "${workspaceRoot}",
         "args": ["@github/local-action", ".", "src/main.js"],
         "console": "integratedTerminal",
         "skipFiles": ["<node_internals>/**", "node_modules/**"]
       }
     ]
   }
   ```

1. Set breakpoints in `src/main.js` and start the "Debug Action" configuration.

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** `src/main.js` & `src/joke.js` exist.
