# Git

This section covers the essential Git workflow for version control, collaboration, and repository management.

## Core learning rule
For every Git command, understand:
- What is it?
- Why do I need it?
- What does it change?
- How do I verify it?

Example:

```bash
git status
```

Don't only memorize it. Understand:

> `git` → the version control system  
> `status` → asks for the current state of the repository  
> It does not change code; it only reports the repo state

This helps you learn Git as a workflow, not as random commands.

## Topics
- init / clone
- status
- add / commit
- log / diff
- branch
- merge
- stash
- reset / revert
- .gitignore
- remote / push / pull
- config
- GitHub workflow basics

## Files
- `commands.md` — command reference and explanations
- `notes.md` — personal learning notes and explanations

## Study goals
- Create and clone repositories
- Track changes with commit history
- Work with branches and merging
- Recover from mistakes safely
- Use Git with GitHub workflows
- Understand how Git records and shares project history

## How to learn each command
Before using a command, ask:
1. What does this command do?
2. What part of Git does it interact with?
3. What output should I expect?
4. How do I confirm the result?

Example workflow:
```bash
git status
git add .
git commit -m "Add feature"
git push origin main
```

These commands together answer:
- What changed?
- What is staged?
- What commit was created?
- Was it sent to the remote repository?

That is the difference between memorizing Git commands and understanding Git.
