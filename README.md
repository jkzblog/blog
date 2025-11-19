# My Bear Blog

A minimal, fast, and clean blog powered by [Hugo](https://gohugo.io/) and the [Bear Blog theme](https://github.com/janraasch/hugo-bearblog).

## 🌐 Live Site

**URL:** https://jkzblog.github.io/blog/

The site is automatically deployed to GitHub Pages using GitHub Actions whenever changes are pushed to the `main` branch.

## 🚀 Quick Start

### Prerequisites

- Hugo v0.123.7 or later (extended version)
- Git

### Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/jkzblog/blog.git
   cd blog
   ```

2. **Initialize the theme submodule:**
   ```bash
   git submodule update --init --recursive
   ```

3. **Run the development server:**
   ```bash
   hugo server -D
   ```

4. **View your site:**
   Open http://localhost:1313 in your browser

## 📝 Creating Content

### Create a new blog post

```bash
hugo new blog/my-post-title.md
```

This creates a new file in `content/blog/` with the proper frontmatter.

### Create a new page

```bash
hugo new about.md
```

## 📁 Project Structure

```
.
├── .github/
│   └── workflows/
│       └── hugo.yml          # GitHub Actions deployment workflow
├── archetypes/               # Content templates
├── content/                  # Blog posts and pages
│   ├── _index.md            # Home page
│   ├── about.md             # About page
│   └── blog/                # Blog posts directory
├── layouts/                  # Custom templates (override theme)
├── static/                   # Static files (images, etc.)
├── themes/
│   └── hugo-bearblog/       # Bear Blog theme (git submodule)
├── .gitignore
├── CLAUDE.md                 # AI assistant guide
├── hugo.toml                 # Site configuration
└── README.md                 # This file
```

## ⚙️ Configuration

Site configuration is in `hugo.toml`. Key settings:

- **Site Title:** `title = "My Bear Blog"`
- **Author:** `author = "Your Name"`
- **Base URL:** `baseURL = "https://jkzblog.github.io/blog/"`

## 🎨 Customization

### Adding Custom CSS

Create `layouts/partials/custom_head.html` and add your styles:

```html
<style>
  body {
    font-family: 'Your Font', sans-serif;
  }
</style>
```

### Adding a Favicon

1. Place your favicon in `static/images/favicon.png`
2. Uncomment and update in `hugo.toml`:
   ```toml
   favicon = "images/favicon.png"
   ```

## 🚢 Deployment

The site automatically deploys to GitHub Pages when you push to the `main` branch.

### Deployment Process

1. Push changes to `main` branch
2. GitHub Actions runs the Hugo build
3. Built site is deployed to GitHub Pages
4. Site is live at https://jkzblog.github.io/blog/

### Manual Build

To build the site locally:

```bash
hugo --gc --minify
```

The built site will be in the `public/` directory.

## 📚 Resources

- **Hugo Documentation:** https://gohugo.io/documentation/
- **Bear Blog Theme:** https://github.com/janraasch/hugo-bearblog
- **Bear Blog:** https://bearblog.dev/
- **Markdown Guide:** https://www.markdownguide.org/

## 🛠️ Useful Commands

```bash
# Start dev server with drafts
hugo server -D

# Build for production
hugo --gc --minify

# Create new blog post
hugo new blog/my-post.md

# List draft posts
hugo list drafts

# Check Hugo version
hugo version
```

## 📄 License

Content is yours. The Hugo Bear Blog theme is licensed under [MIT License](https://github.com/janraasch/hugo-bearblog/blob/master/LICENSE).

## 🤝 Contributing

This is a personal blog, but if you find issues or have suggestions, feel free to open an issue or pull request!

---

Built with ʕ•ᴥ•ʔ using Hugo and Bear Blog theme.
