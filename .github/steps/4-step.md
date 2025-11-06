## Step 4: Add Action Metadata (action.yml)

### 📖 Theory

Define the action’s interface (name, description, outputs, runtime, main entry) via `action.yml` pointing to the bundled file.

### ⌨️ Activity: Create Metadata File

1. Create `action.yml` at the repository root (same level as `package.json`).

    ```yaml
    name: "Joke Action"
    description: "Fetches a random joke and exposes it as an output"

    outputs:
      joke:
        description: "The fetched joke text"

    runs:
      using: node24
      main: dist/index.js
    ```


1. Commit and push:

   ```sh
   git add action.yml
   git commit -m "Add action metadata referencing dist/index.js"
   git push
   ```
