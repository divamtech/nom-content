# Content Repository for Nom

This repository contains the source markdown files for blogs and case studies used on the Nom website.

## Directory Structure

- `content/blogs/`: Individual blog posts in `.md` format.
- `content/case-studies/`: Business case studies in `.md` format.

---

## Guidelines for Blogs

### File Naming
Use kebab-case for filenames: `my-awesome-blog-post.md`.

### Frontmatter Schema
```yaml
---
title: "Full Title of the Blog"
excerpt: "A 1-2 sentence summary for the listing page."
date: "2026-05-14"
author: "Author Name"
tags: ["AI", "Technology", "Business"]
status: "published"
source: "https://optional-original-source.com"
coverImage: "/path/to/image.jpg" # Optional: URL for the list view image
ogImage: "/path/to/og.jpg" # Optional: URL for social sharing
---
```

### Content Tips
- **Do NOT include an `# H1` title** in the body. The frontend automatically renders the title from the frontmatter.
- Use `##` and `###` for subheadings.
- Keep the tone professional yet engaging.
- End with a call to action or a "Resources" section.

---

## Guidelines for Case Studies

### File Naming
Use kebab-case for filenames: `customer-success-story.md`.

### Frontmatter Schema
```yaml
---
title: "Catchy Case Study Title"
date: "2026-05-14" # Format: YYYY-MM-DD
author: "Author Name"
tags: ["Solution", "Industry", "Outcome"]
status: "published" # Use "published" or "draft"
industry: "INDUSTRY NAME" # Typically UPPERCASE (e.g., FINANCE)
subtitle: "Optional secondary headline"
description: "A compelling summary of the problem and solution."
stat1_value: "80%"
stat1_label: "REDUCTION IN COST" # UPPERCASE recommended
stat2_value: "2.5x"
stat2_label: "FASTER DELIVERY"
stat3_value: "GPT-4o" # Note: frontend normalizes this to GPT-4.o
stat3_label: "LLM USED"
---
```

### Standard Structure
To maintain consistency across the site, case studies **may** follow this section hierarchy:

> [!IMPORTANT]
> **Do NOT include an `# H1` title** in the body. The page header already renders the title from the frontmatter. Start your content with `## Context`.

1. **Context**: Background on the client and their situation.
2. **The Problem**: Specific pain points and challenges being addressed.
3. **Our Approach**: The strategic thinking and methodology applied.
4. **What We Engineered**: The specific technical solutions or features implemented.
5. **Architecture and Workflow**: Technical stack, models used, and the operational flow.
6. **Business Impact**: Hard numbers and quantifiable success metrics.
7. **Why It Worked**: Rationale for why this specific solution succeeded.
8. **Risks Mitigated**: How security, privacy, or accuracy risks were handled.
9. **Client Voice**: A direct testimonial from the client (use `> Blockquote`).

---

## Supported Markdown Features

The website uses a modern rendering pipeline that supports several advanced blocks:

### 🖼️ Images
Standard markdown images are automatically optimized using Next.js Image:
```markdown
![Description of image](https://example.com/image.jpg)
```
- **Pro-tip**: Drag-and-drop images into the GitHub editor to host them easily.

### 🔢 LaTeX / Math Rendering
Mathematical formulas are rendered using KaTeX.
- **Inline**: `$E = mc^2$`
- **Block**:
  ```markdown
  $$
  I = \int_{0}^{\infty} e^{-x^2} dx
  $$
  ```

### 📊 Tables & GFM
Full support for GitHub Flavored Markdown, including:
- **Tables** (with alignment)
- **Task Lists** (`- [x] task`)
- **Strikethrough** (`~~text~~`)
- **Autolinks**

### 💻 Code Syntax Highlighting
Beautiful highlighting for 100+ languages using Shiki.
```typescript
const hello = "world";
```

### 📊 Mermaid Diagrams
Architecture diagrams and flowcharts are supported via Mermaid.js.
- **Usage**: Wrap your mermaid code in a triple-backtick block with the `mermaid` language tag.
  ```markdown
  ```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
  ```
  ```

### 🔗 Auto-Anchors
All headings (`##`, `###`) automatically generate IDs and hover-anchors for deep linking.

---

## General Notes
- **Images**: If adding images, drag-and-drop them in github file editor or use external URLs.
- **Status**: Set `status: "draft"` if you are not ready for the post to go live.
- **Formatting**: Use standard Markdown. Avoid complex HTML where possible.