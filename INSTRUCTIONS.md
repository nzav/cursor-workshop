# Mastering Cursor with a Next.js 15 Starter (Shadcn UI)

This workshop will guide you through using Cursor, an AI-powered code editor, to enhance your Next.js development workflow using the [Cursor Workshop](https://github.com/nzav/cursor-workshop) as our foundation.

**Prerequisites:**

- Basic understanding of Next.js concepts (components, pages, routing, API routes).
- Node.js and npm/yarn installed.
- Cursor IDE installed and basic familiarity with its interface.
- Clone the [Cursor Workshop](https://github.com/nzav/cursor-workshop) repository to your local machine.

## Section 1: Introduction to Cursor for Next.js Developers (15 minutes)

1. **Recap of Cursor's Key Features:**
   - Cursor is an AI-powered code editor built on top of VS Code. It provides intelligent code completion, refactoring, error detection, and a deep understanding of your project's context.
   - For Next.js development, this means it can assist with writing React components, handling routing, creating API endpoints, and more, often with just natural language instructions.
2. **Setting up the Next.js Project in Cursor:**
   - Open Cursor IDE.
   - Go to `File` > `Open Folder...` and navigate to the cloned `cursor-workshop` repository on your local machine. Click `Open`.
   - Allow Cursor to index the project files.
3. **Initial Exploration:**
   - In the Cursor Explorer (usually on the left sidebar), take a few moments to familiarize yourself with the project structure:
     - `src/app`: This directory contains your Next.js application routes.
     - `src/components`: This is where reusable React components are located.
     - `src/lib`: You might find utility functions or helper modules here.
     - `public`: Static assets like images are stored here.

## Section 2: Enhancing Next.js Development with AI Assistance (45 minutes) - Hands-on

1. **Component Generation with Inline Edits (Command/Ctrl + K):**
   - Open the `src/app/(delete-this-and-modify-page.tsx)/HomePage.tsx` file.
   - Below the existing content, place your cursor on a new line.
   - Press `Command + K` (macOS) or `Ctrl + K` (Windows/Linux) to open the inline edit window.
   - Type the following instruction: `Create a Next.js component called UserCard that accepts a 'name' (string) and 'email' (string) prop and displays them using Shadcn UI's Card component.`
   - Press `Enter`. Cursor will generate the component code.
   - Review the generated code. You'll likely see imports from the Shadcn UI components in the `@/registry` directory.
   - Now, within the `HomePage.tsx` file, import the `UserCard` component and use it to display some sample user data.
2. **Adding Features using Chat (Command/Ctrl + I):**
   - Note: The repository already contains a theme toggle in `src/components/mode-toggle.tsx`. Let's create a different feature.
   - Open the `src/app/(delete-this-and-modify-page.tsx)/HomePage.tsx` file again.
   - Press `Command + I` (macOS) or `Ctrl + I` (Windows/Linux) to open the chat window.
   - In the chat, type: `Add a simple notification counter to the HomePage that can increment when a button is clicked, using useState from React.`
   - Press `Enter`. Cursor will provide code suggestions in the chat.
   - Carefully review the suggested code, which will likely involve importing `useState` and adding a button with an `onClick` handler.
   - Click the `Apply` button (or similar) next to the suggested code block to integrate it into your `HomePage.tsx` file.
   - Test the functionality by running the Next.js development server (`npm run dev` or `yarn dev`) and opening the app in your browser.
3. **Generating API Routes with Composer (Command/Ctrl + Shift + I or Command/Ctrl + I for floating window):**
   - Create a new directory at `src/app/api/greeting`.
   - Inside the greeting directory, create a new file named `route.ts`.
   - Open the newly created `src/app/api/greeting/route.ts` file.
   - Press `Command + Shift + I` (macOS) or `Ctrl + Shift + I` (Windows/Linux) to open the Composer in full-screen mode (or `Command + I`/`Ctrl + I` for the floating window).
   - In the Composer, type: `Create a Next.js API route in /api/greeting that responds to a GET request with a JSON object containing a "message" key with the value "Hello from the API!".`
   - Select `TypeScript` as the language if prompted.
   - Press `Enter`. Cursor will generate the code for your API route.
   - Review the generated `route.ts` file. It should define an asynchronous `GET` function that returns a `NextResponse`.
   - Run your Next.js development server and navigate to `http://localhost:3000/api/greeting` in your browser to verify the API endpoint is working.
4. **Context-Aware Code Completion for Next.js:**
   - Open any component file in the `src/components` directory.
   - Start typing `<Link ` (note the space after `Link`). Observe how Cursor suggests the `Link` component from `next/link`. Press `Tab` to autocomplete.
   - Inside the `<Link>` component, start typing `href=`. Cursor should suggest string literals or relevant variables.
   - Try importing a component from the `@/registry` directory (which contains Shadcn UI components) and using one of its components (e.g., `<Button>`). Notice how Cursor suggests the available props for the `Button` component.
   - Experiment with typing common Next.js hooks like `useState` or `useEffect` and see how Cursor autocompletes the import statements and basic usage.
5. **Writing, Running, and Verifying Tests with Composer (Agentic Mode):**
   - Create a new file in the `src/components` directory named `UserCard.tsx` (based on the component we created earlier).
   - Press `Command + Shift + I` (macOS) or `Ctrl + Shift + I` (Windows/Linux) to open the Composer in full-screen mode.
   - In the Composer, type the following instruction: `Write a unit test for the UserCard component using Jest and React Testing Library. The test should verify that the component renders the name and email props correctly.`
   - Enable Agentic Mode in the Composer. You might see a toggle or option to enable the agent. This allows Cursor to not only write the code but also attempt to run and verify it.
   - Press `Enter`. Cursor will attempt to:
     - Create a new test file (likely in a `__tests__` directory or a similarly named location).
     - Write the necessary test code using Jest and React Testing Library.
     - Attempt to run the test(s). You might see output in the Composer or a dedicated terminal window within Cursor.
     - Provide feedback on whether the test passed or failed.
   - Review the generated test file and the test results.
   - **Iteration (Optional):** If the test fails or doesn't cover everything you want, you can provide further instructions to the Composer. For example: `The test should also check if the email address is rendered with a specific class name.` Cursor will then attempt to modify the test code and re-run it.
   - **Alternative Approach (If Agentic Mode doesn't automatically run):**
     - After Cursor generates the test file, open the integrated terminal in Cursor (`Terminal` > `New Terminal`).
     - Navigate to the directory containing the test file (e.g., `__tests__`).
     - Run the test command for your project (usually `npm test` or `yarn test`).
     - Once the tests have run, go back to the Composer and ask: `Verify if the test for the UserCard component passed and if it correctly checks for name and email rendering.` Cursor can then analyze the terminal output to confirm the test results.

## Section 3: Enforcing Next.js Coding Standards with Rules (30 minutes) - Hands-on

1. **Creating a Project Rule for Consistent Component Naming:**

   - In your project root, navigate to the `.cursor` directory. If it doesn't exist, create it. Inside `.cursor`, create another directory named `rules`.
   - Inside the `rules` directory, create a new file named `component-naming.mdc`.
   - Open `component-naming.mdc` and add the following content:

   ```markdown
   ---
   description: Enforce that all component filenames in the 'src/components' directory start with an uppercase letter.
   globs:
     - src/components/*.tsx
     - src/components/*.jsx
   ---

   USE WHEN creating a new file or modifying an existing file in the `src/components` directory:

   ENSURE that the filename starts with an uppercase letter.
   ```

   - Save the file. Cursor might take a moment to index the new rule.
   - **Testing the Rule:** Try creating a new component file in the `src/components` directory with a lowercase name (e.g., `mybutton.tsx`). Observe if Cursor highlights this as a potential issue (this might depend on your Cursor settings and the model being used).

2. **Implementing a Rule for Preventing Direct CSS Imports in Components:**

   - Create a new file in the `.cursor/rules` directory named `no-direct-css.mdc`.
   - Open `no-direct-css.mdc` and add the following content:

   ```markdown
   ---
   description: Discourage direct CSS imports in components. Prefer using CSS Modules or Tailwind CSS.
   globs:
     - src/components/*.tsx
     - src/components/*.jsx
     - src/app/**/*.tsx
     - src/app/**/*.jsx
   ---

   USE WHEN adding or modifying import statements in a `.tsx` or `.jsx` file within the `src/components` or `src/app` directories:

   AVOID importing CSS files directly (e.g., `import './styles.css';`).

   CONSIDER using CSS Modules (`import styles from './styles.module.css';`) or Tailwind CSS classes instead.
   ```

   - Save the file.
   - **Testing the Rule:** In one of your component files, try adding a direct CSS import (if you don't have one already). Observe if Cursor flags this based on your defined rule.

3. **Exploring Rule Activation:** Discuss how the `description` and `globs` parameters in the rule files control when a rule is considered and potentially applied by Cursor's AI.

## Section 4: Integrating with Next.js Ecosystem using MCP (Model Context Protocol) (20 minutes)

1. **Brainstorming MCP Use Cases for Next.js:**
   - Discuss how MCP could enable deeper integrations for Next.js development:
     - **Integration with Storybook:** An MCP server could provide information about available components in your Storybook setup, allowing Cursor to suggest and use them correctly.
     - **Backend API Schema Awareness:** If you have an OpenAPI or GraphQL schema for your backend API, an MCP server could provide this context to Cursor, enabling more accurate code completion and type checking when fetching data.
     - **Deployment Tooling Integration:** An MCP server could allow Cursor to trigger deployments or check the status of your Next.js application on platforms like Vercel or Netlify.
2. **Exploring Potential MCP Integrations (Conceptual):**
   - Explain that creating MCP servers involves defining tools (functions) that Cursor can call. These tools can interact with external systems or data sources.
   - For example, a "Get Available Components" tool in a Storybook MCP server might fetch a list of component names and their props.
   - Mention that MCP servers can be written in any language and communicate with Cursor via standard input/output or HTTP. ([Model Context Protocol - Cursor](https://docs.cursor.com/context/model-context-protocol))
3. **Configuration (Recap):**
   - Remind participants that MCP servers are configured in Cursor's settings under the "Features" > "MCP" section. They can add new MCP servers by providing a name and either a command to run a local server or the URL of a remote server.

## Section 5: Q&A and Wrap-up (10 minutes)

- Open the floor for any questions participants have about using Cursor with Next.js or any of the topics covered in the workshop.
- Summarize the key benefits of using Cursor to enhance Next.js development productivity.
- Encourage the team to continue exploring Cursor's features and experiment with creating their own Rules and potentially exploring MCP integrations relevant to their specific workflows.
