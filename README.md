# Claude Code Plugins by recrsn

A collection of Claude Code plugins.

## Install

Add this marketplace to Claude Code:

```
/plugin marketplace add recrsn/claude-plugins
```

## Plugins

### [migrate](plugins/migrate/README.md)

Migration skills for moving between frameworks and runtimes.

```
/plugin install migrate@recrsn-claude-plugins
```

**Skills:**

```
/migrate:electron-to-electrobun  # migrate an Electron app to Electrobun
```

### [code-quality](plugins/code-quality/README.md)

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
