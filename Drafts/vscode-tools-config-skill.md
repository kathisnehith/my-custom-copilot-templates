# VS Code Agent Tools Skill

This document provides a comprehensive reference of all available tools for the VS Code Agent. It outlines the categorizations, specific sub-tools, and their precise descriptions to guide agentic workflows, workspace manipulation, and browser interactions.

| Tool (Description) | Sub Tool | Exact Description |
| :--- | :--- | :--- |
| **agent** (Delegate tasks to other agents) | `runSubagent` | Run a task within an isolated subagent context to enable efficient organization of task and context window managment |
| **browser** (Open and interact with integrated browser pages) | `clickElement` | Click an element in a browser page |
| | `dragElement` | Drag an element over another element |
| | `handleDialog` | Respond to a dialog in a browser page |
| | `hoverElement` | Hover over an element in a browser page |
| | `navigatePage` | Navigate or reload a browser page |
| | `MapsPage` | Navigate or reload a browser page |
| | `openBrowserPage` | Open a URL in the integrated browser |
| | `readPage` | Read the content of a browser page |
| | `runPlaywrightCode` | Run a Playwright code snippet against a browser page |
| | `screenshotPage` | Capture a screenshot of a browser page |
| | `typeInPage` | Type text or press keys in a browser page |
| **edit** (Edit files in your workspace) | `createDirectory` | Create new directories in your workspace |
| | `createFile` | Create new files |
| | `createJupyterNotebook` | Create a new Jupyter Notebook |
| | `editFiles` | Edit files |
| | `editNotebook` | Edit a notebook file in the workspace |
| | `rename` | Rename a symbol across the workspace |
| **execute** (Execute code and applications on your machine) | `createAndRunTask` | Create and run a task in the workspace |
| | `getTerminalOutput` | Get output from an active terminal execution (identified by the "id" retruned by runInTerminal |
| | `killTerminal` | Kill a terminal by its ID. Use this to clean up terminals that are no longer needed |
| | `runInTerminal` | Run commands in the terminal |
| | `runNotebookCell` | Trigger the execution of a cell in a notebook file |
| | `sendToTerminal` | Send input text to an active terminal execution (identified by the "id" r.etruned by runinterminal |
| **read** (Read files in your workspace) | `getNotebookSummary` | This is a tool returns the list of the Notebook cells along with their IDs, types, line ranges, language, execution info & output types. |
| | `problems` | Check errors for a particular file |
| | `readFile` | Read the contents of a file |
| | `readNotebookCellOutput` | Read the output of a previously executed cell |
| | `terminalLastCommand` | Get the last command run in the active terminal. |
| | `terminalSelection` | Get the current selection in the active terminal. |
| | `viewImage` | View the contents of an image file |
| **search** (Search files in your workspace) | `changes` | Get diffs of changed files |
| | `codebase` | Find relevant file chunks, symbols, and other information via semantic search |
| | `fileSearch` | Find files by name using a glob pattern |
| | `listDirectory` | List the contents of a directory |
| | `textSearch` | Search for text in files by regular expression |
| | `usages` | Find references, definitions, and implementations of a symbol |
| **todo** (Manage and track todo items for task planning) | `(none)` | `(none)` |
| **vscode** (Use VS Code features) | `askQuestions` | Ask structured clarifying questions using single select, multi-select, or Freeform inputs to collect requirements before proceeding |
| | `extensions` | Search for VS Code extensions |
| | `getProjectSetupInfo` | Do not call this tool without first calling the tool to create a Workspace provides project set up for school workspace based on type and programming language... |
| | `installExtension` | Install an extension in VS Code. Use this tool to install an extension in vs code As part of new workspace creation process only |
| | `memory` | Manage persistent memory across conversations |
| | `newWorkspace` | Scaffold a new workspace in VS Code |
| | `resolveMemoryFileUri` | Resolve a memory file path to its actual Uri |
| | `runCommand` | Run a command in VS Code. Use this tool to run a command in Visual Studio code, as part of new workspace creation process only |
| | `vscodeAPI` | Use VS Code API references to answer questions about VS Code extension development |
| **web** (Fetch information from the web) | `fetch` | Fetch the main content from a web page. You should include the URL of the page you wanted to fetch |
| | `githubRepo` | Semantic search a GitHub repository for relevant source code snippets. You can specify a repo using owner/repo |
| | `githubTextSearch` | Text search a GitHub repository or organization for files containing specfic keyword or code patterns |



- How to use in <>.agent.md
To empower your agent, reference this skill context in the setup or system prompt section of your custom .agent.md file. This instructs the agent on when and how to invoke these tools.

example of .agent.md format used these tools by paramenter tools in list form

example-tools: ['vscode', 'execute', 'read','search', 'web', 'agent', 'todo']