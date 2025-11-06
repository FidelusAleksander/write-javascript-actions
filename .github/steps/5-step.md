## Step 5: Create Workflow & Consume Output

### 📖 Theory

Use a workflow triggered by `issue_comment` to run the local action and then post the retrieved joke as a comment.

### ⌨️ Activity: Author Workflow

1. Create `.github/workflows/joke-action.yml`.

   ```yaml
   name: Joke Action
   on:
     issue_comment:
       types: [created]
   jobs:
     joke:
       if: ${{ !github.event.repository.is_template }}
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v5
         - name: Get Joke
           id: get_joke
           uses: ./
         - name: Post Joke Comment
           uses: actions/github-script@v7
           with:
             script: |
               const joke = core.getInput('joke') || process.env['JOKE'] || '${{ steps.get_joke.outputs.joke }}';
               const body = `Here is a joke: ${joke}`;
               await github.rest.issues.createComment({
                 owner: context.repo.owner,
                 repo: context.repo.repo,
                 issue_number: context.issue.number,
                 body
               });
   ```

1. Commit and push the workflow:

   ```sh
   git add .github/workflows/joke-action.yml
   git commit -m "Add joke-action workflow consuming output"
   git push
   ```

### 🔍 Activity: Validate Output Wiring

1. Confirm output reference syntax: `${{ steps.get_joke.outputs.joke }}` appears in the workflow.
1. (Optional) Add a log step before posting:

   ```yaml
   - name: Log Joke
     run: echo "Joke => ${{ steps.get_joke.outputs.joke }}"
   ```

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** Workflow file exists with `on: issue_comment` and a step referencing `${{ steps.get_joke.outputs.joke }}`.
