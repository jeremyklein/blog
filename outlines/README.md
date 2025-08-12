# Blog Post Outlines

This directory contains outlines for blog posts that will be automatically converted to full blog posts using Claude AI.

## How It Works

1. **Create Outline**: Add a new `.md` file to this directory with your blog post outline
2. **Push to Outline Branch**: Push your outline to the `outline` branch to trigger generation
3. **Auto-Generation**: GitHub Actions detects the outline and generates a complete blog post
4. **Review Process**: Generated post is placed in `content/posts/` and a PR is created for review
5. **Archive**: Processed outlines are moved to `archived/` directory

## Branch Workflow

### Setup (one-time)
```bash
# Create and switch to outline branch
git checkout -b outline
git push -u origin outline
```

### Creating Blog Posts
```bash
# Switch to outline branch
git checkout outline

# Create your outline file
echo "---
title: \"My New Blog Post\"
tags: [\"tech\", \"tutorial\"]
---

# Outline
- Introduction
- Main content
- Conclusion" > outlines/my-new-post.md

# Push to trigger generation
git add outlines/my-new-post.md
git commit -m "Add outline for new blog post"
git push origin outline
```

### What Happens Next
1. GitHub Actions generates the complete blog post
2. Creates a new branch with the generated content
3. Opens a PR to merge the generated post to `main`
4. Your outline is archived to `outlines/archived/`
5. The automated proofreading system reviews the generated post

## Outline Format

### Quick Start
1. **Copy the template**: Use `TEMPLATE.md` as your starting point
2. **Customize frontmatter**: Update title, tags, categories, etc.
3. **Expand the outline**: Replace template sections with your specific content
4. **Save and push**: Save as `your-topic.md` and push to trigger generation

### Template Structure
See `TEMPLATE.md` for a comprehensive outline template with:
- Detailed frontmatter options
- Structured outline sections
- Writing tips and best practices
- Example topics and approaches

### Basic Format
```markdown
---
title: "Your Blog Post Title"
tags: ["tag1", "tag2", "tag3"]
categories: ["category"]
target_length: "1000-1500 words"
tone: "technical but accessible"
---

# Outline

- Hook: Why this topic is important
- Background/Problem statement
- Main content sections:
  - Key concept 1
  - Key concept 2
  - Implementation details
- Real-world examples
- Best practices
- Conclusion and next steps
```

## Tips for Good Outlines

- **Be Specific**: Include key points you want to cover
- **Structure Clearly**: Use hierarchical bullet points
- **Add Context**: Include any specific technical details or examples
- **Set Tone**: Specify if you want formal, casual, technical, beginner-friendly, etc.
- **Length Guidance**: Specify target word count for appropriate depth

## File Naming

Use descriptive filenames that will become the blog post slug:
- `advanced-git-workflows.md` → `content/posts/advanced-git-workflows.md`
- `docker-best-practices.md` → `content/posts/docker-best-practices.md`

## Generated Output

Claude will create:
- Complete Hugo-compatible markdown file
- Proper frontmatter with date, title, tags, and `draft = false`
- SEO-friendly structure with appropriate headings
- Content matching your existing blog's style and tone
- Filename based on title (slugified) with current date

The generated posts will integrate seamlessly with your existing proofreading and deployment workflows.