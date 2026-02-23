---
name: organize
description: Split large files into manageable chunks following language-specific best practices
allowed-tools: Bash(git*), Bash(sg*), Read, Write, Edit, Glob, Grep, Task
---

Check the diff against origin/main, and identify large files that were added or
modified in this branch. Run `git fetch origin` to make sure git context is
up-to-date.

Here is the list of files changed in this branch:
!`git diff --name-only origin/main`

For each changed file, read the full file and determine if it should be split
based on the language conventions below. Then execute the splits, updating all
imports and references across the project.

## Language conventions

### TypeScript / JavaScript / React

- One React component per file, named after the component
- Colocate component styles and tests alongside the component
- Redux: prefer ducks pattern — slice file contains actions, reducers, and selectors for one domain
- Separate types/interfaces into a `types.ts` when shared across multiple files
- Barrel exports (`index.ts`) for public API of a directory

### Swift / SwiftUI

- One SwiftUI view per file, previews stay in the same file
- One UIKit view controller per file
- Protocols and their default extensions can share a file
- Separate model types into individual files when they exceed trivial size

### Java / Kotlin

- One top-level class per file, file named after the class
- Inner classes stay with their outer class unless they grow large and are used externally
- Kotlin: data classes that are only used by one file can stay; shared ones get their own file

### Python

- One class per file when the class is substantial
- Group small related data classes or enums in a single file
- Separate CLI entry points from library code

### Go

- Group by responsibility: types, handlers, middleware, etc.
- Keep interfaces near the code that depends on them, not the implementation
- Test files mirror source files (`foo.go` → `foo_test.go`)

### General (any language)

- Files over ~300 lines are candidates for splitting
- Files over ~500 lines should almost always be split
- Keep tightly coupled code together — don't split just to hit a line count
- Helper/utility functions used by only one caller stay with the caller

## How to split

1. Identify logical groupings within the file
2. Create new files following the project's existing directory structure and naming conventions
3. Move code to the new files
4. Update all imports, references, and re-exports across the entire project
5. Verify no circular dependencies are introduced
6. Run the project's linter/formatter if configured

## Rules

- Only split files touched by the branch diff
- Preserve external behavior exactly; all existing imports from other files must continue to work
- Follow the project's existing naming and directory conventions over the guidelines above
- Do not rename exported symbols — only move them
- When in doubt about whether to split, leave the code together

Report at the end with a brief summary of files split and the rationale.
