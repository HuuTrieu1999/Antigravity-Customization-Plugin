---
name: manage-skills
description: Manage AntiGravity Skills (list, create, update, or install global and workspace skills)
---

# Skill: manage-skills

This skill instructs the agent on how to manage, view, create, and deploy AntiGravity Skills.

## 1. Skill Resolution Scopes
Skills can live in two scopes. When searching or creating, identify the target scope:
- **Global**: `~/.gemini/config/skills/<skill-name>/`
- **Workspace**: `<workspace-root>/.agents/skills/<skill-name>/` (or `.agent/skills/<skill-name>/` for backward compatibility)

## 2. Listing Skills
To inventory available skills:
1. List folders in the global skills directory.
2. List folders in the workspace `.agents/skills/` directory.
3. For each folder found, read its `SKILL.md` to extract the YAML metadata header (name and description).
4. Present this to the user in a clean table format.

## 3. Creating/Scaffolding a Skill
To create a new skill:
1. Ask the user for the name, scope, and target purpose of the skill.
2. Create the folder: `<target-directory>/skills/<skill-name-kebab-case>/`.
3. Create a `SKILL.md` inside it.
4. Populate `SKILL.md` with:
   - YAML frontmatter with `name` and `description`.
   - Markdown body outlining the step-by-step instructions.
5. If the skill requires scripts (e.g., node, python, bash), create a `scripts/` directory inside the skill folder and write the scripts there.

## 4. Installing/Importing a Skill
To download a skill from an external source (such as Git):
1. Create a temporary folder inside the workspace.
2. Fetch or download the skill contents.
3. Copy the skill directory into either the global or workspace-specific skills directory.
4. Verify that the `SKILL.md` matches the AntiGravity format.
