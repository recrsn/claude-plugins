# Claude Code Plugins by recrsn

A collection of Claude Code plugins.

## Install

Add this marketplace to Claude Code:

```
/plugin marketplace add recrsn/claude-plugins
```

## Plugins

### electron-to-electrobun

Migrate Electron apps to [Electrobun](https://electrobun.dev/).

```
/plugin install electron-to-electrobun@recrsn-claude-plugins
```

**Usage:**

```
/electron-to-electrobun:migrate
```

**What it does:**

- **Phase 1 — Compatibility audit**: Scans your Electron app for API usage (IPC, BrowserWindow, dialogs, menus, clipboard, shell, native modules, build config) and produces a compatibility report with effort estimate
- **Phase 2 — Step-by-step migration**:
  - Replaces Electron IPC with Electrobun's typed RPC schemas
  - Migrates BrowserWindow constructor options and methods
  - Converts preload/contextBridge to RPC (strips IPC bridge code, keeps polyfills)
  - Maps dialogs, menus, clipboard, shell, notifications, paths, and credentials to Electrobun equivalents
  - Updates renderer bridge calls to `rpc.request.*` / `rpc.addMessageListener`
  - Replaces CSS `-webkit-app-region: drag` with Electrobun CSS classes
  - Configures `electrobun.config.ts` build setup
  - Type-checks after each step

### code-quality

Code quality tools for the current branch.

```
/plugin install code-quality@recrsn-claude-plugins
```

**Usage:**

```
/code-quality:deslop  # remove noisy additions (comments, boilerplate, debug logs)
/code-quality:utg     # generate unit tests for changed code
```

## Links

- [Electrobun documentation](https://electrobun.dev/)
- [Electrobun GitHub](https://github.com/nicholasgasior/electrobun)
- [Claude Code plugins](https://docs.anthropic.com/en/docs/claude-code)
