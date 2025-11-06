## Step 1: Initializing the Dad Jokes GitHub Action

Imagine you have a repetitive task that you want to automate. You've searched through the **GitHub Marketplace** to see if there are any existing actions that suit your needs, but found nothing - because your requirement is very specific: **generating DAD JOKES**! 🎭

Since no pre-built action exists for your quirky automation needs, it's time to roll up your sleeves and create your own

### 📖 Theory

The `@actions/core` package provides essential utilities for interacting with the GitHub Actions runtime, while `@actions/github` gives you access to GitHub's API and workflow context.

### ⌨️ Activity: Set up your development environment

1. Right-click the below button to open the **Create Codespace** page in a new tab. Use the default configuration.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Confirm the **Repository** field is your copy of the exercise, not the original, then click the green **Create Codespace** button.

   - ✅ Your copy: `/{{full_repo_name}}`
   - ❌ Original: `/skills-dev/write-javascript-actions`

1. Wait a moment for Visual Studio Code to load in your browser.

1. Verify that **Node.js** is available by opening a terminal and running:

   ```sh
   node --version
   npm --version
   ```

<details>
<summary>Having trouble? 🤷</summary><br/>

- Make sure you selected your personal copy of the repository, not the original template.
- If the Codespace fails to start, try refreshing the page and creating a new one.
- Node.js and npm should be pre-installed in the development environment.

</details>

### ⌨️ Activity: Initialize Project

1. Within your GitHub Codespace terminal window initialize a new project:

   ```sh
   npm init -y
   ```

1. Install the required dependencies:

   ```sh
   npm install request request-promise @actions/core @vercel/ncc
   ```

1. Update `.gitignore` to exclude `node_modules/`:

   ```sh
   echo "node_modules/" >> .gitignore
   ```

1. Review `package.json` to confirm dependencies are listed.

1. Commit and push your changes:

   ```sh
   git add .
   git commit -m "Initialize project and add core dependencies"
   git push
   ```

<details>
<summary>Having trouble? 🤷</summary><br/>

- Ensure you are at the repository root before running `npm init -y`.
- Do not commit `node_modules/` to the repository; ensure it's listed in `.gitignore`.

</details>
