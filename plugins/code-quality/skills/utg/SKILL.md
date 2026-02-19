---
name: utg
description: Generate unit tests for the changed code in this branch
allowed-tools: Bash(git*)
---

Check the diff against origin/main, and generate unit tests for the changed code
in this branch. Run `git fetch origin` to make sure git context is up-to-date.

Here is the list of files changed in this branch:
!`git diff --stat origin/main`

**Focus on generating tests for the changed code:**

- Identify the functions/methods/classes that were added or modified
- Check if the changed code already has sufficient test coverage by looking at existing tests and coverage reports
- If coverage is low for the changed code, prioritize generating tests for those areas
- Only generate tests for logic changes, not data structure changes or formatting changes
- Generate unit tests that cover the new or changed functionality
- Ensure tests cover edge cases and error handling for the changed code
- Use the project's existing test framework and conventions
- Run the test suite with coverage after generating tests, and add more tests if coverage for changed code is low

**Testing guidelines:**

1. Tests should be isolated and not depend on external systems
2. Use mocks/stubs for dependencies as needed
3. Do not mock logging or telemetry calls
4. Only test from the public API of modules/classes, do not test
	 private/internal methods directly
5. Follow existing test style and conventions in the codebase
