## Step 4: Add Action Metadata

### 📖 Theory

Every GitHub Action requires an `action.yml` metadata file that defines the action's interface. This file tells GitHub:

- **What the action does**: Name and description for marketplace and workflows
- **How to run it**: Which runtime to use (`node24`) and entry point file (`dist/index.js`)
- **What it provides**: Output values that workflows can access
- **What it needs**: Input parameters (none in our case)

The `action.yml` file is like a contract between your action and the workflows that use it. It must be in the repository root and point to your bundled file.

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
