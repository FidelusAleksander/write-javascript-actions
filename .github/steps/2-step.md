## Step 2: Create Source Files & Run Locally

### 📖 Theory

Author the action’s core logic and verify it runs locally before bundling.

### ⌨️ Activity: Implement the Dad Jokes Action

Now that your project is initialized and dependencies are installed, it's time to create the source files for your Dad Jokes GitHub Action.


1. Create `src/` directory to hold your GitHub Action JavaScript files:

   ```sh
   mkdir src
   ```

1. Create `src/joke.js` file to hold the logic for fetching a joke from the `icanhazdadjoke.com` API:

   ```js
   const request = require("request-promise");

   const options = {
     method: "GET",
     uri: "https://icanhazdadjoke.com/",
     headers: {
       Accept: "application/json",
       "User-Agent": "Writing JavaScript action GitHub Skills exercise.",
     },
     json: true,
   };

   async function getJoke() {
     const res = await request(options);
     return res.joke;
   }

   module.exports = getJoke;
   ```

1. Create `src/main.js` that will be the main entry point for your action:

    ```js
    const getJoke = require("./joke");
    const core = require("@actions/core");

    async function run() {
      const joke = await getJoke();
      console.log(joke);
      core.setOutput("joke-output", joke);
    }

    run();
    ```

1. Run the action locally to verify it works:

   ```sh
   node src/main.js
   ```

   <!-- TODO: Add screenshot example -->

1. Commit and push:

   ```sh
   git add src/
   git commit -m "Add Dad Joke action source files"
   git push
   ```

### 🛠 Activity (Optional): Debug your action

>[!NOTE]
> This activity is optional and not required to complete the exercise.
>
> Learning how to debug your action code can be very helpful!

<details>
<summary>Show steps</summary><br/>

1. Install dev dependency:

   ```sh
   npm install -D @github/local-action
   ```

1. Create `.vscode/launch.json`:

   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "name": "Debug Action",
         "type": "node",
         "request": "launch",
         "runtimeExecutable": "npx",
         "cwd": "${workspaceRoot}",
         "args": ["@github/local-action", ".", "src/main.js"],
         "console": "integratedTerminal",
         "skipFiles": ["<node_internals>/**", "node_modules/**"]
       }
     ]
   }
   ```

1. Set breakpoints in `src/main.js` and start the "Debug Action" configuration.

</details>
