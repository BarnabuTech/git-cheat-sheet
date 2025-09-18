# Git & GitHub for Beginners

## What is Version Control?

Version control is a system that records changes to files over time so you can recall specific versions later. It's like a time machine for your projects, allowing you to track changes, see who made them, and revert to previous versions if needed.

## Why Use Git?

- **Track Changes**: See what was changed, when, and by whom
- **Collaboration**: Work on the same project with others without conflicts
- **Backup**: Your code is stored both locally and remotely
- **Experimentation**: Try new features without breaking your working code

## Basic Git Commands

### Setting Up

Configuration user information used across all local repositories.

```bash
git config --global user.name "Your Name"
# Set a name that is identifiable for credit when review version history.

git config --global user.email "your.email@example.com"
# Set an Email address that will be associated with each history marker.
```

### Setup and INIT

Configuring user information, initializing and cloning repositories.

```bash
# Initialize a new Git repository
git init

# Clone an existing repository
git clone <repository-url>
```

### Stage and Snapshot

Working with snapshots and the Git staging area.

```bash
# Check status of working directory
git status

# Add files to staging area
git add <file>     # Add specific file
git add .          # Adding all changes

# Unstage a file while retaining the changes in working directory.
git reset <file>         

# Diff of what is changed but not staged.
git diff

# Diff of what is staged but not yet commited.
git diff --staged

# Commit changes with a message
git commit -m "Descriptive message about changes"
```
### Inspect and Compare

Examine logs, diffs and object information.

```bash
# Show the commit history for the currently active branch.
git log

# show the commits on branchA that are not on branchB files to staging area
git log branchB..branchA     

# show the commits that changed file, even across renames.
git log --follow[file]         

# show the diff of what is in branchA that is not in branchB.
git diff branchB...branchA

# show any object in Git in human-readable format.
git show [SHA]

# Commit changes with a message
git commit -m "Descriptive message about changes"
```

### Add Other Basic Git Commands

Check the repository issue tab and add any of yours as from here.

## GitHub Basics

### What is GitHub?

GitHub is a web-based platform that uses Git for version control. It provides a graphical interface and additional features like issue tracking and project management.

### Key GitHub Concepts

- **Repository (repo)**: A project's files and revision history
- **Fork**: A personal copy of someone else's project
- **Pull Request (PR)**: Proposing changes to someone else's repository
- **Issues**: Track bugs, enhancements, or tasks

### GitHub Workflow

1. **Fork** the repository
2. **Clone** your fork locally
3. Create a new **branch** for your changes
4. Make your changes and **commit** them
5. **Push** your changes to your fork
6. Create a **Pull Request** to the original repository

## Best Practices

1. Write clear, concise commit messages
2. Make small, focused commits
3. Create branches for new features or fixes
4. Keep your main branch clean and stable
5. Pull before you push to avoid conflicts
6. Use .gitignore to exclude unnecessary files

## Common Issues & Solutions

- **Merge conflicts**: Edit the conflicted file, then `git add` and `git commit`
- **Undo local changes**: `git checkout -- <file>`
- **Undo last commit**: `git reset --soft HEAD~1`
- **View commit history**: `git log --oneline --graph --decorate --all`

## Resources

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Learn Git Branching](https://learngitbranching.js.org/)

## Getting Help

- `git help <command>` - Get help for a specific command
- `git --help` - List common Git commands
- [GitHub Community Forum](https://github.com/orgs/community/discussions)

Remember: Everyone was a beginner once! Don't be afraid to make mistakes - that's how we learn. Happy coding! 🚀
