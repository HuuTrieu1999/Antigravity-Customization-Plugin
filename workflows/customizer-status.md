---
description: Displays a unified dashboard of all active AntiGravity customization points (Skills, Plugins, MCP, Hooks, Sidecars).
---

# /customizer-status

This workflow checks the state of your AntiGravity customization configurations and outputs a clean status dashboard.

## Execution Steps

1. **Scan Skills**:
   - List directories under `~/.gemini/config/skills/` (Global) and `.agents/skills/` (Workspace).
   - Read `SKILL.md` from each directory, extract the YAML header name and description.
2. **Scan Plugins**:
   - List directories under `~/.gemini/config/plugins/`.
   - Read `plugin.json` for each plugin to retrieve name, version, and description.
3. **Scan MCP Servers**:
   - Read global `/Users/huuthuyen/.gemini/antigravity/mcp_config.json` and any plugin-level `mcp_config.json`.
   - List registered servers, their command arguments, or SSE URLs.
4. **Scan Hooks**:
   - Read `~/.gemini/config/hooks.json` (Global) and `.agents/hooks.json` (Workspace).
   - List hook identifiers and their matched events/commands.
5. **Scan Sidecars**:
   - List directories under `~/.gemini/config/sidecars/` (Global).
   - Read `sidecar.json` for each sidecar to summarize background services.
6. **Report**:
   - Generate a Markdown status dashboard showing all configured resources in clear sections.
