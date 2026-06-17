# AntiGravity Customization Standards

Always enforce these layout and safety guidelines when executing customizations:

## File Layouts
- Workspace files MUST prefer `.agents/` over legacy `.agent/` directories unless requested otherwise.
- Configuration JSONs must be pretty-printed with 2-space indentation.
- Always include YAML frontmatter in `SKILL.md` files.

## Safety & Verification
- Prior to editing `mcp_config.json`, validate the JSON syntax.
- Ensure sidecars have a defined `restart_policy`.
- Verify hook matching patterns to avoid infinite loops (e.g. a hook calling a command that triggers the same hook).
