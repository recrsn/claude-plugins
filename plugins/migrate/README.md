# migrate

Migration skills for moving between frameworks and runtimes.

## Install

```
/plugin install migrate@recrsn-claude-plugins
```

## Skills

### electron-to-electrobun

Migrate an Electron app to [Electrobun](https://electrobun.dev/).

```
/migrate:electron-to-electrobun
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

## Links

- [Electrobun documentation](https://electrobun.dev/)
- [Electrobun GitHub](https://github.com/nicholasgasior/electrobun)
