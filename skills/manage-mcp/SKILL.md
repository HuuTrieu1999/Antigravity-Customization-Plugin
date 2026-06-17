---
name: manage-mcp
description: Manage Model Context Protocol (MCP) servers (list, configure, validate, and troubleshoot)
---

# Skill: manage-mcp

This skill instructs the agent on how to manage, register, and troubleshoot MCP (Model Context Protocol) servers.

## 1. Config Locations
MCP servers are defined in a JSON file configuration:
- **Global Config**: `/Users/huuthuyen/.gemini/antigravity/mcp_config.json`
- **Plugin Config**: `mcp_config.json` located at the root of a plugin folder (e.g., `~/.gemini/config/plugins/<plugin-name>/mcp_config.json`).

## 2. Listing Configured MCP Servers
To inspect MCP server states:
1. Read the target `mcp_config.json` file.
2. Parse the `mcpServers` key.
3. List each server name, its executable/SSE details, parameters, and environment settings.

## 3. Registering/Updating an MCP Server
When a user asks to add or edit an MCP server:
1. Always create a backup of the original `mcp_config.json` file in a temporary folder or append `.bak` to a copy before making modifications.
2. Read the JSON content.
3. Modify the `mcpServers` block:
   - For **Stdio-based servers** (local node/python processes):
     ```json
     "mcpServers": {
       "server-name": {
         "command": "node",
         "args": ["/absolute/path/to/server.js"],
         "env": {
           "API_KEY": "value"
         }
       }
     }
     ```
   - For **SSE/Networked servers**:
     ```json
     "mcpServers": {
       "server-name": {
         "url": "http://localhost:3000/sse"
       }
     }
     ```
4. Save the file and execute a JSON validation checks. Do NOT write invalid JSON files to this path.
5. If the server fails to connect, inspect standard logs (often stored in the platform's diagnostic directory under `logs/`).
