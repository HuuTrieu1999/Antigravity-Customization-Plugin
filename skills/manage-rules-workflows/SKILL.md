---
name: manage-rules-workflows
description: Manage Rules and Workflows (create, edit, or configure agent constraints and slash commands)
---

# Skill: manage-rules-workflows

This skill instructs the agent on how to manage Rules (behavioral guidelines) and Workflows (slash command task templates).

## 1. Rules (Guidelines & Constraints)
Rules are Markdown files loaded by the agent to constraint behavior.
- **Global Rules**: `~/.gemini/GEMINI.md` (applies to all workspaces).
- **Workspace Rules**: `<workspace-root>/.agents/rules/` (applies only to the current project).

### Adding/Modifying a Rule
1. Open the target rule file.
2. Structure the guidelines with clear headings and markdown formatting.
3. Configure the activation criteria in the file or parent folder if needed (Always On, Glob patterns, etc.).
4. Save and verify.

## 2. Workflows (Slash Commands)
Workflows are step-by-step task templates that can be triggered in the agent's chat interface.
- **Workspace Workflows**: `<workspace-root>/.agents/workflows/<workflow-name>.md`
- **Global Workflows**: `~/.gemini/config/workflows/<workflow-name>.md`

### Creating a Custom Slash Command Workflow
1. Create a markdown file named `<workflow-command>.md` (e.g., `generate-tests.md` will be called via `/generate-tests`).
2. Populate the file with:
   - Outline of steps.
   - Specific model commands and prompts to execute.
   - Guidelines for parsing inputs.
3. Validate by reloading the agent workspace to verify the slash command is registered.
