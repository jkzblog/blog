# 🔀 How to Merge to Main Branch

Since the git configuration restricts direct pushes to `main`, you need to merge via GitHub's web interface.

## Option 1: Create Pull Request (Easiest)

1. **Go to your repository:**
   https://github.com/jkzblog/blog

2. **You should see a banner** at the top saying:
   > "claude/claude-md-mi6mmw2nw73ux1cy-01TMfysXMWSVJppY1fmV7Wpk had recent pushes"

   Click the **"Compare & pull request"** button

3. **If you don't see the banner:**
   - Click the **"Pull requests"** tab
   - Click **"New pull request"**
   - For "base", select: **main**
   - For "compare", select: **claude/claude-md-mi6mmw2nw73ux1cy-01TMfysXMWSVJppY1fmV7Wpk**
   - Click **"Create pull request"**

4. **Review and merge:**
   - Add a title like: "Initial blog setup with GitHub Pages deployment"
   - Click **"Create pull request"**
   - Click **"Merge pull request"**
   - Click **"Confirm merge"**

## Option 2: Set as Default Branch

If the main branch doesn't exist yet on GitHub:

1. **Go to:** https://github.com/jkzblog/blog/settings/branches
2. **Look for "Default branch"**
3. Click the dropdown and select **main** (if it exists)
4. Click **"Update"** and confirm

## Option 3: Direct Link

Try this direct link to create a PR:

https://github.com/jkzblog/blog/compare/main...claude/claude-md-mi6mmw2nw73ux1cy-01TMfysXMWSVJppY1fmV7Wpk

This should open the pull request creation page directly.

## After Merging

Once you've merged to main:

1. **Enable GitHub Pages:**
   - Go to: https://github.com/jkzblog/blog/settings/pages
   - Under "Build and deployment", set Source to: **GitHub Actions**
   - Save

2. **Your site will be live at:**
   https://jkzblog.github.io/blog/

The GitHub Actions workflow will automatically deploy your site!

---

**Need help?** The deployment workflow is ready to go - you just need to complete the merge!
