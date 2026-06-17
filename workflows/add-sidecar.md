---
description: Scaffolds a new background sidecar configuration and execution script.
---

# /add-sidecar

This workflow scaffolds a new background sidecar daemon.

## Execution Steps

1. **Information Gathering**:
   - Ask the user for the **Sidecar ID/Name** (e.g., `heartbeat-daemon`).
   - Ask the user for the **Executable Command** (e.g., `python3` or `node`).
   - Ask the user for the **Target Script** (e.g., `main.py` or `index.js`).
2. **Scaffold Files**:
   - Create the sidecar folder: `~/.gemini/config/sidecars/<SidecarName>/`.
   - Write a starter script template inside that folder (e.g., a simple loop writing to a log file or performing a heartbeat).
   - Write the `sidecar.json` configuration file:
     ```json
     {
       "description": "Background daemon for <SidecarName>",
       "command": "<ExecutableCommand>",
       "args": ["<TargetScript>"],
       "restart_policy": "always",
       "env": {}
     }
     ```
3. **Verify**:
   - Present the created directory structure to the user.
   - Explain how the user can customize the execution script and how Antigravity handles the process lifecycle automatically.
