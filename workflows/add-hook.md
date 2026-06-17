---
description: Step-by-step wizard to register a new tool lifecycle hook in hooks.json.
---

# /add-hook

This workflow provides an interactive wizard to configure a lifecycle hook.

## Execution Steps

1. **Information Gathering**:
   - Ask the user for the **Hook Identifier** (e.g., `linter-after-save`).
   - Ask the user for the **Target Event** (choose from: `PreInvocation`, `PreToolUse`, `PostToolUse`, `PostInvocation`, `Stop`).
   - Ask the user for the **Tool Matcher** (e.g., `run_command`, `replace_file_content`, or `*` to match all tools).
   - Ask the user for the **Command / Script** to execute when the hook triggers.
   - Ask the user for the **Timeout** in seconds (defaults to 10).
2. **Apply Cfg**:
   - Locate the target `hooks.json` (defaults to `.agents/hooks.json` in current workspace, or `~/.gemini/config/hooks.json` if requested globally).
   - Read the existing file or initialize an empty JSON `{}` if it does not exist.
   - Append the hook entry:
     ```json
     {
       "<HookIdentifier>": {
         "enabled": true,
         "<TargetEvent>": [
           {
             "matcher": "<ToolMatcher>",
             "hooks": [
               {
                 "type": "command",
                 "command": "<Command>",
                 "timeout": <Timeout>
               }
             ]
           }
         ]
       }
     }
     ```
3. **Verify and Save**:
   - Save the file and execute a JSON syntax validation check.
   - Print a success message showing the active hook details.
