# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Local Development
```bash
hugo server          # Start development server with live reload (usually on localhost:1313)
hugo server -D       # Include draft posts in development server
hugo server --bind 0.0.0.0 --port 1313  # Bind to all interfaces
```

### Building
```bash
hugo                 # Build static site to /public/ directory
hugo -D              # Build including draft posts
hugo --minify        # Build with minified output
```

### Content Creation
```bash
hugo new posts/post-name.md        # Create new post with archetype template
hugo new posts/my-article.md       # Creates content/posts/my-article.md with frontmatter
```

## Project Architecture

### Hugo Static Site Structure
- **Generator**: Hugo static site generator
- **Theme**: Soho theme (minimalist, mobile-first, based on Hyde)
- **Content**: Markdown files with TOML frontmatter
- **Output**: Static HTML/CSS/JS in `/public/`

### Key Directories
- `/content/posts/` - Blog post markdown files
- `/themes/soho/` - Theme files (layouts, CSS, JS)
- `/public/` - Generated static site (git-ignored build output)
- `/static/` - Static assets copied directly to public
- `/layouts/` - Custom layout overrides (currently empty)
- `/archetypes/` - Content templates for `hugo new`

### Content Structure
Posts use TOML frontmatter:
```toml
+++
date = '2025-08-01T08:59:49-04:00'
draft = true
title = 'My First Post'
+++
```

### Theme Configuration
Main config in `hugo.toml`:
- Site title, baseURL, language settings
- Theme specification: `theme="soho"`
- Soho theme supports custom CSS/JS, social icons, SEO features

#### Soho Theme Customization
- **Custom styling**: Add `customCss = ["css/blog.css"]` and `customJs = ["js/blog.js"]` in `[params]`
- **Profile picture**: Set `profilePicture = "images/profile.png"` or `gravatar = "email@example.com"`
- **Social icons**: Add `[[params.socialIcons]]` blocks for LinkedIn, GitHub, Twitter, etc.
- **Theme color**: Override with `themeColor = "#fc2803"`
- **SEO**: Built-in support for Open Graph, Schema.org, Twitter Cards

### Build Process
1. Hugo processes content files and applies theme templates
2. Generates static HTML/CSS/JS in `/public/`
3. `/public/` contains complete deployable site
4. Theme assets (CSS, JS) are automatically included from `/themes/soho/static/`

### Content Workflow
1. Create posts with `hugo new posts/filename.md`
2. Edit content and set `draft = false` when ready to publish
3. Use `hugo server -D` to preview drafts locally
4. Create Pull Request for automated proofreading feedback
5. Review and apply proofreading suggestions
6. Merge PR to automatically build and deploy site

### Content Organization
- **Taxonomies**: Posts support `tags = ["tag1", "tag2"]`, `categories = ["category"]`, `series = ["series-name"]` in frontmatter
- **Menu items**: Configure in `hugo.toml` under `[menu]` section
- **Static files**: Place images/assets in `/static/` to be copied directly to `/public/`

## Automated Proofreading

### Overview
- **AI-Powered**: Uses Claude 3 Haiku for cost-effective proofreading (~$0.01-0.05 per post)
- **GitHub Integration**: Automatically triggered on Pull Requests modifying blog posts
- **Workflow**: `.github/workflows/proofread.yml` handles the automation
- **Non-blocking**: Provides feedback without preventing publishing

### How It Works
1. **Trigger**: Opens/updates PR with changes to `content/posts/**/*.md` files
2. **Analysis**: Claude reviews content for grammar, clarity, flow, tone, and technical accuracy
3. **Feedback**: Posts detailed suggestions as PR comments
4. **Updates**: Refreshes comments automatically when PR is updated

### Setup Requirements
- **API Key**: Anthropic API key stored in GitHub Secrets as `ANTHROPIC_API_KEY`
- **Setup Guide**: Follow instructions in `SETUP_PROOFREADING.md`
- **Permissions**: Workflow has read access to content and write access to PR comments

### Proofreading Scope
- ✅ Grammar and spelling corrections
- ✅ Writing clarity and flow improvements
- ✅ Sentence structure enhancements
- ✅ Tone consistency analysis
- ✅ Technical accuracy verification (when applicable)

### Cost Efficiency
- Uses Claude 3 Haiku (fastest, most economical model)
- Only runs on PR changes, not every commit
- Typical cost per blog post: $0.01-0.05

### Workflow Integration
- Seamlessly integrates with existing Git workflow
- All feedback tracked in version control
- Enables collaborative editing and review process

### Deployment

#### Automatic Deployment
- **GitHub Actions**: Configured to deploy to GitHub Pages automatically on push to main branch
- **Workflow**: `.github/workflows/deploy.yml` builds and deploys the site
- **URL**: https://jeremyklein.github.io/blog/
- **Setup**: Ensure GitHub Pages is enabled with "GitHub Actions" as source in repository settings

#### Manual Deployment
- Build output in `/public/` is a complete static site ready for deployment
- Common targets: GitHub Pages, Netlify, Vercel, or any static hosting service
- Ensure `baseURL` in `hugo.toml` matches your deployment domain

#### Post-Push Deployment
Every push to the `main` branch will automatically:
1. Build the Hugo site with `hugo --gc --minify`
2. Deploy to GitHub Pages
3. Make the site available at the configured URL