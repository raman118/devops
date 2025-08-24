# GitHub Repository Creation and Git Commands

## Table of Contents
1. [Git vs GitHub](#git-vs-github)
2. [Prerequisites](#prerequisites)
3. [Method 1: Using GitHub CLI](#method-1-using-github-cli-recommended)
4. [Method 2: Manual Method](#method-2-manual-method)
5. [Essential Git Commands](#essential-git-commands)
6. [Git Workflow](#git-workflow)
7. [Remote Operations](#remote-operations)
8. [Branch Management](#branch-management)
9. [Common Issues and Solutions](#common-issues-and-solutions)
10. [Best Practices](#best-practices)

## Git vs GitHub

### Git
- **Version control system** that runs locally on your computer
- Tracks changes in files and folders
- Works completely offline
- Created by Linus Torvalds

### GitHub
- **Cloud-based hosting service** for Git repositories
- Provides web interface for Git repositories
- Adds collaboration features (issues, pull requests, etc.)
- Stores your code in the cloud

### Key Concept: Remote Origin
- **Remote Origin** = Connection between your local Git repository and GitHub repository
- Think of it as a bridge between your computer and GitHub
- Without remote origin, your code stays only on your local machine

## Prerequisites

### Required Software
```bash
# Check if Git is installed
git --version

# Check if GitHub CLI is installed
gh --version
```

### Installation Links
- **Git**: https://git-scm.com/downloads
- **GitHub CLI**: https://cli.github.com/
- **Git Bash**: Comes with Git installation on Windows

## Method 1: Using GitHub CLI (Recommended)

### Step 1: Install and Setup GitHub CLI
```bash
# Install GitHub CLI (download from https://cli.github.com/)

# Login to GitHub
gh auth login
```
Follow the authentication process:
1. Choose "GitHub.com"
2. Choose "HTTPS" or "SSH"
3. Choose "Login with a web browser"
4. Copy the code and paste in browser

### Step 2: Create Repository with Files
```bash
# Navigate to your project folder
cd /path/to/your/project

# Initialize Git repository
git init

# Add all files to staging area
git add .

# Create initial commit
git commit -m "Initial commit: Added project files"

# Create GitHub repository and push everything
gh repo create your-repo-name --public --push

# Alternative: Create private repository
gh repo create your-repo-name --private --push
```

### Step 3: Verify Repository Creation
```bash
# Check remote origin
git remote -v

# View repository in browser
gh repo view --web
```

## Method 2: Manual Method

### Step 1: Create Repository on GitHub.com
1. Go to **GitHub.com**
2. Click **"New repository"** or **"+"** → **"New repository"**
3. Enter repository name (e.g., "devops")
4. Choose **Public** or **Private**
5. **Don't check** "Initialize this repository with a README"
6. Click **"Create repository"**

### Step 2: Connect Local Repository to GitHub
```bash
# Navigate to your project folder
cd /path/to/your/project

# Initialize Git repository (if not already done)
git init

# Add remote origin (replace with your repository URL)
git remote add origin https://github.com/your-username/your-repo-name.git

# Check if remote is added correctly
git remote -v
```

### Step 3: Add Files and Push
```bash
# Add all files to staging area
git add .

# Create initial commit
git commit -m "Initial commit: Added project files"

# Push to GitHub (first time)
git push -u origin main

# For subsequent pushes
git push origin main
```

## Essential Git Commands

### Repository Initialization
```bash
git init                    # Initialize new Git repository
git clone <repo-url>        # Clone existing repository
```

### File Operations
```bash
git status                  # Check repository status
git add filename            # Add specific file to staging
git add .                   # Add all files to staging
git add *.txt              # Add all .txt files
git reset filename         # Remove file from staging area
```

### Commit Operations
```bash
git commit -m "message"     # Commit with message
git commit -am "message"    # Add and commit in one command
git log                     # View commit history
git log --oneline          # Condensed commit history
```

### Remote Operations
```bash
git remote -v              # View remote repositories
git remote add origin <url> # Add remote repository
git remote remove origin   # Remove remote repository
git push origin main       # Push to remote repository
git pull origin main       # Pull from remote repository
git fetch origin          # Fetch changes without merging
```

## Git Workflow

### Basic Workflow
```bash
# 1. Check current status
git status

# 2. Add files to staging area
git add .

# 3. Commit changes
git commit -m "Descriptive commit message"

# 4. Push to GitHub
git push origin main
```

### Daily Development Workflow
```bash
# Start of day - get latest changes
git pull origin main

# Make changes to files
# ... edit files ...

# Check what changed
git status
git diff

# Stage changes
git add .

# Commit changes
git commit -m "Add: feature description"

# Push changes
git push origin main
```

## Remote Operations

### Adding Remote Repository
```bash
# Add remote origin
git remote add origin https://github.com/username/repo-name.git

# Verify remote
git remote -v
```

### Remote URL Formats
```bash
# HTTPS (easier for beginners)
https://github.com/username/repo-name.git

# SSH (more secure, requires SSH key setup)
git@github.com:username/repo-name.git
```

### Changing Remote URL
```bash
# Change from HTTPS to SSH
git remote set-url origin git@github.com:username/repo-name.git

# Change from SSH to HTTPS
git remote set-url origin https://github.com/username/repo-name.git
```

## Branch Management

### Working with Branches
```bash
git branch                 # List local branches
git branch -a             # List all branches (local + remote)
git branch feature-name   # Create new branch
git checkout feature-name # Switch to branch
git checkout -b feature-name # Create and switch to new branch
```

### Branch Operations
```bash
git merge feature-name    # Merge branch into current branch
git branch -d feature-name # Delete local branch
git push origin --delete feature-name # Delete remote branch
```

### Default Branch (main vs master)
[O```bash
# Check current branch
git branch

# Rename master to main (if needed)
git branch -m master main

# Push and set upstream
git push -u origin main
```

## Common Issues and Solutions

### Issue 1: Authentication Failed
```bash
# Solution 1: Use Personal Access Token
# Go to GitHub → Settings → Developer settings → Personal access tokens
# Use token as password

# Solution 2: Use GitHub CLI
gh auth login
```

### Issue 2: Remote Origin Already Exists
```bash
# Remove existing remote
git remote remove origin

# Add correct remote
git remote add origin https://github.com/username/repo-name.git
```

### Issue 3: Push Rejected (non-fast-forward)
```bash
# Pull first, then push
git pull origin main
git push origin main

# Or force push (use carefully)
git push --force origin main
```

### Issue 4: Merge Conflicts
```bash
# Pull changes
git pull origin main

# Edit conflicted files manually
# Look for <<<<<<< HEAD markers

# Add resolved files
git add .

# Commit merge
git commit -m "Resolve merge conflicts"

# Push
git push origin main
```

### Issue 5: Wrong Branch Name
```bash
# If your default branch is 'master' but GitHub expects 'main'
git push origin master

# Or rename branch
git branch -m master main
git push -u origin main
```

## Best Practices

### Commit Messages
```bash
# Good commit messages
git commit -m "Add: user authentication feature"
git commit -m "Fix: resolve login bug for mobile users"
git commit -m "Update: improve error handling in API"
git commit -m "Remove: deprecated function from utils"

# Bad commit messages
git commit -m "changes"
git commit -m "fix"
git commit -m "update"
```

### Repository Structure
```
your-repo/
├── README.md              # Project description
├── .gitignore            # Files to ignore
├── docs/                 # Documentation
├── src/                  # Source code
├── tests/                # Test files
└── notes/                # Your notes
    ├── git-notes.md
    ├── linux-notes.md
    └── devops-notes.md
```

### .gitignore File
```bash
# Create .gitignore file
touch .gitignore

# Common entries for .gitignore
*.log                     # Log files
*.tmp                     # Temporary files
node_modules/             # Node.js dependencies
.env                      # Environment variables
.DS_Store                 # macOS system files
*.pyc                     # Python compiled files
```

### Security Best Practices
- Never commit passwords or API keys
- Use environment variables for sensitive data
- Add .env files to .gitignore
- Use SSH keys for authentication
- Enable two-factor authentication on GitHub

## Quick Reference Commands

### Repository Setup
```bash
# Create new repo with GitHub CLI
gh repo create repo-name --public --push

# Manual setup
git init
git remote add origin <url>
git add .
git commit -m "Initial commit"
git push -u origin main
```

### Daily Commands
```bash
git status               # Check status
git add .               # Stage all changes
git commit -m "message" # Commit changes
git push origin main    # Push to GitHub
git pull origin main    # Get latest changes
```

### Information Commands
```bash
git log --oneline       # View commit history
git remote -v           # View remote repositories
git branch             # View branches
git diff               # View changes
```

### Troubleshooting Commands
```bash
git reset HEAD~1        # Undo last commit (keep changes)
git reset --hard HEAD~1 # Undo last commit (lose changes)
git stash              # Temporarily save changes
git stash pop          # Restore stashed changes
```

## Complete Example Workflow

### Creating a New Project
```bash
# 1. Create project directory
mkdir my-devops-project
cd my-devops-project

# 2. Create some files
echo "# My DevOps Project" > README.md
mkdir notes
echo "# Git Notes" > notes/git-notes.md

# 3. Initialize Git
git init

# 4. Add files
git add .

# 5. Initial commit
git commit -m "Initial commit: Setup project structure"

# 6. Create GitHub repository and push
gh repo create my-devops-project --public --push
```

### Adding New Files Later
```bash
# 1. Create new file
echo "# Linux Notes" > notes/linux-notes.md

# 2. Check status
git status

# 3. Add new file
git add notes/linux-notes.md

# 4. Commit
git commit -m "Add: comprehensive Linux notes for DevOps"

# 5. Push to GitHub
git push origin main
```

---

## Summary

1. **GitHub CLI method is fastest** for creating repositories
2. **Remote origin connects** your local repo to GitHub
3. **Basic workflow**: add → commit → push
4. **Always pull before pushing** in collaborative projects
5. **Use descriptive commit messages**
6. **Never commit sensitive information**

Remember: Git works locally, GitHub is the cloud storage. Remote origin is the bridge between them!
