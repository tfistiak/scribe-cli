# ScribeCLI

A powerful Node.js CLI tool that turns any blog into a clean Markdown content library. It scrapes posts from a list URL, downloads all images locally, and formats frontmatter exactly how you need it.

## Features

- **Custom Frontmatter**: Define your frontmatter structure using a `demo.md` template.
- **Image Downloading**: Automatically downloads hero and content images to a local folder and updates links.
- **Smart Cleanup**: Removes duplicate titles, metadata blocks (author/date), and site-specific footer content ("Recent Posts", "Follow us").
- **Infinite Scroll**: robustly scrolls list pages to capture all posts.
- **Configurable Selectors**: Use interactive prompts or a JSON config file for CSS selectors.

## Installation

```bash
npm install
```

## Usage

Run the tool with the blog URL and your template path:

```bash
node index.js <blog_list_url> <path_to_demo.md> [options]
```

### Options

- `--config`, `-c`: Path to a JSON configuration file containing CSS selectors (bypasses interactive prompts).

### Example

```bash
node index.js https://www.bonnpark.com/blog demo.md --config bonnpark_config.json
```

## Configuration

### `demo.md`
Create a sample markdown file with the frontmatter fields you want to extract. The tool will parse these keys and scrape them.

```markdown
---
title: ""
date: ""
image: ""
categories: []
tags: []
author: ""
---
```

### `config.json` (Optional)
Navigate the interactive prompts once, or create a JSON file with your selectors:

```json
{
  "postLinkSelector": "a[href*='/post/']",
  "fm_title": "h1",
  "fm_date": "span.date",
  "fm_image": "img.hero",
  "contentSelector": "article"
}
```
