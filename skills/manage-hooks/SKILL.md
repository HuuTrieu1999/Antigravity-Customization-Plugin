---
name: manage-hooks
description: Manage Lifecycle Hooks (add, modify, or disable Pre/Post invocation and tool use hooks)
---

# Skill: manage-hooks

This skill instructs the agent on how to view, register, edit, and disable lifecycle hooks.

## 1. Config Locations
Hooks are defined in a `hooks.json` file in one of the following locations:
- **Global Hooks**: `~/.gemini/config/hooks.json`
- **Workspace Hooks**: `<workspace-root>/.agents/hooks.json`
- **Plugin Hooks**: `~/.gemini/config/plugins/<plugin-name>/hooks.json`

## 2. Event Types
Hooks can target specific events in the agent execution cycle:
- `PreInvocation`: Executed before the model receives the prompt.
- `PreToolUse`: Executed before a tool call runs.
- `PostToolUse`: Executed after a tool call completes.
- `PostInvocation`: Executed after all tool calls in an invocation complete.
- `Stop`: Executed when the agent execution loop terminates.

## 3. Configuration Format
Ensure the JSON format adheres to the target schema:
```json
{
  "hook-identifier": {
    "enabled": true,
    "<EventName>": [
      {
        "matcher": "regex_pattern_of_tool_name_or_*",
        "hooks": [
          {
            "type": "command",
            "command": "path/to/executable.sh --arg",
            "timeout": 10
          }
        ]
      }
    ]
  }
}
```

## 4. Editing and Safe Practices
1. Back up the target `hooks.json` before modifying.
2. Ensure you specify a valid `matcher` for `PreToolUse` and `PostToolUse` events (e.g., `run_command` or `replace_file_content`).
3. Verify that the command executed by the hook does NOT trigger the same hook event recursively, creating an infinite loop.
4. Save the file and validate JSON formatting.
