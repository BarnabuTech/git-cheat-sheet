# Advanced Git Commands

This guide covers more advanced Git commands and concepts for developers who are comfortable with the basics.

## Branch Management

### Working with Branches

```bash
# List all branches (local and remote)
git branch -a

# Create and switch to a new branch
git checkout -b feature/new-feature

# Delete a local branch
git branch -d branch-name

# Force delete a branch (use with caution!)
git branch -D branch-name

# Rename current branch
git branch -m new-branch-name
```

### Remote Branches

```bash
# List remote branches
git branch -r

# Delete a remote branch
git push origin --delete branch-name

# Track a remote branch
git checkout --track origin/branch-name
```

## Stashing Changes

Stashing lets you save your work without committing it.

```bash
# Stash changes
git stash save "Work in progress"

# List stashed changes
git stash list

# Apply the most recent stash
git stash apply

# Apply a specific stash
git stash apply stash@{n}

# Create a branch from a stash
git stash branch new-branch stash@{n}

# Clear all stashes
git stash clear
```

## Rewriting History

### Amending Commits

```bash
# Add changes to the last commit
git add .
git commit --amend

# Change the last commit message
git commit --amend -m "New commit message"
```

### Interactive Rebase

```bash
# Rebase last 3 commits
git rebase -i HEAD~3

# During interactive rebase, you can:
# - pick: use commit
# - reword: use commit, but edit the commit message
# - edit: use commit, but stop for amending
# - squash: use commit, but meld into previous commit
# - fixup: like "squash", but discard this commit's log message
# - drop: remove commit
```

## Git Reset vs Revert

### Reset (use with caution!)

```bash
# Soft reset (moves HEAD, keeps changes in working directory)
git reset --soft HEAD~1

# Mixed reset (default, moves HEAD and staging area)
git reset HEAD~1

# Hard reset (destructive! discards all changes)
git reset --hard HEAD~1
```

### Revert (safer alternative)

```bash
# Create a new commit that undoes changes
git revert <commit-hash>

# Revert a specific file to a previous commit
git checkout <commit-hash> -- path/to/file
```

## Git Bisect

Find which commit introduced a bug:

```bash
# Start bisect session
git bisect start

# Mark current commit as bad
git bisect bad

# Mark a known good commit
git bisect good <commit-hash>

# Mark current commit as good/bad
git bisect good  # or bad

# End bisect session
git bisect reset
```

## Submodules

Work with other Git repositories within your project:

```bash
# Add a submodule
git submodule add <repository-url> <path>

# Initialize and update submodules
git submodule update --init --recursive

# Update all submodules to latest commits
git submodule update --remote
```

## Git Hooks

Automate tasks with Git hooks:

- `.git/hooks/` - Directory containing hook scripts
- `pre-commit` - Runs before commit
- `pre-push` - Runs before push
- `post-merge` - Runs after merge

## Git Worktrees

Work on multiple branches simultaneously:

```bash
# Create a new worktree
git worktree add ../new-branch branch-name

# List worktrees
git worktree list

# Remove a worktree
git worktree remove ../path-to-worktree
```

## Tips & Tricks

```bash
# Show what changed in a commit
git show <commit-hash>

# Find which commit introduced a bug
git blame path/to/file

# Clean untracked files (use with caution!)
git clean -fd

# Search through commit messages
git log --grep="search term"

# Show changes between branches
git diff branch1..branch2

# Show commit history as a graph
git log --graph --oneline --all
```

Remember: With great power comes great responsibility. Always double-check commands before running them, especially when rewriting history or using destructive commands like `git reset --hard`.
