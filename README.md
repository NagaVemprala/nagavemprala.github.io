
```markdown
# Git Cheat Sheet & Workflow Guide

This repository contains the source code for **nagavemprala.github.io**. Below is a step-by-step guide on how to clone this repository to a local Windows machine, make changes, and push them back to GitHub[cite: 1].

---

## 🚀 First-Time Setup

### 1. Set Up Your Identity
Before making your first commit, tell Git who you are so your contributions link correctly to your GitHub profile. Open **Git Bash** and run[cite: 1]:

```bash
# Set your global commit name
git config --global user.name "Your Name"

# Set your global commit email
git config --global user.email "your.email@example.com"

```

### View All Configuration Settings
To list every single configuration setting Git can find on your system (including system-wide, user-specific, and repository-specific settings), run:

```bash
git list --config
```

### View Only the Settings and Where They Come From
Since settings can be configured globally (for your whole computer) or locally (just for the current project folder), it's incredibly helpful to see where each setting is stored. Run:

```bash
git config --list --show-origin
```

This will print the file path next to each setting, showing you exactly which file is controlling that behavior.

### Check a Specific Setting
If you just want to verify a single detail—like ensuring your username or email is set up correctly without digging through a massive list—you can ask for it specifically:

```bash
git config user.name
```



### 2. Clone the Repository

Download a complete local copy of this repository to your computer:

```bash
# Navigate to your preferred projects directory (e.g., C:/Projects)
cd /c/Projects

# Clone the repository
git clone [https://github.com/NagaVemprala/nagavemprala.github.io.git](https://github.com/NagaVemprala/nagavemprala.github.io.git)

# Move into the project directory
cd nagavemprala.github.io

```

---

## 🛠️ Daily Development Workflow

Whenever you want to update your project, follow this standard cycle:

### Step 1: Make Your Changes

Open the project folder in your favorite code editor (e.g., VS Code or Claude Code) and modify, add, or delete files as needed.

### Step 2: Check What Changed

See exactly which files Git detects have been modified, added, or deleted:

```bash
git status

```

* 🔴 **Red files:** Changes exist locally but are not yet tracked ("unstaged").



### Step 3: Stage Your Changes

Select the files you want to include in your next snapshot.

```bash
# Stage ALL modified and new files in the current folder
git add .

# (Optional) Stage a specific file or folder instead of everything:
# git add folder-name/filename.ext

```

* 🟢 Running `git status` again will now show the files in **green**, meaning they are ready to be saved.



### Step 4: Commit Your Changes

Save a snapshot of your staged changes locally with a clear, descriptive message explaining *what* you changed:

```bash
git commit -m "feat: update website layout and structure"

```

### Step 5: Push to GitHub

Upload your local snapshot back to the remote repository on GitHub:

```bash
git push origin main

```

> **Note:** If Windows prompts you with a **Git Credential Manager** pop-up, choose **"Sign in with your browser"** to authorize your account. This is a one-time setup.
> 
> 

---

## 💡 Quick Reference Summary Table

| Command | What it does |
| --- | --- |
| `git status` | Shows modified, untracked, or staged files.
| `git add .` | Stages all current changes for the next commit.
| `git commit -m "msg"` | Saves a local snapshot of your staged changes.
| `git push origin main` | Uploads all local commits to the live GitHub repository.
| `git pull origin main` | Downloads and merges the latest updates from GitHub to your local machine.

```

