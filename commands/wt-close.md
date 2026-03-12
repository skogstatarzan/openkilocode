---
description: Mark feature/bugfix as complete and close the worktree
---

You have now completed the work in the current worktree environment.

The user provided reason: {{args}}

If no reason was provided, ask the user for a brief explanation of what was accomplished.

Follow this checklist:

1. **Ensure all code is tested and functional**
   - Run any relevant tests
   - Verify the implementation works as expected

2. **Commit all changes locally** if needed
   - Note: `worktree_delete` performs an auto-commit, but you may want to commit explicitly first for a cleaner history

3. **Call the `worktree_delete` tool** with the reason provided by the user

The worktree will be cleaned up and you'll return to the main working directory.
