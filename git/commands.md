# Git Commands

## Useful quick reference

| Goal | Command |
|---|---|
| Check installed Git | `git --version` |
| Set username | `git config --global user.name "Your Name"` |
| Set email | `git config --global user.email "you@example.com"` |
| View config | `git config --list` |
| Initialize repo | `git init` |
| Clone repo | `git clone <repository-url>` |
| Check status | `git status` |
| Add one file | `git add <file>` |
| Add all changes | `git add .` |
| Undo unstaged file change | `git restore <file>` |
| Commit changes | `git commit -m "message"` |
| Stage + commit tracked files | `git commit -am "message"` |
| Show history | `git log` |
| Compact log | `git log --oneline` |
| Show commit details | `git show <commit>` |
| Show unstaged changes | `git diff` |
| Show staged changes | `git diff --staged` |
| List branches | `git branch` |
| Create branch | `git branch <branch-name>` |
| Switch branches | `git switch <branch-name>` |
| Create + switch | `git switch -c <branch-name>` |
| Delete branch | `git branch -d <branch-name>` |
| Merge branch | `git merge <branch-name>` |
| Save temporary changes | `git stash` |
| List stashes | `git stash list` |
| Restore latest stash | `git stash pop` |
| Remove file from staging | `git reset <file>` |
| Revert a commit | `git revert <commit>` |
| View remotes | `git remote -v` |
| Add remote | `git remote add origin <repository-url>` |
| Remove remote | `git remote remove origin` |
| Push commits | `git push` |
| Push main & set upstream | `git push -u origin main` |
| Pull updates | `git pull` |
| Fetch without merging | `git fetch` |

---

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
> `status` → asks for the current state of the repo  
> It does not change code; it only reports what is modified, staged, or committed

This is the same learning idea as Linux: understand the command before memorizing it.

---

## 1. Check Git

### `git --version`
```bash
git --version
```
Shows the installed Git version.
- What is it? A version check command.
- Why do I need it? To confirm Git is installed and working.
- What does it change? Nothing.
- How do I verify it? It prints a version like `git version 2.39.0`.

---

## 2. Configure Git

### `git config --global user.name`
```bash
git config --global user.name "Your Name"
```
Sets the Git username for your global profile.
- What is it? A configuration command.
- Why do I need it? So commits are associated with your name.
- What does it change? Your Git identity settings.
- How do I verify it? Run `git config --global user.name`.

### `git config --global user.email`
```bash
git config --global user.email "you@example.com"
```
Sets the Git email address.
- Why do I need it? This is attached to each commit.
- Verify with `git config --global user.email`.

### `git config --list`
```bash
git config --list
```
Shows all configured Git settings.
- Useful to confirm your username and email.

---

## 3. Create / get a repository

### `git init`
```bash
git init
```
Initializes a new Git repository in the current folder.
- What is it? Creates a `.git` directory.
- Why do I need it? To start tracking files in a project.
- What does it change? It creates repository metadata.
- How do I verify it? Run `git status` and see the repo state.

### `git clone`
```bash
git clone <repository-url>
```
Downloads an existing repository from GitHub or another remote host.
- Why do I need it? To copy an existing project to my machine.
- Verify with `ls` or `git status` inside the cloned folder.

---

## 4. Check repository status

### `git status`
```bash
git status
```
Shows which files are modified, staged, or committed.
- What is it? A status report for the repository.
- Why do I need it? To know what changed before committing.
- What does it change? Nothing.
- How do I verify it? The output shows files in different states.

---

## 5. Track changes

### `git add <file>`
```bash
git add <file>
```
Adds a specific file to the staging area.
- What does it change? It prepares a file for the next commit.
- Verify with `git status`.

### `git add .`
```bash
git add .
```
Adds all current changes to the staging area.
- Why do I need it? To stage everything before committing.
- Verify with `git status`.

### `git restore <file>`
```bash
git restore <file>
```
Discards unstaged changes in a file.
- What does it change? Restores the file to its last committed version.
- How do I verify it? Check the file content or run `git status`.

---

## 6. Commit changes

### `git commit -m "message"`
```bash
git commit -m "message"
```
Saves staged changes as a commit.
- What is it? A snapshot of the project at a point in time.
- Why do I need it? To save work permanently in the repository history.
- What does it change? Creates a new commit.
- How do I verify it? Run `git log --oneline`.

### `git commit -am "message"`
```bash
git commit -am "message"
```
Stages modified tracked files and creates a commit in one step.
- It only affects already-tracked files.
- Verify with `git log --oneline`.

---

## 7. View history

### `git log`
```bash
git log
```
Shows the commit history.
- Why do I need it? To see what changed and in what order.
- Verify by reading commit messages and hashes.

### `git log --oneline`
```bash
git log --oneline
```
Shows a compact version of the commit history.
- Helpful for quick review.

### `git show <commit>`
```bash
git show <commit>
```
Shows the details of a specific commit.
- It displays the changed files and diff.

---

## 8. Compare changes

### `git diff`
```bash
git diff
```
Shows unstaged changes.
- What does it change? Nothing.
- Why do I need it? To review modifications before committing.
- Verify by checking the diff output.

### `git diff --staged`
```bash
git diff --staged
```
Shows staged changes.
- Good for reviewing the files that are ready to commit.

---

## 9. Branches

### `git branch`
```bash
git branch
```
Lists local branches.
- Verify by seeing the current branch and others.

### `git branch <branch-name>`
```bash
git branch <branch-name>
```
Creates a new branch.
- Why do I need it? To isolate work without affecting main.

### `git switch <branch-name>`
```bash
git switch <branch-name>
```
Switches to another branch.
- Verify with `git branch` or `git status`.

### `git switch -c <branch-name>`
```bash
git switch -c <branch-name>
```
Creates and switches to a new branch in one command.

### `git branch -d <branch-name>`
```bash
git branch -d <branch-name>
```
Deletes a branch after it is merged.
- Verify by checking branch list.

---

## 10. Merge

### `git merge <branch-name>`
```bash
git merge <branch-name>
```
Combines another branch into the current branch.
- Why do I need it? To bring feature work into main or another branch.
- Verify with `git status` and by checking the branch files.

---

## 11. Stash

### `git stash`
```bash
git stash
```
Temporarily saves uncommitted changes.
- Why do I need it? To pause work without losing changes.
- Verify with `git stash list`.

### `git stash list`
```bash
git stash list
```
Shows saved stashes.

### `git stash pop`
```bash
git stash pop
```
Restores the latest stash and removes it from the stash list.
- Verify with `git status`.

---

## 12. Undo changes

### `git restore <file>`
```bash
git restore <file>
```
Discards unstaged changes in a file.
- Why do I need it? To revert a file before committing.

### `git reset <file>`
```bash
git reset <file>
```
Removes a file from the staging area.
- What does it change? It unstages the file, not the file content itself.

### `git revert <commit>`
```bash
git revert <commit>
```
Creates a new commit that reverses an existing commit.
- Why do I need it? To undo changes safely without erasing history.

---

## 13. Remote repository

### `git remote -v`
```bash
git remote -v
```
Shows the remote repositories connected to the project.
- Verify by checking the URL(s) returned.

### `git remote add origin <repository-url>`
```bash
git remote add origin <repository-url>
```
Adds a remote repository to the project.
- It usually connects the local repo to GitHub.

### `git remote remove origin`
```bash
git remote remove origin
```
Removes the configured remote repository.
- Verify by running `git remote -v` again.

---

## 14. Push / pull

### `git push`
```bash
git push
```
Uploads local commits to the remote repository.
- Why do I need it? To share my work.
- Verify by checking the remote repository on GitHub.

### `git push -u origin main`
```bash
git push -u origin main
```
Pushes the `main` branch and sets the upstream branch for future pushes.
- Useful when the branch is not yet linked to a remote.

### `git pull`
```bash
git pull
```
Downloads and integrates remote changes into the current branch.
- Why do I need it? To keep your local repo updated.

### `git fetch`
```bash
git fetch
```
Downloads remote changes without merging them.
- Useful for checking if new changes exist before integrating them.

---

## 15. Git workflow example

```bash
git status
git add .
git commit -m "Add project files"
git push -u origin main
```

This is a normal basic workflow:
1. Check status
2. Stage changes
3. Commit
4. Push to remote

---

> Keep adding examples and notes as you learn more Git commands.

