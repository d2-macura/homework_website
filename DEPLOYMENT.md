# Deployment Guide - GitHub Pages

This guide explains how to deploy the Macura Dorothy portfolio website to GitHub Pages.

---

## What is GitHub Pages?

GitHub Pages is a **free** hosting service from GitHub. It takes your HTML, CSS, and image files and publishes them as a real website that anyone can visit!

**Think of it like this:** Your code files are like a recipe, and GitHub Pages is like a restaurant that cooks the recipe and serves it to visitors!

---

## Prerequisites

Before you start, make sure you have:

1. **A GitHub account** - Sign up at [github.com](https://github.com)
2. **Git installed** - Download from [git-scm.com](https://git-scm.com)
3. **GitHub CLI (optional but helpful)** - Download from [cli.github.com](https://cli.github.com)

---

## Step-by-Step Deployment

### Step 1: Initialize Git Repository

Open your terminal in the project folder and run:

```bash
# Initialize a new Git repository
git init

# Add all files to staging
git add .

# Create your first commit
git commit -m "Initial commit: Portfolio website with responsive hero image"
```

**What does this do?**
- `git init` - Creates a hidden `.git` folder that tracks your changes
- `git add .` - Tells Git "I want to save ALL these files"
- `git commit` - Creates a snapshot of your files (like saving a game!)

---

### Step 2: Create a GitHub Repository

**Option A: Using GitHub Website**

1. Go to [github.com](https://github.com) and log in
2. Click the **"+"** button in the top right → **"New repository"**
3. Fill in the details:
   - **Repository name:** `macura-dorothy-portfolio` (or any name you want)
   - **Description:** "Professional portfolio website for Macura Dorothy"
   - **Public/Private:** Choose Public (required for free GitHub Pages)
   - **Do NOT** initialize with README (we already have files!)
4. Click **"Create repository"**
5. GitHub will show you commands - copy the ones under "push an existing repository"

**Option B: Using GitHub CLI**

```bash
# Create repository and push in one command
gh repo create macura-dorothy-portfolio --public --source=. --push
```

---

### Step 3: Push Your Code to GitHub

If you used Option A (website), run these commands:

```bash
# Connect your local repository to GitHub
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git

# Rename default branch to "main" (GitHub's standard)
git branch -M main

# Push your code to GitHub!
git push -u origin main
```

**Replace:**
- `YOUR-USERNAME` with your GitHub username
- `YOUR-REPO-NAME` with your repository name

---

### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub.com
2. Click **"Settings"** (gear icon in the top menu)
3. In the left sidebar, scroll down and click **"Pages"**
4. Under **"Build and deployment"**:
   - **Source:** Select **"GitHub Actions"**

   ⚠️ **Important:** Do NOT select "Deploy from a branch" - we use GitHub Actions!

5. Click **"Save"** if prompted

---

### Step 5: Watch the Deployment

1. Go to the **"Actions"** tab in your repository
2. You should see a workflow running called "Deploy to GitHub Pages"
3. Click on it to watch the progress
4. Green checkmark ✅ = Success!
5. Red X ❌ = Something went wrong (check the logs)

---

### Step 6: Visit Your Live Website!

Once deployment is complete, your website is live at:

```
https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/
```

**Example:** If your username is `macuradot` and repo is `portfolio`:
```
https://macuradot.github.io/portfolio/
```

---

## How to Update Your Website

After making changes to your files:

```bash
# See what files changed
git status

# Add your changes
git add .

# Create a commit with a description
git commit -m "Updated hero image styling"

# Push to GitHub (triggers automatic deployment!)
git push
```

**That's it!** GitHub will automatically rebuild and redeploy your website!

---

## Troubleshooting

### Problem: "404 - Page not found"

**Solutions:**
1. Wait 5-10 minutes - first deployment can be slow
2. Make sure you have an `index.html` file in the root folder
3. Check that Pages is set to "GitHub Actions" not "Branch"

### Problem: Deployment failed

**Solutions:**
1. Go to Actions tab and click on the failed workflow
2. Read the error message - it usually tells you what's wrong
3. Common issues:
   - Missing files referenced in HTML
   - Syntax errors in workflow file

### Problem: Images not loading

**Solutions:**
1. Check file paths are correct (case-sensitive!)
   - `assets/Model_Portrait.jpg` ≠ `assets/model_portrait.jpg`
2. Make sure images are committed to Git
3. Use relative paths like `assets/image.jpg` not `/assets/image.jpg`

### Problem: CSS not updating

**Solutions:**
1. Hard refresh your browser: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)
2. Clear browser cache
3. Wait a few minutes for GitHub's cache to update

---

## Custom Domain (Optional)

Want to use your own domain like `macuradot.com`?

1. Buy a domain from a registrar (Namecheap, GoDaddy, etc.)
2. In GitHub Pages settings, enter your custom domain
3. Add DNS records at your domain registrar:
   - Type: `CNAME`
   - Host: `www`
   - Value: `YOUR-USERNAME.github.io`

---

## Project Structure

```
homework_website/
├── .github/
│   └── workflows/
│       └── deploy.yml      # Automatic deployment instructions
├── assets/
│   └── model_portrait.jpg  # Hero background image
├── index.html              # Home page
├── portfolio.html          # Portfolio page
├── report.html             # Report page
├── contact.html            # Contact page
├── style.css               # All styles (with detailed comments!)
├── .gitignore              # Files Git should ignore
└── DEPLOYMENT.md           # This file!
```

---

## Need Help?

- **GitHub Pages Documentation:** https://docs.github.com/en/pages
- **GitHub Actions Documentation:** https://docs.github.com/en/actions
- **Git Tutorial:** https://git-scm.com/book/en/v2

---

Happy deploying! 🚀
