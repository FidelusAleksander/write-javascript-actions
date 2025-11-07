## Step 3: Bundle the Action

### 📖 Theory: Bundling the action

GitHub Actions written in JavaScript need to be bundled before they can be used. This is because:

1. **Dependencies**: Your action likely uses npm packages (like `@actions/core` and `request-promise`). GitHub Actions runners don't automatically install these dependencies.

2. **Single file requirement**: GitHub Actions expect a single JavaScript file as the entry point. Your source code is split across multiple files (`main.js`, `joke.js`).

3. **Performance**: A bundled file loads faster than multiple separate files with dependencies.

**What is `@vercel/ncc`?**

`ncc` (Node.js Compiler Collection) is a tool that:

- Bundles your Node.js project into a single file
- Includes all dependencies inline
- Optimizes the code for production
- Creates a `dist/index.js` file that contains everything needed to run your action

This bundled file is what GitHub Actions will actually execute when someone uses your action.

### ⌨️ Activity: Build Setup & Bundle

1. Add a build script to `package.json` (inside the existing scripts block or create one):

    ```json
    "scripts": {
      "build": "ncc build src/main.js -o dist"
    }
    
    ```

1. Run the build command. This should create a `dist/` directory with a bundled `index.js` file:

    ```sh
    npm run build
    ```

1. Commit and push the changes to the `main` branch:

   ```sh
   git add .
   git commit -m "Add ncc build script and bundled dist/index.js"
   git push
   ```
