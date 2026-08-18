# DevOps Learning

This repository is organized as a structured learning path for core DevOps topics, starting with Linux, Git, GitHub, and Replit before moving into cloud storage, containers, and infrastructure automation.

## 1. Linux

### Topics covered

```
Linux
├── Files & directories (ls, cd, mkdir, cp, mv, rm)
├── Permissions & ownership (chmod, chown, ls -l)
├── Users & groups (whoami, id, sudo)
├── Processes (ps, top, pgrep)
├── Services & systemd (systemctl status, start, enable)
├── Packages (apt update, apt upgrade, apt install)
├── Disk / memory / CPU (df, du, free, lscpu, nproc)
├── Networking (ip, ping, ss, netstat)
├── SSH (ssh, ssh-keygen, ssh-copy-id)
├── Logs (journalctl, tail, /var/log/)
├── Pipes & redirection (|, >, >>, 2>, 2>&1)
├── Environment variables (export, unset, echo $VAR)
├── PATH (which, command -v)
├── Searching files (grep, grep -r, grep -i)
├── Finding files (find, find -type, find -size)
├── HTTP requests (curl, curl -I, curl -O, wget)
├── Archives (tar -cvf, tar -xvf, tar -czvf)
├── Cron scheduling (crontab -l, crontab -e)
└── Bash scripting (variables, if, for loops, chmod +x)
```

## 2. Git

### Topics covered

```
Git
├── Initialize & clone (git init, git clone, git clone SSH/HTTPS)
├── Status & tracking (git status, git add, git add .)
├── Committing (git commit, git commit -m, git commit -am)
├── History (git log, git log --oneline, git show)
├── Comparing (git diff, git diff --staged)
├── Branches (git branch, git switch, git switch -c)
├── Deleting branches (git branch -d, git branch -D)
├── Merging (git merge, merge conflicts)
├── Stashing (git stash, git stash pop, git stash list)
├── Undoing changes (git restore, git restore --staged, git revert, git reset)
├── Remote repositories (git remote -v, git remote add, git remote set-url)
├── Fetching (git fetch, git fetch origin)
├── Pulling (git pull)
├── Pushing (git push, git push -u, git push --set-upstream)
├── Remote branches (git branch -r, git branch -a)
├── Tags (git tag, git tag v1.0.0, git push origin v1.0.0)
├── .gitignore
└── SSH vs HTTPS clone
```

## 3. GitHub

### Topics covered

```
GitHub
├── Repository basics
│   ├── Clone repository
│   ├── Create repository
│   └── Remote configuration (git remote add origin, git remote -v)
├── Push & Pull workflow
│   ├── Push commits (git push)
│   ├── Push with upstream (git push -u origin main)
│   ├── Pull updates (git pull)
│   └── Fetch without merge (git fetch)
├── Branches on GitHub
│   ├── Create branch (git switch -c)
│   ├── Push branch (git push -u origin feature)
│   ├── List branches (git branch -r, git branch -a)
│   └── Delete remote branch (git push origin --delete)
├── SSH Authentication
│   ├── SSH keys (ssh-keygen, id_ed25519, id_ed25519.pub)
│   ├── SSH Agent (ssh-agent, ssh-add)
│   ├── Test SSH (ssh -T git@github.com)
│   ├── SSH vs HTTPS URLs
│   └── Change remote to SSH (git remote set-url)
├── GitHub Authentication
│   ├── HTTPS with token (Personal Access Token)
│   ├── SSH key pairs (private & public)
│   └── Authentication workflow
├── Pull Requests
│   ├── Create PR (gh pr create)
│   ├── Review PR (gh pr view)
│   ├── Merge PR (gh pr merge)
│   └── PR comments (gh pr comment)
├── Issues
│   ├── Create issue (gh issue create)
│   ├── View issue (gh issue view)
│   ├── Close issue (gh issue close)
│   └── Issue comments (gh issue comment)
├── Forking & Contributing
│   ├── Fork repository
│   ├── Clone fork
│   └── Pull request to original repo
├── Repository management
│   ├── List repos (gh repo list)
│   ├── View repo details (gh repo view)
│   └── Create repo (gh repo create)
├── GitHub CLI (gh)
│   ├── Authentication (gh auth login, gh auth status)
│   └── Terminal-based workflows
├── README & documentation
│   ├── README.md best practices
│   └── Project documentation
└── Security
    ├── SSH keys security
    ├── Token security
    └── Repository access control
```

## 4. Bitbucket
- repositories
- clone / push / pull
- branches
- pull requests
- basic collaboration
- learn after Git + GitHub basics

## 5. Replit
- Projects
- Git/GitHub integration
- Running applications
- Deployment basics

## 6. Cloud storage
- AWS S3 / object storage
- Cloud basics and storage concepts
- Learn it as a separate cloud topic, not as part of Git or Github

## 7. Advanced path
- Docker
- CI/CD
- AWS
- Kubernetes
- Terraform
- Monitoring

---

## Folder structure

```text
devops-learning
├── linux/
│   ├── README.md
│   ├── commands.md
│   └── notes.md
├── git/
│   ├── README.md
│   ├── commands.md
│   └── notes.md
├── github/
│   ├── README.md
│   ├── commands.md
│   └── notes.md
├── bitbucket/
│   ├── README.md
│   ├── commands.md
│   └── notes.md
├── replit/
│   ├── README.md
│   ├── commands.md
│   └── notes.md
│
└── README.md
```

## Repository goals
- Build a practical command reference for Linux and Git
- Learn collaboration with GitHub and Git hosting basics
- Practice deployment and project hosting with GitHub/Bitbucket/Replit
- Learn cloud storage and cloud concepts as a separate topic
- Prepare for container and infrastructure topics

## Suggested order
1. Linux fundamentals
2. Git basics and version control
3. GitHub workflows and collaboration
4. Bitbucket basics and comparison
5. Replit projects and deployment basics
6. Cloud storage fundamentals (AWS S3 and object storage)
7. Docker, CI/CD, AWS, Kubernetes, Terraform, and Monitoring

### Learning order

```text
Linux
  ↓
Git
  ↓
GitHub
  ↓
Bitbucket
  ↓
Replit
  ↓
Cloud storage
  ↓
Docker
  ↓
CI/CD
```
