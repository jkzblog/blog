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
This is a blog repository. Once initialized, it may use one of the following frameworks:
- **Static Site Generators:** Hugo, Jekyll, Eleventy, Astro
- **React-based:** Next.js, Gatsby
- **Vue-based:** VuePress, Nuxt Content
- **Other:** Custom implementation

### Current State
- **Status:** Empty repository (no commits yet)
- **Branch:** `claude/claude-md-mi6mmw2nw73ux1cy-01TMfysXMWSVJppY1fmV7Wpk`
- **Remote:** http://local_proxy@127.0.0.1:35499/git/jkzblog/blog

---

## Codebase Structure

### Expected Directory Structure

Once the blog is initialized, expect a structure similar to one of these patterns:

#### Hugo Structure
```
.
├── archetypes/          # Content templates
├── content/             # Blog posts and pages (Markdown)
├── data/                # Data files (JSON, YAML, TOML)
├── layouts/             # HTML templates
├── static/              # Static assets (images, CSS, JS)
├── themes/              # Hugo themes
├── config.toml          # Site configuration
└── public/              # Generated site (ignored in git)
```

#### Jekyll Structure
```
.
├── _posts/              # Blog posts (YYYY-MM-DD-title.md)
├── _drafts/             # Draft posts
├── _layouts/            # HTML templates
├── _includes/           # Reusable components
├── _data/               # Data files
├── _sass/               # Sass partials
├── assets/              # CSS, JS, images
├── _config.yml          # Site configuration
└── _site/               # Generated site (ignored in git)
```

#### Next.js Blog Structure
```
.
├── components/          # React components
├── pages/               # Routes and pages
│   ├── posts/          # Blog post pages
│   └── api/            # API routes
├── public/              # Static files
├── styles/              # CSS/SCSS files
├── lib/                 # Utility functions
├── content/             # Markdown content
├── package.json         # Dependencies
└── next.config.js       # Next.js configuration
```

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

#### Common Commands (Update based on actual framework)

**Hugo:**
```bash
hugo server -D          # Development server with drafts
hugo                    # Build for production
hugo new posts/title.md # Create new post
```

**Jekyll:**
```bash
bundle exec jekyll serve      # Development server
bundle exec jekyll build      # Build for production
```

**Next.js:**
```bash
npm run dev             # Development server
npm run build           # Production build
npm run start           # Start production server
npm run lint            # Run linter
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
Typical frontmatter structure for blog posts:

**Hugo/Jekyll:**
```yaml
---
title: "Post Title"
date: 2025-11-19
draft: false
tags: ["tag1", "tag2"]
categories: ["category"]
author: "Author Name"
description: "Brief description for SEO"
image: "/images/featured.jpg"
---
```

**Next.js (with MDX):**
```yaml
---
title: 'Post Title'
date: '2025-11-19'
tags: ['tag1', 'tag2']
excerpt: 'Brief description'
coverImage: '/images/featured.jpg'
---
```

#### File Naming
- **Blog posts:** Use kebab-case: `my-blog-post-title.md`
- **With dates:** `YYYY-MM-DD-title.md` (Jekyll convention)
- **Components:** PascalCase for React/Vue: `BlogPost.jsx`
- **Utilities:** camelCase: `formatDate.js`
- **Styles:** kebab-case: `blog-post.css`

### Code Style

#### Markdown
- Use consistent heading hierarchy (don't skip levels)
- Include alt text for all images: `![Alt text](image.jpg)`
- Use code fences with language specification: ` ```javascript `
- Use relative links for internal content
- Keep line length reasonable (80-100 characters when possible)

#### JavaScript/TypeScript
- Use consistent quotes (prefer single quotes for JS, as configured)
- 2-space or 4-space indentation (match existing code)
- Semicolons: use consistently (follow existing convention)
- Use modern ES6+ features
- Prefer `const` over `let`, avoid `var`

#### CSS/SCSS
- Use BEM methodology or CSS modules
- Mobile-first responsive design
- Organize properties logically (positioning, box model, typography, visual)
- Use CSS custom properties (variables) for theming

### Asset Management

#### Images
- **Location:** `/static/images/` (Hugo), `/public/images/` (Next.js), `/assets/images/` (Jekyll)
- **Optimization:** Compress images before committing
- **Naming:** Descriptive kebab-case: `machine-learning-diagram.png`
- **Formats:** Use WebP with fallbacks when possible

#### Static Files
- Keep static assets organized in subdirectories
- Version control only source files, not generated/built assets
- Use `.gitignore` for build outputs and dependencies

---

## Common Tasks

### Adding a New Blog Post

1. **Create the file:**
   ```bash
   # Hugo
   hugo new posts/my-new-post.md

   # Jekyll (manual)
   touch _posts/2025-11-19-my-new-post.md

   # Next.js (manual)
   touch content/posts/my-new-post.md
   ```

2. **Add frontmatter and content**

3. **Preview locally:**
   ```bash
   # Start dev server (framework-specific)
   npm run dev  # or hugo server, or bundle exec jekyll serve
   ```

4. **Commit and push:**
   ```bash
   git add .
   git commit -m "content: add post about [topic]"
   git push -u origin <branch-name>
   ```

### Updating Site Configuration

1. **Locate config file:** `config.toml`, `config.yml`, `next.config.js`, etc.
2. **Make changes** following existing patterns
3. **Test thoroughly** - config changes can break builds
4. **Document changes** in commit message
5. **Commit:** `git commit -m "config: update site title and description"`

### Adding a New Feature/Component

1. **Plan the change** - consider impact on existing code
2. **Create component files** in appropriate directory
3. **Write tests** if applicable
4. **Update documentation** if needed
5. **Test locally** thoroughly
6. **Commit with descriptive message**

### Troubleshooting Build Issues

1. **Check dependencies:**
   ```bash
   npm install  # or bundle install for Jekyll
   ```

2. **Clear caches:**
   ```bash
   # Next.js
   rm -rf .next

   # Hugo
   hugo --gc

   # Jekyll
   bundle exec jekyll clean
   ```

3. **Verify configuration** files are valid (YAML/TOML/JSON syntax)

4. **Check for broken links** or missing files

5. **Review error messages** carefully - they usually point to the issue

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
# Install dependencies
npm install  # or yarn, pnpm, bundle install

# Run development server
npm run dev

# Build for production
npm run build

# Run tests
npm test

# Run linter
npm run lint
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

## Framework-Specific Notes

### Hugo
- **Content Organization:** Use page bundles for resources
- **Shortcodes:** Create reusable content snippets
- **Taxonomies:** Use tags and categories effectively
- **Themes:** Prefer theme components over full theme overrides

### Jekyll
- **Collections:** Use for non-post content types
- **Plugins:** Check `_config.yml` for enabled plugins
- **Liquid Templates:** Learn basic Liquid syntax
- **Data Files:** Use `_data` for structured content

### Next.js
- **SSG vs SSR:** Prefer Static Site Generation for blog posts
- **Image Optimization:** Use `next/image` component
- **MDX:** Combine Markdown with React components
- **API Routes:** Use sparingly for blog functionality

### Gatsby
- **GraphQL:** Use for querying content and metadata
- **Plugins:** Check `gatsby-config.js` for plugins
- **Source Plugins:** Understand content sources
- **Gatsby Images:** Use for optimized images

---

## Additional Resources

### Documentation Links
Update these links based on the actual framework in use:

- Framework Documentation: [To be added]
- Theme Documentation: [To be added]
- Hosting Platform: [To be added]
- Style Guide: [To be added]

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

### 2025-11-19
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
