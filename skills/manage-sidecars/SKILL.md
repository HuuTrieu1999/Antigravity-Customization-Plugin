---
name: manage-sidecars
description: Manage Sidecars (configure, register, and monitor background processes and services)
---

# Skill: manage-sidecars

This skill instructs the agent on how to list, view, scaffold, and configure background sidecar processes.

## 1. Directory Structure
A sidecar is an independent folder containing a configuration and target execution script. It lives in:
- **Global Scope**: `~/.gemini/config/sidecars/<sidecar-name>/`
- **Plugin Scope**: `~/.gemini/config/plugins/<plugin-name>/sidecars/<sidecar-name>/`

The folder name serves as both the sidecar's unique ID and its current working directory (Cwd).

## 2. Config File Schema (`sidecar.json`)
Every sidecar directory must contain a `sidecar.json` file. Ensure compliance with the schema:
```json
{
  "description": "Short human-readable description of the background process",
  "command": "python3",
  "args": ["main.py"],
  "restart_policy": "always",
  "env": {
    "ENV_VAR_KEY": "value"
  }
}
```
*Note:* The `command` field is mutually exclusive with `builtin` (which currently supports `schedule`).

## 3. Scaffolding a Sidecar
To create and register a new sidecar:
1. Create a directory named after the sidecar inside the appropriate scope directory.
2. Write the execution script (e.g., `main.py`, `script.sh`) inside that directory.
3. If it is a shell script, make sure to make it executable using `chmod +x <script>`.
4. Create the `sidecar.json` configuration file, pointing `command` and `args` to the script.
5. Reload the agent or verify that the sidecar starts running in the background.
