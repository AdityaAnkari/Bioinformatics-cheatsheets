# 🛠️ Git Basics for Bioinformatics Projects

**Git** is a version control system that helps you track changes in your code, scripts, or data files over time.

When used with **GitHub**, it becomes a powerful way to:

- 🔄 Keep backups of your work
- 🤝 Collaborate with teammates
- 🧪 Reproduce and document your bioinformatics analyses
- 📊 Share tools, pipelines, and results with the world

---

## 🧾 What Is This Page?

This cheatsheet teaches you the most important Git commands for everyday use. You’ll learn to:

- Create and clone repositories
- Track file changes
- Commit edits with messages
- Push and pull from GitHub
- Fix common Git mistakes

Written for **absolute beginners** — no coding or CS background needed.

---

## 🧪 What You Need First

✅ You should already have:

- A **GitHub account**: [https://github.com](https://github.com)
- Git installed: Check with `git --version`
  - Install on Linux: `sudo apt install git`
  - Install on macOS: `brew install git`
  - Install on Windows: Use Git Bash → [https://git-scm.com/downloads](https://git-scm.com/downloads)

---

## 🔧 Set Up Git (First Time Only)

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"


📁 Create a New Local Git Project
```bash

mkdir my_project
cd my_project
git init

This creates a hidden .git folder to track everything.

🔄 Clone an Existing GitHub Repo
To copy a remote repo to your computer:

```bash

git clone https://github.com/username/repo-name.git
cd repo-name

This is how you'll start working on shared projects or use open-source pipelines.

📌 Track & Save File Changes
```bash

# Check current status
git status

# Add a specific file
git add script.py

# Add ALL files
git add .

# Commit with a message
git commit -m "Add alignment script for bwa"

Now your changes are saved in Git history (but not yet pushed to GitHub).


🚀 Push to GitHub
```bash

# First push (set upstream)
git push -u origin main

# Later pushes
git push

Make sure you've created a GitHub repo and connected it to your local folder.


🔁 Pull Updates from GitHub
```bash

git pull

Use this to download the latest changes others have made (if collaborating).

🧠 Check Project History
```bash

git log

Press q to quit the log view.

❌ Undoing Mistakes (Common Fixes)

| Problem               | Command                         |
| --------------------- | ------------------------------- |
| Unstage a file        | `git restore --staged filename` |
| Discard local changes | `git checkout -- filename`      |
| View differences      | `git diff`                      |
| Reset last commit     | `git reset --soft HEAD~1`       |

🧠 Don’t panic — Git is very forgiving once you learn how to “go back in time.”

🧪 Example Workflow (Real-Life Use)
```bash

git clone https://github.com/adityaankari/bioinformatics-cheatsheets.git
cd bioinformatics-cheatsheets

# Make changes to bwa.md
nano alignment/bwa.md

# Save and commit
git add alignment/bwa.md
git commit -m "Update BWA section with extra tips"
git push

Now the changes are visible on GitHub!

💡 Git Tips for Bioinformaticians

| Tip                         | Why It Matters                            |
| --------------------------- | ----------------------------------------- |
| Commit often                | Small commits = easier to undo            |
| Write clear commit messages | Helpful for you & others                  |
| Use `.gitignore`            | Avoid pushing huge `.bam`, `.fastq` files |
| Backup often (push)         | Cloud copy in case laptop crashes         |
| Use GitHub issues           | Track bugs, TODOs, notes                  |
| Use branches                | For experimental or risky changes         |


📁 .gitignore (Optional)
Create a .gitignore file to exclude unnecessary files:

markdown

*.bam
*.fastq
*.log
*.zip
*.DS_Store

📚 Learn More
Pro Git Book (Free) (https://git-scm.com/book/en/v2)

GitHub Docs (https://docs.github.com/)

Git Cheat Sheet PDF (https://education.github.com/git-cheat-sheet-education.pdf)

✅ Final Summary

| Task              | Command                                    |
| ----------------- | ------------------------------------------ |
| Init new project  | `git init`                                 |
| Clone repo        | `git clone URL`                            |
| Track changes     | `git add filename` or `git add .`          |
| Save with message | `git commit -m "message"`                  |
| Push to GitHub    | `git push`                                 |
| Pull updates      | `git pull`                                 |
| View history      | `git log`                                  |
| Fix mistakes      | `git restore`, `git reset`, `git checkout` |

👨‍🔬 Git isn’t just for programmers — it’s a bioinformatician’s best friend.
Learn it once, use it forever.










