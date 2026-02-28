---
name: cohesive
description: Check code modified in the current branch for cohesiveness, and execute refactors
allowed-tools: Bash(git*), Bash(sg*), Read, Edit, Glob, Grep, Task
---

Check the diff against origin/main, and review the changed code for cohesiveness.
Run `git fetch origin` to make sure git context is up-to-date.

Here is the list of files changed in this branch:
!`git diff --name-only origin/main`

For each changed file, read the full file and assess whether the modifications
maintain or improve cohesion. Then execute refactors to fix any issues found.

## What to look for

### Single Responsibility violations

- Functions/methods that now handle multiple unrelated concerns after the change
- Classes that gained responsibilities outside their original purpose
- Modules that mix abstraction levels (e.g., business logic interleaved with I/O)

### Misplaced code

- Logic added to a file/module where it doesn't conceptually belong
- Utility code inlined where it should live in a shared module (only if one already exists)
- Data transformations happening far from the data's source or consumer

### Coupling introduced by the change

- New dependencies between modules that should be independent
- Functions that reach deep into other modules' internals
- Shared mutable state introduced across boundaries

### Scattered related logic

- Related logic for a single feature spread across many files unnecessarily
- Duplicated logic that should be consolidated
- Related constants, types, or helpers that belong together but are separated

## How to refactor

- Extract functions/methods when a block handles a distinct sub-task
- Move code to the module where it conceptually belongs
- Group related logic together within a file
- Consolidate duplicated logic into a single location
- Split files only when they clearly serve multiple unrelated purposes

## Rules

- Only refactor code touched by the branch diff — do not reorganize unrelated code
- Preserve external behavior exactly; no functional changes
- Follow existing project conventions for file organization and naming
- Do not create new files unless a clear, existing organizational pattern calls for it
- Run the project's linter/formatter after refactoring if one is configured

Report at the end with a brief summary of refactors performed.
