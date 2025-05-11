# Using Code Runner to Run JavaScript and TypeScript in VS Code

This guide explains how to configure and use the **Code Runner** extension in Visual Studio Code to run JavaScript (`.js`) and TypeScript (`.ts`) files.

---

## Prerequisites

1. **Install Node.js**  
   Ensure you have Node.js installed on your system. You can download it from [Node.js Official Website](https://nodejs.org/).

2. **Install Code Runner Extension**  
   Install the **Code Runner** extension in VS Code:
   - Open VS Code.
   - Go to the Extensions view (`Ctrl+Shift+X` or `Cmd+Shift+X` on macOS).
   - Search for "Code Runner" and click **Install**.

3. **Install `ts-node` and `@swc/core`** (for TypeScript)  
   Run the following commands in your terminal to install `ts-node` and `@swc/core` globally:

   ```bash
   npm install -g ts-node @swc/core
   ```

---

## Configuration

### Real TypeScript Configuration for Code Runner

To run TypeScript files using Code Runner, add the following configuration to your workspace's `.vscode/settings.json` file:

```jsonc
{
    "code-runner.executorMap": {
        "javascript": "node",
        "typescript": "ts-node --swc"
    },
    "code-runner.saveFileBeforeRun": true,
    "code-runner.clearPreviousOutput": true,
    "code-runner.showExecutionMessage": false
}
```

This configuration ensures that Code Runner uses `node` to execute JavaScript files and `ts-node` with the `--swc` flag to compile and execute TypeScript files.

---

## Running Files with Code Runner

### 1. Run a JavaScript File
- Open a `.js` file in VS Code.
- Press **Ctrl+Alt+N** (or **Cmd+Option+N** on macOS) to run the file using Code Runner.
- The output will appear in the **Output** panel.

### 2. Run a TypeScript File
- Open a `.ts` file in VS Code.
- Press **Ctrl+Alt+N** (or **Cmd+Option+N** on macOS) to run the file using Code Runner.
- The output will appear in the **Output** panel.

---

## Running Files Manually

### 1. Run a JavaScript File
You can also run JavaScript files manually in the terminal using Node.js:

```bash
node path/to/file.js
```

For example, if your file is located at `vanilla-js/index.js`, run:

```bash
node vanilla-js/index.js
```

### 2. Run a TypeScript File
You can also run TypeScript files manually in the terminal using `ts-node`:

```bash
ts-node --swc path/to/file.ts
```

For example, if your file is located at `vanilla-ts/index.ts`, run:

```bash
ts-node --swc vanilla-ts/index.ts
```

---

## Troubleshooting

1. **No Output in the Output Panel**  
   Ensure you are checking the **Output** panel (not the terminal). To open it:
   - Go to **View > Output**.
   - In the dropdown at the top-right of the Output panel, select **Code**.

2. **Experimental Warning for TypeScript**  
   If you see `ExperimentalWarning: Type Stripping is an experimental feature`, ensure you have installed `@swc/core` globally:

   ```bash
   npm install -g @swc/core
   ```

3. **Error: `ts-node` Not Found**  
   Ensure `ts-node` is installed globally:

   ```bash
   npm install -g ts-node
   ```

4. **Run with Node's Warning Suppression**  
   If warnings persist, you can suppress them by running the file manually with:

   ```bash
   ts-node --swc index.ts
   ```

---

## Additional Resources

- [Node.js Official Website](https://nodejs.org/)
- [Code Runner Extension](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner)
- [ts-node Documentation](https://typestrong.org/ts-node/)

---