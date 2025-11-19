# CLAUDE.md - AI Assistant Guide for Blog Repository

> **Last Updated:** 2025-11-19
> **Repository:** jkzblog/blog
> **Purpose:** Documentation for AI assistants working on this blog codebase

## Table of Contents

1. [Repository Overview](#repository-overview)
2. [Codebase Structure](#codebase-structure)
3. [Development Workflows](#development-workflows)
4. [Key Conventions](#key-conventions)
5. [Common Tasks](#common-tasks)
6. [AI Assistant Guidelines](#ai-assistant-guidelines)

---

## Repository Overview

### Project Type
This is a **Hugo static site blog** using the **Bear Blog theme**.

- **Framework:** Hugo v0.123.7+extended
- **Theme:** [hugo-bearblog](https://github.com/janraasch/hugo-bearblog) by Jan Raasch
- **Philosophy:** Minimal, fast, no-nonsense blogging

### Current State
- **Status:** Initialized and configured
- **Branch:** `claude/claude-md-mi6mmw2nw73ux1cy-01TMfysXMWSVJppY1fmV7Wpk`
- **Remote:** http://local_proxy@127.0.0.1:35499/git/jkzblog/blog
- **Build System:** Hugo static site generator
- **Theme Location:** `themes/hugo-bearblog` (git submodule)

---

## Codebase Structure

### Actual Directory Structure

This blog uses Hugo with the following structure:

#### Current Hugo Structure
```
.
├── archetypes/          # Content templates
├── assets/              # Asset files (processed by Hugo Pipes)
├── content/             # Blog posts and pages (Markdown)
│   ├── _index.md       # Home page content
│   ├── about.md        # About page
│   └── blog/           # Blog posts directory
│       ├── _index.md   # Blog section index
│       └── *.md        # Individual blog posts
├── data/                # Data files (JSON, YAML, TOML)
├── i18n/                # Internationalization files
├── layouts/             # Custom HTML templates (override theme)
├── static/              # Static assets (images, CSS, JS)
├── themes/              # Hugo themes
│   └── hugo-bearblog/  # Bear Blog theme (git submodule)
├── .gitignore           # Git ignore file
├── CLAUDE.md            # This file
├── hugo.toml            # Site configuration
└── public/              # Generated site (ignored in git)
```

### Key Files and Directories

#### Configuration
- **`hugo.toml`**: Main site configuration (title, author, theme, permalinks, etc.)
- **`.gitignore`**: Excludes `public/`, `resources/`, and other generated files

#### Content
- **`content/_index.md`**: Home page content (with frontmatter)
- **`content/blog/`**: Blog posts directory
- **`content/about.md`**: About page
- All content files use TOML frontmatter (`+++` delimiters)

#### Theme
- **`themes/hugo-bearblog/`**: Git submodule containing the Bear Blog theme
- Theme can be customized by adding files to `layouts/partials/` to override theme defaults

#### Build Output
- **`public/`**: Generated static site (ignored in git, created on build)

---

## Development Workflows

### Git Workflow

#### Branch Naming Convention
- **Feature branches:** `claude/claude-md-*` (for AI assistant work)
- **Main branch:** `main` or `master`
- **Development branches:** `dev`, `develop`

#### Commit Guidelines
1. **Commit Message Format:**
   ```
   type(scope): brief description

   Optional detailed explanation
   ```

2. **Commit Types:**
   - `feat`: New feature or content
   - `fix`: Bug fix
   - `docs`: Documentation changes
   - `style`: Formatting, styling changes
   - `content`: Blog post additions/updates
   - `refactor`: Code restructuring
   - `perf`: Performance improvements
   - `test`: Adding tests
   - `chore`: Maintenance tasks

3. **Example Commit Messages:**
   ```
   content: add post about machine learning basics

   feat(theme): add dark mode toggle

   fix(layout): resolve mobile navigation issue

   docs: update CLAUDE.md with project structure
   ```

#### Push Protocol
- Always push to the designated branch: `git push -u origin <branch-name>`
- Branch must start with `claude/` and match the session ID
- Retry on network errors: up to 4 times with exponential backoff (2s, 4s, 8s, 16s)

### Build & Deployment

#### Hugo Commands

This blog uses Hugo. Here are the essential commands:

**Development:**
```bash
hugo server -D          # Development server with drafts
hugo server             # Development server (published content only)
hugo server --bind 0.0.0.0 --baseURL http://yourip:1313  # Serve on network
```

**Building:**
```bash
hugo                    # Build for production
hugo --gc --minify      # Build with garbage collection and minification
hugo --buildDrafts      # Build including draft posts
```

**Creating Content:**
```bash
hugo new blog/my-post.md     # Create new blog post
hugo new about.md            # Create new page
hugo new blog/_index.md      # Create blog section index
```

**Other Useful Commands:**
```bash
hugo list drafts        # List all draft posts
hugo list future        # List posts with future publish dates
hugo list expired       # List expired posts
hugo version            # Show Hugo version
```

#### Testing
- Always test locally before committing
- Verify links are not broken
- Check responsive design
- Validate markdown formatting
- Test build process completes without errors

---

## Key Conventions

### Content Management

#### Blog Post Frontmatter
This Hugo Bear Blog uses **TOML frontmatter** (with `+++` delimiters):

**Blog Post:**
```toml
+++
title = "Post Title"
date = 2025-11-19
draft = false
+++
```

**Page with Menu:**
```toml
+++
title = "About"
menu = "main"
weight = 3
+++
```

**Common Frontmatter Fields:**
- `title`: Post or page title (required)
- `date`: Publication date in YYYY-MM-DD format
- `draft`: Set to `true` for drafts (won't appear unless using `-D` flag)
- `menu`: Add to main menu (use `"main"`)
- `weight`: Order in menu (lower numbers appear first)
- `description`: Meta description for SEO
- `tags`: Array of tags (Bear Blog theme disables taxonomies by default)
- `slug`: Custom URL slug (optional)

#### File Naming
- **Blog posts:** Use kebab-case: `my-blog-post-title.md`
- **Pages:** Use kebab-case: `about.md`, `contact.md`
- **Section indexes:** Use `_index.md` (e.g., `blog/_index.md`)
- **No dates in filenames:** Hugo uses frontmatter `date` field instead

### Code Style

#### Markdown
- Use consistent heading hierarchy (don't skip levels)
- Include alt text for all images: `![Alt text](image.jpg)`
- Use code fences with language specification: ` ```javascript `
- Use relative links for internal content
- Keep line length reasonable (80-100 characters when possible)

#### HTML Templates (if customizing)
- Follow Go template syntax: `{{ .Title }}`, `{{ range .Pages }}`
- Place custom templates in `layouts/` to override theme defaults
- Use `layouts/partials/custom_head.html` for custom CSS/JS
- Keep templates minimal to maintain Bear Blog's performance

### Asset Management

#### Images
- **Location:** `/static/images/` (served at `/images/` in built site)
- **Optimization:** Compress images before committing
- **Naming:** Descriptive kebab-case: `machine-learning-diagram.png`
- **Usage in posts:** `![Alt text](/images/my-image.png)`
- **Favicon:** Place in `/static/images/favicon.png` and configure in `hugo.toml`

#### Static Files
- Keep static assets organized in subdirectories
- Version control only source files, not generated/built assets
- Use `.gitignore` for build outputs and dependencies

---

## Common Tasks

### Adding a New Blog Post

1. **Create the file:**
   ```bash
   hugo new blog/my-new-post.md
   ```
   This creates `content/blog/my-new-post.md` with default frontmatter.

2. **Edit the frontmatter and content:**
   ```markdown
   +++
   title = "My New Blog Post"
   date = 2025-11-19
   draft = false
   +++

   Your content goes here...
   ```

3. **Preview locally:**
   ```bash
   hugo server -D  # Include drafts
   # or
   hugo server     # Published posts only
   ```
   Visit http://localhost:1313 in your browser.

4. **Build to verify:**
   ```bash
   hugo --gc --minify
   ```

5. **Commit and push:**
   ```bash
   git add .
   git commit -m "content: add post about [topic]"
   git push -u origin <branch-name>
   ```

### Updating Site Configuration

1. **Edit `hugo.toml`:**
   - Update `title`, `author`, `description`, etc.
   - Modify `[params]` section for theme settings
   - Adjust `[permalinks]` for URL structure

2. **Test thoroughly:**
   ```bash
   hugo server
   ```
   Config changes take effect immediately (server auto-reloads)

3. **Common changes:**
   - Site title: `title = "New Title"`
   - Author: `author = "Your Name"`
   - Description: `description = "New description"`
   - Enable post navigator: `enablePostNavigator = true`

4. **Commit changes:**
   ```bash
   git commit -m "config: update site title and description"
   ```

### Customizing the Theme

The Bear Blog theme can be customized without modifying theme files:

1. **Custom CSS:**
   - Create `layouts/partials/custom_head.html`
   - Add inline styles or link to custom CSS:
   ```html
   <style>
     body { font-family: 'Your Font', sans-serif; }
   </style>
   ```

2. **Override templates:**
   - Copy template from `themes/hugo-bearblog/layouts/` to `layouts/`
   - Modify your copy (your version takes precedence)

3. **Add favicon:**
   - Place image in `static/images/favicon.png`
   - Update `hugo.toml`: `favicon = "images/favicon.png"`

### Troubleshooting Build Issues

1. **Hugo build fails:**
   ```bash
   hugo --verbose  # Run with verbose output
   hugo --debug    # Run with debug output
   ```

2. **Clear Hugo cache:**
   ```bash
   hugo --gc       # Garbage collection
   rm -rf public/  # Remove build output
   rm -rf resources/_gen/  # Remove generated resources
   ```

3. **Theme not found:**
   ```bash
   # Ensure theme submodule is initialized
   git submodule update --init --recursive
   ```

4. **Verify configuration:**
   - Check `hugo.toml` syntax (TOML format)
   - Ensure `theme = 'hugo-bearblog'` is set
   - Verify content frontmatter uses `+++` delimiters

5. **Check for broken links or missing files:**
   ```bash
   hugo --printPathWarnings
   ```

---

## AI Assistant Guidelines

### General Principles

1. **Understand Before Acting**
   - Always explore the codebase before making changes
   - Identify the framework and conventions in use
   - Read existing code to understand patterns

2. **Maintain Consistency**
   - Match existing code style and formatting
   - Follow established naming conventions
   - Use the same frameworks/libraries already in use

3. **Prioritize Safety**
   - Never delete content without confirmation
   - Test changes locally before committing
   - Create backups of important files when making major changes
   - Don't commit sensitive data (API keys, passwords, etc.)

4. **Communicate Clearly**
   - Explain what you're doing and why
   - Provide file paths with line numbers for references
   - Ask for clarification when requirements are ambiguous

### Specific Guidelines

#### When Adding Content
- Verify frontmatter format matches existing posts
- Check that all required fields are present
- Ensure images and links are valid
- Preview the post before committing

#### When Modifying Code
- Run linters and formatters if configured
- Update tests if behavior changes
- Check for TypeScript errors if applicable
- Verify no regressions in existing functionality

#### When Updating Dependencies
- Check for breaking changes in changelogs
- Update lock files (`package-lock.json`, `Gemfile.lock`)
- Test thoroughly after updates
- Document version changes in commit

#### When Refactoring
- Make incremental changes
- Ensure tests pass after each change
- Don't mix refactoring with feature additions
- Update documentation to reflect changes

### Tools and Commands

#### Exploration
```bash
# Find files by pattern
find . -name "*.md" -type f

# Search for content
grep -r "search term" --include="*.js"

# View directory structure
tree -L 3 -I 'node_modules|.git'

# Check file line count
wc -l filename.js
```

#### Git Operations
```bash
# Check status
git status

# View changes
git diff

# Stage specific files
git add path/to/file

# Amend last commit (only if not pushed)
git commit --amend

# View commit history
git log --oneline -10
```

#### Build and Test
```bash
# Hugo has no dependencies to install (static binary)

# Run development server
hugo server -D

# Build for production
hugo --gc --minify

# Check for issues
hugo --printPathWarnings

# List content
hugo list drafts
hugo list future
```

### Task Management

Use the TodoWrite tool to:
- Plan multi-step tasks
- Track progress on complex features
- Ensure all requirements are met
- Provide visibility to the user

**Example Todo Structure:**
```
1. [in_progress] Research existing blog post format
2. [pending] Create new blog post with frontmatter
3. [pending] Add images and optimize
4. [pending] Preview locally and verify formatting
5. [pending] Commit and push changes
```

### Error Handling

1. **Build Errors:**
   - Read the full error message
   - Check the file and line number mentioned
   - Verify syntax and configuration
   - Search for similar issues online if needed

2. **Git Errors:**
   - For push failures, retry with exponential backoff
   - For merge conflicts, analyze carefully before resolving
   - For branch issues, verify you're on the correct branch

3. **Dependency Errors:**
   - Check version compatibility
   - Clear caches and reinstall
   - Verify lockfiles are committed
   - Check for platform-specific issues

### Security Considerations

- **Never commit:**
  - API keys or secrets
  - `.env` files (unless `.env.example`)
  - Database credentials
  - Personal information
  - Large binary files

- **Always:**
  - Review `.gitignore` is comprehensive
  - Use environment variables for sensitive data
  - Validate user input in interactive features
  - Keep dependencies updated for security patches
  - Follow OWASP guidelines for web security

### Performance Best Practices

- Optimize images before committing
- Minimize JavaScript bundle sizes
- Use lazy loading for images and components
- Leverage static generation when possible
- Cache API responses appropriately
- Use CDN for static assets in production

---

## Hugo Bear Blog Specific Notes

### Theme Philosophy
- **Minimalism:** Keep pages tiny (~5kb) and fast
- **No JavaScript required:** Pure HTML/CSS
- **SEO optimized:** robots.txt, sitemap, meta tags included
- **Dark mode:** Automatic based on user's system preference
- **Accessibility:** Clean semantic HTML

### Hugo Features Used
- **Permalinks:** Clean URLs without dates (`/slug/` instead of `/blog/2025/11/19/slug/`)
- **Taxonomies disabled:** Bear Blog theme disables tags/categories for simplicity
- **Markdown rendering:** Uses Chroma for syntax highlighting
- **Robots.txt:** Auto-generated for SEO

### Content Organization
- **Flat structure:** Posts in `content/blog/*.md`
- **No categories/tags:** Keep it simple (disabled by default)
- **Menu system:** Use frontmatter `menu` and `weight` fields
- **Section pages:** Use `_index.md` for section landing pages

### Performance Tips
- Keep markdown files focused and concise
- Optimize images before adding to `static/`
- Use `hugo --gc --minify` for production builds
- Avoid heavy customizations that add JavaScript

### Customization Guidelines
- Use `layouts/partials/custom_head.html` for custom CSS
- Override specific templates by copying to `layouts/`
- Keep customizations minimal to maintain performance
- Test mobile and desktop views
- Verify dark mode styling if customizing CSS

---

## Additional Resources

### Documentation Links

- **Hugo Documentation:** https://gohugo.io/documentation/
- **Hugo Bear Blog Theme:** https://github.com/janraasch/hugo-bearblog
- **Bear Blog (inspiration):** https://bearblog.dev/
- **Hugo Quick Start:** https://gohugo.io/getting-started/quick-start/
- **Hugo Content Management:** https://gohugo.io/content-management/
- **Hugo Template Docs:** https://gohugo.io/templates/
- **Markdown Guide:** https://www.markdownguide.org/

### Project-Specific Notes
Add project-specific information here as the project evolves:

- Special build requirements
- Custom scripts and their purposes
- Third-party integrations
- Deployment procedures
- Contact information for questions

---

## Changelog

Track major updates to this CLAUDE.md file:

### 2025-11-19 (Update 2)
- Updated with Hugo Bear Blog specific information
- Added Hugo commands, workflows, and conventions
- Removed generic framework sections
- Added Hugo-specific troubleshooting
- Documented current project structure

### 2025-11-19 (Initial)
- Initial creation of CLAUDE.md
- Added comprehensive structure and guidelines
- Template ready for blog project initialization

---

## Contributing to This Document

This document should be updated whenever:
- The project structure changes significantly
- New conventions are established
- New tools or frameworks are added
- Common issues are discovered and resolved

When updating:
1. Maintain the existing structure
2. Update the "Last Updated" date
3. Add entry to Changelog
4. Keep examples relevant and accurate
5. Remove outdated information

---

**Note to AI Assistants:** This document is a living guide. As you work on the project and discover patterns, conventions, or useful information, consider updating this file to help future AI assistants (and human developers) working on this codebase.
