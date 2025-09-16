# Git Branching: A Visual Guide

Understanding branches is key to mastering Git. This guide uses simple diagrams to show how branches work.

## Basic Branching

### Starting Point

```
A---B---C (main)
```
- `A`, `B`, `C` are commits
- `(main)` is the branch pointer

### Creating a New Branch

```bash
git checkout -b feature
```

```
A---B---C (main, feature)
```
- Both `main` and `feature` point to commit `C`

### Making Commits on a Branch

```bash
git commit -m "Add feature X"
```

```
A---B---C (main)
         \
          D (feature)
```
- `feature` branch moves forward with new commit `D`
- `main` stays at commit `C`

## Merging

### Fast-Forward Merge

When the target branch hasn't diverged:

```
A---B---C (main)
         \
          D---E (feature)
```

```bash
git checkout main
git merge feature
```

Result:

```
A---B---C---D---E (main, feature)
```

### 3-Way Merge

When both branches have new commits:

```
A---B---C (main)
     \
      D---E (feature)
```

```bash
git checkout main
git merge feature
```

Result:

```
A---B---C---F (main)
     \     /
      D---E (feature)
```
- `F` is a merge commit with two parents

## Rebasing

### Before Rebase

```
A---B---C (main)
     \
      D---E (feature)
```

### After Rebase

```bash
git checkout feature
git rebase main
```

```
A---B---C (main)
         \
          D'---E' (feature)
```
- `D'` and `E'` are new commits with different hashes
- History is linear

## Common Branching Workflows

### Feature Branch Workflow

```
main:     A---B-----------F---G (main)
           \             /
feature:    C---D---E---/ (feature)
```
1. Create `feature` from `main`
2. Make commits `C`, `D`, `E` on `feature`
3. Merge `feature` back into `main`

### Hotfix Workflow

```
main:     A---B---C---E (main)
               \     /
hotfix:         D---/ (hotfix)
```
1. Create `hotfix` from `main`
2. Fix the bug in commit `D`
3. Merge `hotfix` back into `main`

## Branch Management

### Viewing Branches

```bash
# Local branches
git branch

# All branches (including remote)
git branch -a

# Show branch relationships
git log --graph --oneline --all
```

### Cleaning Up

```bash
# Delete merged branches
git branch --merged | egrep -v "(^\*|main|master|dev)" | xargs git branch -d

# Prune remote-tracking branches
git fetch --prune
```

## Best Practices

1. **Keep branches focused** - One feature/bugfix per branch
2. **Name branches clearly** - Use prefixes like `feature/`, `bugfix/`, `hotfix/`
3. **Update often** - Rebase or merge from main frequently
4. **Delete merged branches** - Keep your repository clean
5. **Use pull requests** - For code review before merging

## Common Branching Patterns

### Long-Running Branches

```
main:     A---B---C---F---G---H (main)
           \     /     /
release:   D---E-----/ (release-1.0)
             \       /
feature:      \-----/ (feature-x)
```
- `main` - Always deployable
- `release-*` - Release preparation
- `feature-*` - New features

### Git Flow

```
main:     A---B-------D---F (main)
           \         /   /
release:    C-------E---/ (release-1.0)
             \     /
develop:      \---/ (develop)
               \   \
feature:        G---H (feature-x)
```
- `main` - Production releases
- `develop` - Integration branch
- `feature/*` - New features
- `release/*` - Release preparation
- `hotfix/*` - Critical bug fixes

## Visualizing with GitK

For a graphical view of your branches:

```bash
gitk --all
```

Or use these commands:

```bash
# Show commit graph
git log --graph --oneline --all

# Show branch tree
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

Remember: Branches are just pointers to commits. They're lightweight and easy to create, so use them liberally!
