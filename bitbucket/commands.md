# Bitbucket Commands

## Useful quick reference

| Goal | Command |
|---|---|
| Clone repo | `git clone <repository-url>` |
| Check status | `git status` |
| Add file | `git add <file>` |
| Add all changes | `git add .` |
| Commit changes | `git commit -m "message"` |
| Push to remote | `git push` |
| Pull updates | `git pull` |
| List branches | `git branch` |
| Create branch | `git branch <branch-name>` |
| Switch branch | `git switch <branch-name>` |
| Create + switch | `git switch -c <branch-name>` |
| Merge branch | `git merge <branch-name>` |
| View remotes | `git remote -v` |
| Add remote | `git remote add origin <repository-url>` |

---

## Core learning rule
For every Bitbucket-related step, understand:
- What is it?
- Why do I need it?
- What does it change?
- How do I verify it?

Example:

```bash
git push
```

Break it down:

> `git` → version control tool  
> `push` → upload your local commits to the remote repo  
> The remote repo might be Bitbucket, GitHub, or another host

Then verify in Bitbucket by checking the branch or commit history.

---

## 1. Clone a repository

### `git clone`
```bash
git clone <repository-url>
```
Downloads an existing repository to your machine.
- What is it? A copy of a remote repository.
- Why do I need it? To start working on the project locally.
- What does it change? Creates a local working folder.
- How do I verify it? Run `git status` inside the cloned folder.

---

## 2. Check repository state

### `git status`
```bash
git status
```
Shows modified, staged, and untracked files.
- Why do I need it? To know what changed before committing.
- Verify by checking the output after changes are made.

---

## 3. Stage and commit changes

### `git add`
```bash
git add <file>
git add .
```
Adds changes to the staging area.
- What does it change? It prepares files for the next commit.
- Verify with `git status`.

### `git commit`
```bash
git commit -m "message"
```
Creates a new commit with a message.
- Why do I need it? To save changes in the repository history.
- Verify with `git log --oneline`.

---

## 4. Push and pull

### `git push`
```bash
git push
```
Uploads local commits to the remote repository on Bitbucket.
- Verify by checking the branch and commit history in Bitbucket.

### `git pull`
```bash
git pull
```
Downloads and merges remote changes into the current branch.
- Why do I need it? To stay in sync with the remote repo.
- Verify with `git status` and checking the updated files.

---

## 5. Branch workflow

### `git branch`
```bash
git branch
```
Lists local branches.

### `git switch -c <branch-name>`
```bash
git switch -c <branch-name>
```
Creates and switches to a new branch.
- Why do I need it? To work on a feature safely.
- Verify with `git branch`.

### `git merge <branch-name>`
```bash
git merge <branch-name>
```
Combines changes from another branch into the current one.
- Verify by checking the resulting branch state and files.

---

## 6. Remote repository basics

### `git remote -v`
```bash
git remote -v
```
Shows the remote URLs connected to the repo.
- It helps confirm Bitbucket is configured correctly.

### `git remote add origin <repository-url>`
```bash
git remote add origin <repository-url>
```
Connects the local repo to a Bitbucket repository.
- Verify by running `git remote -v` again.

---

## 7. Basic Bitbucket workflow

```bash
git clone <repository-url>
git status
git add .
git commit -m "Add feature"
git push
git pull
```

This is the core Git + Bitbucket flow:
1. clone repo
2. make changes
3. check status
4. stage + commit
5. push to Bitbucket
6. pull updates when needed

---

> Bitbucket is not a different kind of Git. It is a Git hosting platform with a similar workflow to GitHub. Learn Git well first, then learn the platform differences.
