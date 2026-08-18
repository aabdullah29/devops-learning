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
| Check SSH installed | `ssh -V` |
| List SSH keys | `ls -al ~/.ssh` |
| Generate SSH key | `ssh-keygen -t ed25519 -C "email@example.com"` |
| Start SSH agent | `eval "$(ssh-agent -s)"` |
| Add SSH key to agent | `ssh-add ~/.ssh/id_ed25519` |
| Show public SSH key | `cat ~/.ssh/id_ed25519.pub` |
| Test GitHub SSH | `ssh -T git@github.com` |
| Change to SSH remote | `git remote set-url origin git@github.com:USERNAME/REPO.git` |
| Verify remote URL | `git remote -v` |
| Check GitHub auth | `gh auth status` |
| View pull request | `gh pr view <pr-number>` |
| Check PR status | `gh pr status` |
| Merge PR | `gh pr merge <pr-number>` |
| View issue | `gh issue view <issue-number>` |
| Close issue | `gh issue close <issue-number>` |

---

## Key command explanations and aliases

### SSH setup and authentication

```bash
ssh -V
# Check SSH version installed

ssh-keygen -t ed25519 -C "your_email@example.com"
# Generate a new ED25519 SSH key pair
# Creates:
#   - Private key: ~/.ssh/id_ed25519 (keep secret!)
#   - Public key: ~/.ssh/id_ed25519.pub (add to GitHub)

eval "$(ssh-agent -s)"
# Start the SSH authentication agent
# Allows SSH to work without entering passphrase every time

ssh-add ~/.ssh/id_ed25519
# Add private SSH key to the running agent
# After this, SSH authentication works automatically

cat ~/.ssh/id_ed25519.pub
# Display your public SSH key
# Copy this and add to GitHub → Settings → SSH and GPG keys
```

### Test GitHub SSH connection

```bash
ssh -T git@github.com
# Test SSH authentication with GitHub

# Success message:
# Hi USERNAME! You've successfully authenticated, but GitHub does not provide shell access.

# If it fails:
# - Make sure public key is added to GitHub
# - Check that SSH agent is running
# - Verify the private key is added to the agent
```

### Clone with SSH vs HTTPS

```bash
git clone git@github.com:USERNAME/REPOSITORY.git
# Clone using SSH
# Requires SSH keys configured
# After setup: no password needed

git clone https://github.com/USERNAME/REPOSITORY.git
# Clone using HTTPS
# Requires GitHub username and Personal Access Token (or credential manager)
# May prompt for credentials
```

### Change existing repository to SSH

```bash
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
# Change remote URL from HTTPS to SSH

git remote -v
# Verify the change worked
# Should show git@ URLs instead of https://
```

### GitHub CLI - authentication and basic commands

```bash
gh auth login
# Log in to GitHub from the terminal
# Prompts for protocol (SSH or HTTPS) and authentication method

gh auth status
# Show current authentication status

gh auth logout
# Log out from GitHub CLI
```

### GitHub CLI - Pull Requests

```bash
gh pr list
# List all pull requests in current repository

gh pr view <pr-number>
# View details of a specific PR

gh pr status
# Show status of PRs related to current branch

gh pr create
# Create a new pull request from terminal

gh pr comment <pr-number> -b "message"
# Add a comment to a PR

gh pr merge <pr-number>
# Merge a pull request
```

### GitHub CLI - Issues

```bash
gh issue list
# List all issues in current repository

gh issue view <issue-number>
# View details of a specific issue

gh issue create
# Create a new issue from terminal

gh issue comment <issue-number> -b "message"
# Add a comment to an issue

gh issue close <issue-number>
# Close an issue
```

### GitHub CLI - Repository management

```bash
gh repo list
# List your GitHub repositories

gh repo view <owner>/<repo>
# View repository details

gh repo clone <owner>/<repo>
# Clone repository using GitHub CLI

gh repo create
# Create a new repository on GitHub from terminal
```

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

## 12. SSH Authentication

### Check SSH installed
```bash
ssh -V
```
Shows the installed SSH version.
- Verify by seeing a version number like `OpenSSH_8.6p1`.

### Check existing SSH keys
```bash
ls -al ~/.ssh
```
Lists SSH files in the home directory.
- Look for `id_ed25519`, `id_rsa`, and `.pub` files.

### Check for public keys
```bash
ls ~/.ssh/*.pub
```
Lists only public key files.

---

## 13. Generate SSH Key

### Generate ED25519 key
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Creates a new ED25519 SSH key pair.
- It prompts for a filename and passphrase.
- Saves private key to `~/.ssh/id_ed25519`.
- Saves public key to `~/.ssh/id_ed25519.pub`.

---

## 14. Start SSH Agent

### Start the SSH agent
```bash
eval "$(ssh-agent -s)"
```
Starts the SSH authentication agent for the current shell session.
- The agent manages SSH keys so you don't need to type the passphrase every time.

---

## 15. Add SSH Key to Agent

### Add private key to agent
```bash
ssh-add ~/.ssh/id_ed25519
```
Adds the private SSH key to the running SSH agent.
- After this, Git operations over SSH work without entering the passphrase.

---

## 16. Display and copy SSH public key

### Show public key
```bash
cat ~/.ssh/id_ed25519.pub
```
Displays the public SSH key content.
- Copy the entire output.

### Add public key to GitHub
1. Copy the public key output
2. Go to GitHub → Settings → SSH and GPG keys
3. Click "New SSH key"
4. Paste the public key
5. Add a title and click "Add SSH key"

---

## 17. Test GitHub SSH connection

### Test SSH authentication
```bash
ssh -T git@github.com
```
Tests whether SSH authentication with GitHub works.
- Success message: `Hi USERNAME! You've successfully authenticated, but GitHub does not provide shell access.`
- If it fails, check that the public key is added to GitHub.

---

## 18. GitHub SSH URLs

### SSH URL format
```
git@github.com:USERNAME/REPOSITORY.git
```
This is the SSH-based repository URL for GitHub.

### HTTPS URL format
```
https://github.com/USERNAME/REPOSITORY.git
```
This is the HTTPS-based repository URL for GitHub.

---

## 19. Change existing repository to SSH

### Change remote URL from HTTPS to SSH
```bash
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```
Converts a repository using HTTPS to SSH authentication.

### Verify the change
```bash
git remote -v
```
Confirms the remote now uses the SSH URL.

---

## 20. GitHub SSH workflow

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
# Copy public key to GitHub Settings
ssh -T git@github.com
git clone git@github.com:USERNAME/REPOSITORY.git
git push
```

This workflow:
1. Generates an SSH key
2. Starts the SSH agent
3. Adds the key to the agent
4. Copies the public key to GitHub
5. Tests the connection
6. Clones a repo using SSH
7. Pushes changes using SSH

---

## 21. GitHub workflow with remotes and branches

```bash
git clone git@github.com:USERNAME/REPOSITORY.git
cd REPOSITORY
git status
git switch -c feature-branch
git add .
git commit -m "Add feature"
git push -u origin feature-branch
git fetch origin
git pull origin main
```

This is a typical GitHub workflow using SSH.

---

> Keep adding GitHub workflow examples and notes as you use GitHub in real projects.

