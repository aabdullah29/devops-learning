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

---

## GitHub Authentication

### HTTPS vs SSH

**HTTPS:**
```
https://github.com/USERNAME/REPOSITORY.git
```
- Uses username/token for authentication
- Works behind most firewalls
- Requires entering credentials (or using credential manager)
- GitHub no longer accepts account passwords; use Personal Access Token (PAT)

**SSH:**
```
git@github.com:USERNAME/REPOSITORY.git
```
- Uses SSH key pair for authentication
- Requires SSH keys to be set up
- No need to enter password after key is added to agent
- Requires SSH access (may not work behind some firewalls)

### SSH key pair

A key pair has two parts:

**Private key:**
```
~/.ssh/id_ed25519
```
- Kept secret on your machine
- Used to authenticate with GitHub
- NEVER share this

**Public key:**
```
~/.ssh/id_ed25519.pub
```
- Shared with GitHub
- GitHub stores it and recognizes your private key
- SAFE to share

### SSH Agent

The SSH agent is a service that keeps your private key available so you don't need to enter the passphrase every time.

Flow:
```
My Computer
    ↓
SSH Agent (holds private key)
    ↓
GitHub (verifies public key)
    ↓
Authenticated
```

### Authentication workflow

1. Generate SSH key pair
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

2. Start SSH agent
   ```bash
   eval "$(ssh-agent -s)"
   ```

3. Add private key to agent
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

4. Copy public key to GitHub
   ```bash
   cat ~/.ssh/id_ed25519.pub
   # Copy to GitHub Settings → SSH and GPG keys
   ```

5. Test connection
   ```bash
   ssh -T git@github.com
   ```

6. Use SSH for Git operations
   ```bash
   git clone git@github.com:USERNAME/REPOSITORY.git
   git push
   git pull
   ```

### Fetch vs Pull

I often confuse these, so here's the distinction:

**Fetch:**
```bash
git fetch
```
- Downloads remote changes
- Does NOT automatically change your local files
- Safe to do before knowing what changed
- Verify with `git log HEAD..origin/main --oneline`

**Pull:**
```bash
git pull
```
- Fetch + merge
- Downloads AND integrates remote changes
- Updates your local branch
- Used when you want to sync up

### Remote configuration

Check your remote:
```bash
git remote -v
```

Output should show:
```
origin  git@github.com:USERNAME/REPOSITORY.git (fetch)
origin  git@github.com:USERNAME/REPOSITORY.git (push)
```

If it shows HTTPS, change to SSH:
```bash
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```

---

## My learning summary
GitHub is where the Git workflow becomes collaborative. The important part is not memorizing every Git command, but understanding the repository flow: clone, branch, commit, push, pull request, review, and merge.

For authentication, I learned that SSH is more secure and convenient than HTTPS once set up. The SSH agent keeps my private key available so I don't need to enter a passphrase every time.
