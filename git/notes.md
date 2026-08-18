# Git Notes

`notes.md` is for your own learning notes — things you understand, explanations, mistakes, and important concepts.

## Git basics
Git is a version control system used to track changes in files over time.

It helps with:
- saving project history
- working on different branches
- collaborating with others
- undoing mistakes safely

## Repository
A repository is a Git project folder that tracks changes.

Example:
```bash
git init
```

This creates a `.git` directory and starts tracking the project.

## git status
`git status` shows what changed in the repository.

Example:
```bash
git status
```

It helps answer:
- Which files changed?
- Which files are staged?
- Which files are not tracked yet?

## git add
`git add` stages files for the next commit.

Example:
```bash
git add file.txt
git add .
```

Important idea:
- `git add` does not save history yet.
- It only prepares the files for commit.

## git commit
A commit is a saved version of the project.

Example:
```bash
git commit -m "Add login page"
```

This saves the staged changes with a message.

## Branches
A branch is an isolated line of work.

Example:
```bash
git switch -c feature-login
git branch
```

Why it matters:
- You can work on features without affecting the main branch.
- This keeps development organized.

## Merge
Merging combines changes from one branch into another.

Example:
```bash
git merge feature-login
```

This brings feature work into the current branch.

## Stash
Stash temporarily saves uncommitted work.

Example:
```bash
git stash
git stash list
git stash pop
```

Use it when you need to pause work and come back later.

## Reset and revert
These are different:
- `git reset` = undo staging or move HEAD back
- `git revert` = create a new commit that undoes a previous commit safely

Example:
```bash
git reset <file>
git revert <commit>
```

## Remote repository
A remote is a Git repository hosted elsewhere, usually on GitHub.

Examples:
```bash
git remote -v
git remote add origin <repository-url>
git push -u origin main
```

This connects the local repo to a remote server and uploads changes.

## Pull and fetch
- `git pull` = download and merge remote changes
- `git fetch` = download remote changes without merging

Example:
```bash
git pull
git fetch
```

## GitHub workflow
The usual flow is:
1. Create or clone a repository
2. Make changes
3. Check status
4. Add files
5. Commit changes
6. Push to remote
7. Open a pull request

Example:
```bash
git status
git add .
git commit -m "Update project"
git push origin main
```

## Important habit
For every command, ask:
- What does it do?
- Why do I need it?
- What changes in the repo?
- How do I verify the result?

Example:
```bash
git status
```

This is not just a command to memorize. It tells me the current state of the repo before I commit or push anything.

## My learning summary
Git is easier to understand when I use it in a real project and check the result with `git status`, `git log`, and `git diff`. I should learn the purpose of each command instead of memorizing commands without context.
