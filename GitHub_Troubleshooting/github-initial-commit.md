# GitHub Initial Commit and Push

## Problem

After creating a new Git repository locally, you want to push it to GitHub for the first time, but you’re unsure of the correct sequence of commands.

---

## Cause

A new local Git repo doesn’t have any remote configured or commits present. GitHub requires:
1. At least one commit to push
2. A configured remote (like `origin`)
3. Authentication via PAT or SSH

---

## Solution

Here are the steps for making the **initial commit** and pushing it to a new GitHub repository:

---

### 1. Initialize Git (if not already)

```bash
git init
```

### 2. Add Files to Stage

```bash
git add .
```

Or add specific files (optional):

```bash
git add README.md main.py
```

### 3. Commit the Files

```bash
git commit -m "Initial commit"
```

### 4. Add the GitHub Remote

- For HTTPS:
```bash
git remote add origin https://github.com/<username>/<repo-name>.git
```

- For SSH:
```bash
git remote add origin git@github.com:<username>/<repo-name>.git
```
- Replace `<username>` and `<repo-name>` with your actual GitHub username and repository name.

### 5. Push to GitHub

For main/master branch:

```bash
git push -u origin master
```

or

```bash
git push -u origin main
```
---

## Notes

The flag -u sets upstream tracking so you can later just use git push or git pull

Ensure the GitHub repo is created before pushing, and it's empty (no README if you're pushing an existing local repo)