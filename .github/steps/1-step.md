<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
-->

## Step 1: Initialize Project & Install Dependencies

### 📖 Theory

Set up a modern root-level JavaScript action project and install required runtime and build dependencies without committing `node_modules`.

### ⌨️ Activity: Initialize Project

1. Open a terminal and clone your exercise repository locally.
1. Switch to the `main` branch if not already: `git switch main`.
1. At the repository root (not inside `.github/actions/`), initialize a new project:

```sh
npm init -y
```

1. Install action runtime & build dependencies:

```sh
npm install @actions/core @actions/github @vercel/ncc
```

1. (Optional) Plan for local debugging later; you will add `@github/local-action` in Step 2.

1. Create a `src/` directory (leave it empty this step):

```sh
mkdir src
```

1. Add or update `.gitignore` to exclude `node_modules/`:

```sh
echo "node_modules/" >> .gitignore
```

1. Review `package.json` to confirm dependencies are listed (do not create `action.yml` yet).

1. Commit and push your changes:

```sh
git add .
git commit -m "Initialize project and add core dependencies"
git push
```

<details>
<summary>Having trouble? 🤷</summary><br/>

- Ensure you are at the root of the repository before running `npm init -y`.
- If `git switch main` fails, use `git checkout main` (older Git versions).
- Run `npm -v` to verify Node.js tooling is installed.

</details>
