## Step 3: Bundle the Action

### 📖 Theory

Bundle dependencies into a single optimized `dist/index.js` with `@vercel/ncc` so you never commit `node_modules`.

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



