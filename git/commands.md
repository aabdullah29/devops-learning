# Git Commands

## Repository setup
```bash
git init
git clone https://github.com/user/repo.git
```

## Status and tracking
```bash
git status
git add file.txt
git add .
git commit -m "Add feature"
```

## History and comparison
```bash
git log
git log --oneline
git diff
git diff HEAD
```

## Branching
```bash
git branch
git checkout -b feature-branch
git checkout main
git merge feature-branch
```

## Stash and recovery
```bash
git stash
git stash list
git stash pop
git reset --hard HEAD~1
git revert HEAD
```

## Ignore files
```bash
printf "node_modules/\n.env\n" > .gitignore
```

## Remote syncing
```bash
git remote -v
git push origin main
git pull origin main
```
