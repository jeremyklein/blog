# Blog Post Outlines

This directory contains outlines for blog posts that will be automatically converted to full blog posts using Claude AI.

## How It Works

1. **Create Outline**: Add a new `.md` file to this directory with your blog post outline
2. **Auto-Generation**: GitHub Actions detects the new outline and generates a complete blog post
3. **Review Process**: Generated post is placed in `content/posts/` and a PR is created for review
4. **Archive**: Processed outlines are moved to `archived/` directory

## Outline Format

Create a markdown file with YAML frontmatter:

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