## Step 5: Create Workflow & Consume Output

Well done! :clap: You've created the Dad Jokes GitHub Action and defined its metadata.

Your action should be ready to use in any GitHub repository now!

### ⌨️ Activity: Author Workflow

Let's see your Dad Jokes action in action by creating a GitHub Actions workflow that uses it!

1. Create a new GitHub Actions workflow file with the following name

   ```txt
   .github/workflows/joke-action.yml
   ```

1. Add the following contents to the workflow file:

   ```yaml
   name: Joke Action
   on:
    issue_comment:
      types: [created]

   permissions:
    issues: write
    contents: read
  
   jobs:
     joke:
       if: startsWith(github.event.comment.body, '/joke')
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v5
         - name: Get Joke
           id: get-joke
           uses: ./
         - name: Create comment
           uses: peter-evans/create-or-update-comment@v5
           with:
            issue-number: {% raw %}${{ github.event.issue.number }}{% endraw %}
            body: {% raw %}${{ steps.get-joke.outputs.joke }}{% endraw %}
   ```

   This workflow triggers when someone comments `/joke` on an issue and responds with a joke!

1. Commit and push the workflow file to the `main` branch:

   ```sh
   git add .github/workflows/joke-action.yml
   git commit -m "Add workflow to test joke action"
   git push
   ```
