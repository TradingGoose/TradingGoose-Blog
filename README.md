# TradingGoose Blog

Blog content for [TradingGoose.ai/blog](https://tradinggoose.ai/blog).

Posts in this repo are automatically fetched and rendered by TradingGoose Studio. Push a new post and it goes live within 10 minutes — no app deploy needed.

## Folder structure

Each post is a folder at the repo root. The folder name becomes the URL slug.

```
my-post-title/
  index.md        # Post content (frontmatter + markdown)
  cover.png       # Cover image (optional)
  diagram.png     # Any additional images used in the post
  screenshot.jpg
```

Example: `getting-started/index.md` renders at `/blog/getting-started`.

## Frontmatter

```yaml
---
title: "Your Post Title"
description: "A short summary shown in cards and SEO meta."
date: "2026-04-07"
image: "cover.png"            # Relative to post folder, or absolute URL
published: true               # Set false to hide (default: true)
tags:
  - trading
  - automation
authors:
  - "BWJ2310"                 # Simplest — just a GitHub username
  - github: "BWJ2310"         # With overrides
    name: "TradingGoose Team"
    x: "tradinggoose"         # Optional X/Twitter handle
---
```

### Authors

Only a GitHub username is required. The system auto-resolves:

| Field | Resolved from |
|-------|--------------|
| Avatar | `github.com/{github}.png` |
| Profile link | `github.com/{github}` (or `x.com/{x}` if `x` is set) |
| Display name | `@{github}` (or custom `name` if provided) |

## Images

### Cover image

Set `image` in frontmatter. Relative paths resolve to the post folder:

```yaml
image: "cover.png"       # → {post-folder}/cover.png
image: "https://..."     # Absolute URLs work too
```

### Inline images

Use standard markdown with relative paths:

```markdown
![Architecture diagram](./diagram.png)
![Screenshot](./screenshot.jpg)
```

All relative paths are auto-resolved to `raw.githubusercontent.com` URLs at render time.

## Setup

Add these environment variables to TradingGoose Studio:

```bash
BLOG_GITHUB_REPO=TradingGoose/TradingGosoe-Blogs   # This repo
BLOG_GITHUB_BRANCH=main                              # Optional, defaults to main
GITHUB_TOKEN=ghp_...                                  # Optional, increases API rate limit
```

Content revalidates every 10 minutes via Next.js ISR.

## Local development

For local dev without this repo, place posts directly in:

```
TradingGoose-Studio/apps/tradinggoose/app/(landing)/blog/content/
  my-post/
    index.md
    cover.png
```

Same structure, same frontmatter. When `BLOG_GITHUB_REPO` is not set, the app reads from this local folder.
