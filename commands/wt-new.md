---
description: Start a new feature in an isolated git worktree
---

You are about to start work on a **new feature**.

The user provided: {{args}}

Parse this input to extract:
1. **Feature name** (required): A short, descriptive name for the feature
2. **Base branch** (optional, default: main): The branch to base the work on

Examples of valid input:
- `user-auth` → name: "user-auth", base: "main"
- `user-auth develop` → name: "user-auth", base: "develop"
- `add dark mode` → name: "add-dark-mode", base: "main"
- `fix login bug main` → name: "fix-login-bug", base: "main"

Follow this exact checklist:

1. **Determine a suitable branch name** based on the feature name:
   - Format: `feature/{{kebab-case of name}}` (e.g., `feature/user-onboarding-wizard`)
   - Keep it short and clear
   - Convert spaces and special characters to kebab-case

2. **Call the `worktree_create` tool**:
   - `branch` = the branch name you determined
   - `baseBranch` = the base branch (main if not specified)

3. **Once the worktree is created** → shift your focus there and begin implementation according to the user's next instructions.
