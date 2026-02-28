# agent skills by recrsn

A collection of agent skills for Claude Code and 40+ other AI coding tools.

## Install

```bash
npx skills add recrsn/claude-plugins
```

Or install a specific skill:

```bash
npx skills add recrsn/claude-plugins --skill deslop
```

## Skills

### deslop

Remove all unnecessary changes introduced in this branch — noisy comments, defensive boilerplate, debug logging, `any` casts, and commented-out code.

### utg

Generate unit tests for code changed in this branch.

### cohesive

Review code changed in this branch for cohesiveness — single responsibility, misplaced logic, coupling, scattered features — and execute refactors.

### organize

Split large files changed in this branch into manageable chunks following language best practices — one component per file, ducks pattern, one class per file, etc.

### electron-to-electrobun

Migrate an Electron app to [Electrobun](https://electrobun.dev/). Runs a compatibility audit first, then migrates IPC, windows, preload, menus, dialogs, and build config to Electrobun equivalents.
