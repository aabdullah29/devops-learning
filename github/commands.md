# GitHub Commands

## Repository basics
```bash
git remote -v
git push origin main
git pull origin main
```

## Branch workflow
```bash
git checkout -b feature-name
git push -u origin feature-name
git checkout main
```

## Pull Requests
- Open a pull request from a feature branch to main
- Review code changes and comments
- Merge after approval

## Issues
- Create a bug report or task
- Assign labels and milestones
- Track progress and close when resolved

## README
```md
# Project Name

Short description of the project
## Features
## Installation
## Usage
```

## GitHub Actions (later)
```yaml
name: CI
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Hello from GitHub Actions"
```
