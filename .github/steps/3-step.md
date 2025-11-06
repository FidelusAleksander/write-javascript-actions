<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 3: Bundle the Action

### 📖 Theory

Bundle dependencies into a single optimized `dist/index.js` with `@vercel/ncc` so you never commit `node_modules`.

### ⌨️ Activity: Build Setup & Bundle

1. Add a build script to `package.json` (inside the existing scripts block or create one):

```json
{
  "scripts": {
    "build": "ncc build src/main.js -o dist"
  }
}
```

If you already have other scripts, just add the build entry.

1. Run the build:

```sh
npm run build
```

1. Inspect the generated file:

```sh
ls dist
head -n 20 dist/index.js
```

1. Commit only source + `dist/` (no `node_modules/`):

```sh
git add package.json dist/index.js
git commit -m "Add ncc build script and bundled dist/index.js"
git push
```

1. (Optional) Rebuild after changes:

```sh
npm run build
```

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** `package.json` contains `ncc build src/main.js -o dist`; `dist/index.js` exists; `node_modules/` not committed.
