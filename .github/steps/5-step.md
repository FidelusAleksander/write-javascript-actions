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
            issue-number: ${{ github.event.issue.number }}
            body: ${{ steps.get-joke.outputs.joke }}
            
   ```

   The workflow will run on every issue comment created event. If the comment starts with `/joke`, it will execute the Dad Jokes action and post the joke as a comment in the same issue.

1. Commit and push the workflow file to the `main`:
