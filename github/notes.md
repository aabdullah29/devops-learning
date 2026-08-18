# GitHub Notes

`notes.md` is for your own learning notes — things you understand, explanations, mistakes, and important concepts.

## Important distinction

Git is the version-control tool.

GitHub is the platform where you host and share Git repositories and collaborate with others.

So GitHub notes should focus on the workflow of using Git repositories on GitHub, not repeating every command from Git.

## GitHub basics
GitHub is a web platform for hosting Git repositories and working with teams.

It helps with:
- storing code online
- collaborating with teammates
- reviewing changes with pull requests
- tracking work with issues
- documenting projects with README files

## Clone a repository
Example:
```bash
git clone <github-repository-url>
```

This copies the repository from GitHub to your local machine.

## Remote repository
A GitHub repository is usually connected as the `origin` remote.

Example:
```bash
git remote add origin <github-repository-url>
git remote -v
```

This lets you push and pull from GitHub.

## Push to GitHub
Example:
```bash
git push -u origin main
```

This uploads the local branch to GitHub and sets the upstream branch.

## Pull request
A pull request is a request to merge one branch into another, usually `main`.

Typical flow:
1. Create a branch
2. Make changes
3. Commit changes
4. Push branch to GitHub
5. Open a pull request
6. Review and merge

## Branches on GitHub
A branch on GitHub is just a version of the project used for independent work.

Example:
```bash
git switch -c feature-name
git push -u origin feature-name
```

This makes a branch available for collaboration and review.

## Forking
A fork is your own copy of someone else's GitHub repository.

Typical workflow:
1. Fork repository
2. Clone your fork
3. Create a branch
4. Make changes
5. Push to your fork
6. Open a pull request to the original repo

## Issues
Issues are used to track bugs, tasks, features, and improvements.

Examples:
- bug report
- feature request
- task list
- project tracking

## README
A README explains the project and helps people understand:
- what it does
- how to run it
- how to install it
- what the project is for

## GitHub CLI
The GitHub CLI (`gh`) lets you interact with GitHub from the terminal.

Examples:
```bash
gh --version
gh auth login
gh repo list
gh pr create
gh issue create
```

This is helpful for automation and command-line workflow.

## Important habit
For every GitHub action, I should ask:
- What does this step do in the repository?
- Which branch or repo is involved?
- What should I check in GitHub after running it?

Example:
```bash
git push -u origin main
```

This is not just a Git command. It is the step that makes my code appear on GitHub for others to see and review.

## My learning summary
GitHub is where the Git workflow becomes collaborative. The important part is not memorizing every Git command, but understanding the repository flow: clone, branch, commit, push, pull request, review, and merge.
