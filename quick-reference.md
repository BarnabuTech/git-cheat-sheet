# Git Quick Reference Cheat Sheet

## Setup & Configuration

```bash
# Set your name and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default branch name to 'main'
git config --global init.defaultBranch main

# Set default editor (e.g., VS Code)
git config --global core.editor "code --wait"
```

## Getting Started

```bash
# Initialize a new repository
git init

# Clone an existing repository
git clone <repository-url>

# Check repository status
git status
```

## Basic Workflow

```bash
# Stage changes
git add <file>     # Stage specific file
git add .          # Stage all changes

# Commit changes
git commit -m "Descriptive message"

# View commit history
git log

# View compact commit history
git log --oneline --graph --decorate --all
```

## Branching

```bash
# List branches
git branch         # Local branches
git branch -a      # All branches (including remote)

# Create and switch to new branch
git checkout -b new-branch

# Switch to existing branch
git checkout branch-name

# Delete a branch
git branch -d branch-name     # Safe delete
git branch -D branch-name     # Force delete
```

## Remote Repositories

```bash
# Add a remote
git remote add origin <url>

# View remotes
git remote -v

# Push to remote
git push -u origin branch-name

# Pull changes
git pull origin branch-name

# Fetch changes (without merging)
git fetch
```

## Undoing Things

```bash
# Unstage a file
git restore --staged <file>

# Discard changes in working directory
git restore <file>

git checkout -- <file>  # Alternative for older Git

# Amend last commit
git commit --amend -m "New message"

# Revert a commit
git revert <commit-hash>

# Reset to previous commit (use with caution!)
git reset --hard HEAD~1
```

## Stashing

```bash
# Stash changes
git stash save "Message"

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{n}

# Drop a stash
git stash drop stash@{n}
```

## Common Workflows

### Feature Branch Workflow

```bash
git checkout -b feature/new-feature
# Make changes
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature
# Create pull request on GitHub/GitLab
```

### Fixing a Bug

```bash
git checkout -b bugfix/issue-123
git add .
git commit -m "Fix issue #123"
git push -u origin bugfix/issue-123
```

## Common Issues

### Merge Conflicts

1. Edit the conflicted files
2. Mark as resolved: `git add <file>`
3. Complete the merge: `git commit`

### Discard All Local Changes

```bash
git reset --hard
git clean -fd
```

### Find What Changed

```bash
# What changed in a file
git diff

# Who changed what and when
git blame <file>

# Search commit messages
git log --grep="search term"
```

## Aliases (Add to ~/.gitconfig)

```ini
[alias]
    co = checkout
    br = branch
    ci = commit
    st = status
    last = log -1 HEAD
    lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

---

**Remember:**
- Always check `git status` before and after commands
- When in doubt, `git help <command>` is your friend
- Commit often, perfect later, publish once
- Write clear, descriptive commit messages
