# code-quality

Code quality tools for the current branch.

## Install

```
/plugin install code-quality@recrsn-plugins
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
