# GitHub

This section covers the GitHub platform, repository workflows, collaboration, pull requests, issues, and automation basics.

## Important distinction

Git != GitHub

- Git is the version-control tool.
- GitHub is the platform where you host/share Git repositories and collaborate.

So this GitHub section should focus more on the GitHub workflow, not repeat every Git command.

## Core learning rule
For every GitHub workflow step, understand:
- What is it?
- Why do I need it?
- What does it change?
- How do I verify it?

Example:

```bash
git push -u origin main
```

Don't only memorize it. Understand:

> `git` → the version control tool  
> `push` → upload local commits  
> `-u origin main` → push the `main` branch to the remote named `origin` and set tracking

This helps you understand how GitHub works in practice.

## Topics
- repositories
- clone / fork
- push / pull
- branches
- Pull Requests
- Issues
- README.md
- GitHub Actions (later)
- GitHub CLI (gh)

## Files
- `commands.md` — GitHub command reference and workflow examples
- `notes.md` — personal notes and practical understanding

## Study goals
- Understand GitHub repository workflow
- Clone and connect repos to GitHub
- Push branches and create pull requests
- Use issues and documentation
- Learn GitHub CLI basics
- Understand GitHub collaboration practices

## How to learn each command
Before using a command, ask:
1. What does this GitHub step do?
2. What repository or branch is involved?
3. What output should I expect?
4. How do I confirm the change in GitHub?

Example workflow:
```bash
git switch -c feature-name
git add .
git commit -m "Add feature"
git push -u origin feature-name
```

These steps together answer:
- Where is the work happening?
- What is being changed?
- How is it shared on GitHub?
- How do I create the review workflow?

That is the difference between using GitHub and understanding GitHub.
