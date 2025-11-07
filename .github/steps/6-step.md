## Step 6: Trigger & Validate

### 📖 Theory

Now it's time to test your custom GitHub Action! Your workflow is configured to:

1. **Trigger**: Listen for issue comments that start with `/joke`
2. **Execute**: Run your Dad Jokes action using the local action (`uses: ./`)
3. **Output**: Post the retrieved joke as a new comment in the same issue

When you comment `/joke`, GitHub will:

- Trigger the "Joke Action" workflow
- Check out your repository code
- Run your bundled action (`dist/index.js`)
- Your action will fetch a random dad joke from the API
- The workflow will create a new comment with the joke

### ⌨️ Activity: Try out your action

1. Create a comment in this issue (or create a new one) with the text `/joke`

1. Monitor the **Actions** tab for the "Joke Action" workflow run to complete:
   - Click on the **Actions** tab in your repository
   - Look for a new workflow run titled "Joke Action"
   - The run should show a green checkmark when completed successfully

1. Return to the issue and refresh the page. You should see a new comment posted by `github-actions[bot]` containing a random dad joke!

   **Example output:**

   ```text
   What do you call a bear with no teeth? A gummy bear!
   ```

   <details>
   <summary>Troubleshooting 🛠️</summary><br/>

   If the workflow doesn't trigger or fails:
   - Make sure your comment starts exactly with `/joke`
   - Check the Actions tab for error messages
   - Verify that your `dist/index.js` file exists and was committed
   - Ensure your `action.yml` file is correctly formatted

   </details>
