# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A Claude Code plugin marketplace — a collection of skills organized as plugins. There is no build system, no dependencies, and no test infrastructure. All implementation logic lives in SKILL.md files that Claude Code executes directly.

## Architecture

```
.claude-plugin/marketplace.json    ← marketplace registry (lists all plugins)
plugins/<plugin-name>/
  .claude-plugin/plugin.json       ← plugin manifest (name, version, author)
  README.md                        ← plugin documentation
  skills/<skill-name>/SKILL.md     ← skill definition (frontmatter + instructions)
```

### Key concepts

- **Marketplace**: The root `.claude-plugin/marketplace.json` registers plugins with name, source path, category, and version.
- **Plugin**: A directory under `plugins/` with a `.claude-plugin/plugin.json` manifest. Groups related skills.
- **Skill**: A `SKILL.md` file with YAML frontmatter (`name`, `description`, `allowed-tools`) followed by the full prompt/instructions Claude Code will execute.

### Current plugins

| Plugin | Skills | Category |
|--------|--------|----------|
| `migrate` | `electron-to-electrobun` | migration |
| `code-quality` | `deslop`, `utg` | code quality |

## Conventions

- Skills declare their `allowed-tools` in frontmatter — respect the minimal permission set (e.g., `Bash(git*)` means git-only shell access).
- The `deslop` and `utg` skills operate on branch diffs against `origin/main`.
- Skill SKILL.md files are self-contained prompts; they are documentation *and* implementation.

## Adding a new skill

1. Create `plugins/<plugin>/skills/<skill-name>/SKILL.md` with frontmatter:
   ```yaml
   ---
   name: skill-name
   description: What the skill does
   allowed-tools: <comma-separated tool list>
   ---
   ```
2. Add the plugin to `.claude-plugin/marketplace.json` if it's a new plugin.
3. Create/update `plugins/<plugin>/.claude-plugin/plugin.json` and `plugins/<plugin>/README.md`.
