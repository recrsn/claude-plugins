# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

An agent skills repository — a collection of SKILL.md files installable via the `skills` CLI (`npx skills`). There is no build system, no dependencies, and no test infrastructure. All implementation logic lives in SKILL.md files that agents execute directly.

## Architecture

```
skills/<skill-name>/
  SKILL.md    ← skill definition (frontmatter + instructions)
```

### Key concepts

- **Skill**: A `SKILL.md` file with YAML frontmatter (`name`, `description`, `allowed-tools`) followed by the full prompt/instructions the agent will execute.
- **Install**: `npx skills add recrsn/claude-plugins` installs all skills; `--skill <name>` installs one.

### Current skills

| Skill | Description |
|-------|-------------|
| `deslop` | Remove unnecessary changes (comments, boilerplate, debug logs) from the current branch |
| `utg` | Generate unit tests for code changed in the current branch |
| `cohesive` | Review and refactor changed code for cohesion |
| `organize` | Split large files following language-specific conventions |
| `electron-to-electrobun` | Migrate an Electron app to Electrobun |

## Conventions

- Skills declare their `allowed-tools` in frontmatter — respect the minimal permission set (e.g., `Bash(git*)` means git-only shell access).
- The `deslop`, `utg`, `cohesive`, and `organize` skills operate on branch diffs against `origin/main`.
- Skill SKILL.md files are self-contained prompts; they are documentation *and* implementation.

## Adding a new skill

1. Create `skills/<skill-name>/SKILL.md` with frontmatter:
   ```yaml
   ---
   name: skill-name
   description: What the skill does and when to use it
   allowed-tools: <comma-separated tool list>
   ---
   ```
2. Add a one-line entry to the skills table in `README.md` and this file.
