---
name: manage-plugins
description: Manage AntiGravity Plugins (inventory, import, and install plugin packages)
---

# Skill: manage-plugins

This skill instructs the agent on how to list, view, configure, and install AntiGravity Plugins.

## 1. Plugin Scopes and Directory
All user-defined and third-party plugins reside in:
- **Global Plugins**: `~/.gemini/config/plugins/<plugin-name>/`
- Each plugin directory contains a `plugin.json` configuration file, which outlines capabilities, dependencies, and author metadata.

## 2. Listing and Querying Plugins
To view installed plugins:
1. List all subdirectories inside `~/.gemini/config/plugins/`.
2. For each directory, read its `plugin.json` file.
3. Parse and present the plugin name, version, description, and configured tools/permissions to the user.
4. You can also run the CLI command: `agy plugin list` if available in the terminal shell.

## 3. Installing/Staging a Plugin
To install a plugin:
1. Run `agy plugin install <plugin-id>` if it is a registered community plugin.
2. For manually downloaded/custom plugins:
   - Create a directory for the plugin under `~/.gemini/config/plugins/<plugin-name-kebab-case>/`.
   - Copy all its subdirectories (skills, rules, hooks, sidecars) and `plugin.json` into that folder.
   - Restart/reload the agent session if needed to trigger discovery.
