# GitHub Commands

## Useful quick reference

| Goal | Command |
|---|---|
| Clone repo | `git clone <github-repository-url>` |
| Connect repo to GitHub | `git remote add origin <github-repository-url>` |
| Check remote URL | `git remote -v` |
| Push branch | `git push -u origin main` |
| Push new commits | `git push` |
| Download + merge | `git pull` |
| Download without merge | `git fetch` |
| Create branch | `git switch -c feature-name` |
| Push branch to GitHub | `git push -u origin feature-name` |
| Delete remote branch | `git push origin --delete <branch-name>` |
| List PRs | `gh pr list` |
| Create PR | `gh pr create` |
| List issues | `gh issue list` |
| Create issue | `gh issue create` |
| Check GitHub CLI | `gh --version` |
| Log into GitHub CLI | `gh auth login` |
| List repos | `gh repo list` |
| Clone via GitHub CLI | `gh repo clone <owner>/<repo>` |
| Create repo | `gh repo create` |

---

## Core learning rule
For every GitHub step, understand:
- What is it?
- Why do I need it?
- What does it change?
- How do I verify it?

Example:

```bash
git push -u origin main
```

Break it down:

> `git` → version control tool  
> `push` → uploads local commits  
> `-u origin main` → pushes the `main` branch to the `origin` remote and sets upstream tracking

Then verify by checking GitHub to see the branch and commit appear.

---

## 1. Clone a GitHub repository

### `git clone <github-repository-url>`
```bash
git clone <github-repository-url>
```
Downloads a GitHub repository to your computer.
- What is it? A copy of the remote repo.
- Why do I need it? To work on the project locally.
- What does it change? Creates a local folder with the repo contents.
- How do I verify it? Run `ls` or `git status` inside the project folder.

---

## 2. Connect local repo to GitHub

### `git remote add origin <github-repository-url>`
```bash
git remote add origin <github-repository-url>
```
Connects the local repository to a GitHub remote.
- What is it? A link between the local repo and the remote host.
- Why do I need it? So you can push and pull changes.
- What does it change? Adds a remote named `origin`.
- How do I verify it? Run `git remote -v`.

### `git remote -v`
```bash
git remote -v
```
Shows the connected remote repositories.
- This confirms the GitHub URL is configured correctly.

---

## 3. Push to GitHub

### `git push -u origin main`
```bash
git push -u origin main
```
Pushes the `main` branch to GitHub and sets upstream tracking.
- Why do I need it? To upload your work to the remote repository.
- Verify by checking the GitHub repository page and branch.

### `git push`
```bash
git push
```
Pushes new commits to the upstream branch.
- Use this after the initial `-u` setup.

---

## 4. Get changes from GitHub

### `git pull`
```bash
git pull
```
Downloads and merges changes from the remote repository.
- Why do I need it? To sync your local branch with GitHub.
- Verify by checking `git status` and the updated files.

### `git fetch`
```bash
git fetch
```
Downloads remote changes without merging them.
- Useful to inspect changes before integrating them.

---

## 5. Branch workflow

### `git switch -c feature-name`
```bash
git switch -c feature-name
```
Creates and switches to a new feature branch.
- Why do I need it? To isolate features or fixes before merging.
- Verify with `git branch` or `git status`.

### `git push -u origin feature-name`
```bash
git push -u origin feature-name
```
Pushes a new branch to GitHub.
- This makes the branch available for review.

---

## 6. Delete remote branch

### `git push origin --delete <branch-name>`
```bash
git push origin --delete <branch-name>
```
Deletes a branch from GitHub.
- Use this when a feature branch is no longer needed.
- Verify by checking the branch list in the repository.

---

## 7. Fork workflow

```bash
# 1. Fork the repository on GitHub
# 2. Clone your fork

git clone <your-fork-url>

# 3. Create a branch
git switch -c feature-name

# 4. Make changes
git add .
git commit -m "Add feature"

# 5. Push the branch
git push -u origin feature-name

# 6. Open a Pull Request on GitHub
```

This is the standard fork-and-pull workflow for contributing to open-source or shared repos.

---

## 8. Pull Requests and collaboration

### Pull Request basics
- Create a feature branch
- Push it to GitHub
- Open a Pull Request
- Review code and discuss changes
- Merge after approval

How to verify a PR:
- Check the diff
- Review comments
- Confirm the target branch is correct
- Make sure tests/build pass if required

---

## 9. GitHub CLI (`gh`)

### `gh --version`
```bash
gh --version
```
Checks whether GitHub CLI is installed.

### `gh auth login`
```bash
gh auth login
```
Logs in to GitHub from the terminal.

### `gh repo list`
```bash
gh repo list
```
Lists repositories available to the logged-in user.

### `gh repo clone <owner>/<repo>`
```bash
gh repo clone <owner>/<repo>
```
Clones a GitHub repository using GitHub CLI.

### `gh repo create`
```bash
gh repo create
```
Creates a GitHub repository.

### `gh pr list`
```bash
gh pr list
```
Lists pull requests for the current repository.

### `gh pr create`
```bash
gh pr create
```
Creates a pull request from the terminal.

### `gh issue list`
```bash
gh issue list
```
Lists issues in the current repo.

### `gh issue create`
```bash
gh issue create
```
Creates a new GitHub issue from the terminal.

---

## 10. README and repository docs

```md
# Project Name

Short description of the project

## Features
- feature 1
- feature 2

## Installation
npm install

## Usage
npm run dev
```

A good README explains:
- what the project does
- how to run it
- how to set it up
- where to learn more

---

## 11. GitHub workflow example

```bash
git clone <github-repository-url>
git switch -c feature-name
git add .
git commit -m "Add feature"
git push -u origin feature-name
```

This is the normal process for starting a small feature branch on GitHub.

---

> Keep adding GitHub workflow examples and notes as you use GitHub in real projects.

