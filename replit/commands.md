# Replit Commands

## Useful quick reference

| Goal | Command |
|---|---|
| Check CLI version | `replit --version` |
| Log in | `replit login` |
| Log out | `replit logout` |
| Create project | `replit create` |
| List projects | `replit list` |
| Clone project | `replit clone <url>` |
| Run project | `replit run` |
| Check Git status | `git status` |
| Stage changes | `git add .` |
| Commit changes | `git commit -m "message"` |
| Push to GitHub | `git push` |
| Pull from GitHub | `git pull` |
| Show current directory | `pwd` |
| List files | `ls` |
| Change directory | `cd <directory>` |
| Create directory | `mkdir <directory>` |
| Create file | `touch <file>` |
| Display file contents | `cat <file>` |

---

## Core learning rule
For every Replit command, understand:
- What is it?
- Why do I need it?
- What does it change?
- How do I verify it?

Example:

```bash
replit run
```

Break it down:

> `replit` → the Replit CLI  
> `run` → starts or executes the current project  
> It does not create code; it runs the current app in the Replit environment

This is important because Replit CLI features can change over time.

---

## 1. Replit CLI

### `replit --version`
```bash
replit --version
```
Checks whether the Replit CLI is installed.
- What is it? A version check.
- Why do I need it? To confirm the CLI is available.
- What does it change? Nothing.
- How do I verify it? It prints a version number.

---

## 2. Authentication

### `replit login`
```bash
replit login
```
Logs into your Replit account.
- Why do I need it? To access your projects and account settings.
- Verify by checking that the terminal shows a successful login.

### `replit logout`
```bash
replit logout
```
Logs out of Replit.
- It ends the current authenticated session.

---

## 3. Projects and Repls

### `replit create`
```bash
replit create
```
Creates a new Replit project.
- Why do I need it? To start a new project quickly.
- Verify by seeing the new project in your Replit workspace.

### `replit list`
```bash
replit list
```
Lists your Replit projects.
- Good for checking what you have available.

### `replit clone <url>`
```bash
replit clone <url>
```
Clones a project from a Replit URL.
- Verify by checking that the project directory appears.

---

## 4. Run a project

### `replit run`
```bash
replit run
```
Runs the current project.
- Why do I need it? To start the app or service in Replit.
- Verify by checking the terminal output and app behavior.

---

## 5. Replit + Git/GitHub workflow

### `git status`
```bash
git status
```
Shows the current Git state of the project.
- Why do I need it? To see local changes before committing.
- Verify by checking the modified files.

### `git add .`
```bash
git add .
```
Stages all current project changes.
- It prepares everything for a commit.

### `git commit -m "message"`
```bash
git commit -m "message"
```
Creates a Git commit with a message.
- Why do I need it? To save changes in the repository history.
- Verify with `git log --oneline`.

### `git push`
```bash
git push
```
Pushes local commits to GitHub.
- Verify by checking GitHub to see the new changes.

### `git pull`
```bash
git pull
```
Downloads and merges updates from GitHub.
- Useful to sync the project with the remote repository.

---

## 6. Replit Shell basics

### `pwd`
```bash
pwd
```
Shows the current directory.

### `ls`
```bash
ls
```
Lists files and folders.

### `cd <directory>`
```bash
cd <directory>
```
Changes the current directory.

### `mkdir <directory>`
```bash
mkdir <directory>
```
Creates a new folder.

### `touch <file>`
```bash
touch <file>
```
Creates a new empty file.

### `cat <file>`
```bash
cat <file>
```
Displays the contents of a file.

---

## 7. Real-world Replit workflow

```bash
git status
git add .
git commit -m "Update project"
git push
replit run
```

This is a simple and practical Replit workflow:
1. write code
2. run the project
3. check git status
4. commit changes
5. push to GitHub
6. verify the app behavior

---

> Important: Replit CLI commands and features can change, so only document commands you actually use and understand in your project.
