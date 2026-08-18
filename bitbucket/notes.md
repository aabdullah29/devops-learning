# Bitbucket Notes

`notes.md` is for your own learning notes — things you understand, explanations, mistakes, and important concepts.

## Why Bitbucket?
Bitbucket is a platform for storing Git repositories online, just like GitHub.

Git is the tool.
GitHub and Bitbucket are hosting platforms.

## Main idea
Once Git is understood, Bitbucket is easier because the workflow is almost the same.

Typical flow:
```bash
git clone <repo-url>
git status
git add .
git commit -m "Update project"
git push
```

## Differences from GitHub
Bitbucket is similar to GitHub in most everyday workflows:
- clone repository
- create branches
- commit changes
- push updates
- open pull requests
- merge changes

The main difference is the platform itself, not the Git model behind it.

## Branches
Branches help isolate work.

Example:
```bash
git switch -c feature-login
git branch
```

This is the same idea as in GitHub.

## Pull requests and reviews
Bitbucket also supports code review and pull requests, but the interface is different from GitHub.

The important idea is still:
- work on a branch
- push branch
- open pull request
- review and merge

## Basic workflow in my own words
1. Clone project
2. Make changes
3. Check status
4. Stage files
5. Commit changes
6. Push to Bitbucket
7. Pull updates when needed

## Important habit
I should not try to learn all Git hosting platforms at once.

The order should be:
- Git first
- GitHub second
- Bitbucket later

## My learning summary
Bitbucket is not separate from Git. It is just another place to host a Git repository. If I understand Git well, Bitbucket becomes easy to learn because the workflow is almost the same.
