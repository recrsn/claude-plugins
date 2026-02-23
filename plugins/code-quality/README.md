# code-quality

Code quality tools for the current branch.

## Install

```
/plugin install code-quality@recrsn-claude-plugins
```

## Skills

### deslop

Remove all unnecessary changes introduced in this branch — noisy comments, defensive boilerplate, debug logging, `any` casts, and commented-out code.

```
/code-quality:deslop
```

### utg

Generate unit tests for code changed in this branch.

```
/code-quality:utg
```

### organize

Split large files changed in this branch into manageable chunks following language best practices — one component per file, ducks pattern, one class per file, etc.

```
/code-quality:organize
```

### cohesive

Review code changed in this branch for cohesiveness — single responsibility, misplaced logic, coupling, scattered features — and execute refactors.

```
/code-quality:cohesive
```
