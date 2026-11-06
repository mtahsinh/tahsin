# GitHub Upload & Setup Guide

A complete step-by-step guide from logging in to staging, committing, and pushing this portfolio to GitHub.

---

## 1. Authenticate with GitHub

If you haven't logged in, or if you need to switch from another account (e.g. `` to `Tahsin-Hasan`):

### A. Remove any old or expired login
```bash
gh auth logout -h github.com
```
*(Press `Y` and Enter when asked to confirm).*

### B. Log in with your GitHub account
```bash
gh auth login
```
Select the following options when prompted:
1. **What account do you want to log into?** &rarr; `GitHub.com`
2. **What is your preferred protocol for Git operations?** &rarr; `HTTPS`
3. **Authenticate Git with your GitHub credentials?** &rarr; `Yes`
4. **How would you like to authenticate GitHub CLI?** &rarr; `Login with a web browser`

Copy the 8-character code shown in the terminal, press Enter to open [github.com/login/device](https://github.com/login/device), paste the code, and confirm authorization under **`Tahsin-Hasan-1`**.

### C. Verify authentication
```bash
gh auth status
```
You should see:
```text
✓ Logged in to github.com account Tahsin-Hasan-1
```

---

## 2. Configure Git Identity

Set your commit name and email:

```bash
git config --global user.name "Tahsin-Hasan-1"
git config --global user.email "tahsin.hasan.cse@std.iu.ac.bd"
```

Verify your config:
```bash
git config --list | grep user
```

---

## 3. Git Repository Setup (If Not Already Initialized)

If the folder is not yet a Git repository, initialize and link it:

```bash
# Initialize repo (only if not already done)
git init

# Rename default branch to main
git branch -M main

# Add the remote repository
git remote add origin https://github.com/Tahsin-Hasan-1/tahsin.git
```

If the remote is already added, verify it:
```bash
git remote -v
```
It should output:
```text
origin  https://github.com/Tahsin-Hasan/tahsin.git (fetch)
origin  https://github.com/Tahsin-Hasan/tahsin.git (push)
```

If the remote is already added, verify it:
```bash
git remote -v
```
It should output:
```text
origin  https://github.com/Tahsin-Hasan/tahsin.git (fetch)
origin  https://github.com/Tahsin-Hasan/tahsin.git (push)
```

---

## 4. Check Status

See all modified, untracked, and staged files:

```bash
git status
```

---

## 5. Stage Files

Stage all changes:
```bash
git add .
```

*Or stage specific files:*
```bash
git add index.html about.html contact.html includes/ assets/
```

---

## 6. Commit Changes

Commit staged changes with a descriptive message:

```bash
git commit -m "feat: redesign portfolio with focus areas, centered mobile menu, and clean styling"
```

---

## 7. Push to GitHub

Push to the `main` branch:

```bash
git push -u origin main
```
*(For subsequent pushes, you can simply run `git push`).*

---

## 🚀 Quick Copy-Paste (Routine Updates)

Once authenticated and initialized, use this quick workflow to push future changes:

```bash
git status
git add .
git commit -m "update: site enhancements"
git push origin main
```

---

## ⚠️ Troubleshooting

| Problem | Cause | Solution |
| :--- | :--- | :--- |
| **`403 Permission to Tahsin-Hasan-1/tahsin.git denied`** | Logged into a different GitHub account | Run `gh auth logout -h github.com` then `gh auth login` with `Tahsin-Hasan` |
| **`fatal: not a git repository`** | Git not initialized in current directory | Run `git init` and `git remote add origin https://github.com/Tahsin-Hasan/tahsin.git` |
| **`Updates were rejected because the remote contains work`** | Remote has commits you don't have locally | Run `git pull origin main --rebase` then retry `git push` |
