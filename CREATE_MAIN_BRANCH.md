# 🔧 How to Create Main Branch on GitHub

The `main` branch doesn't exist yet on GitHub, which is why you can't create a pull request. Here's how to fix it:

## Method 1: Create Main Branch from Web Interface (Easiest)

1. **Go to your repository:**
   https://github.com/jkzblog/blog

2. **Look for the branch dropdown** (top left, currently shows your branch name)
   - It's near the file list
   - Click on it

3. **Type "main" in the text field** that appears

4. **Click "Create branch: main from claude/claude-md..."**
   - GitHub will create the main branch from your current branch

5. **Done!** Now set it as default (next step)

## Method 2: Set Default Branch in Settings

1. **Go to Settings:**
   https://github.com/jkzblog/blog/settings/branches

2. **Look for "Default branch" section**

3. **Click the dropdown or "Switch default branch to another branch"**

4. **Select or create "main"**

5. **Click "Update"** and confirm

## Method 3: Use GitHub CLI (If you have gh installed)

If you have GitHub CLI installed on your machine:

```bash
# In your terminal
gh repo set-default jkzblog/blog
gh api repos/jkzblog/blog/git/refs -f ref=refs/heads/main -f sha=$(git rev-parse HEAD)
```

## After Creating Main Branch

Once `main` exists:

1. **Set it as default branch** in Settings > Branches
2. **Enable GitHub Pages:**
   - Go to: https://github.com/jkzblog/blog/settings/pages
   - Source: Select **"GitHub Actions"**
   - Save

3. **Your site will deploy automatically!**

The GitHub Actions workflow will trigger and deploy your site to:
**https://jkzblog.github.io/blog/**

## Still Having Issues?

If the branch dropdown doesn't work, try this alternative:

1. Go to: https://github.com/jkzblog/blog/branches
2. Click **"New branch"**
3. Name it **"main"**
4. Select source branch: **claude/claude-md-mi6mmw2nw73ux1cy-01TMfysXMWSVJppY1fmV7Wpk**
5. Click **"Create branch"**

---

Everything is ready to deploy - just need to create the main branch! 🚀
