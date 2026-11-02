# Sonic-DE blog

The posts of the Sonic-DE blog on [sonicde.org](https://sonicde.org).

This repository is the only place posts are written. The site copies them into its blog
one way, from here; the site's own post editor is turned off, so a change made anywhere
else won't last.

## Writing a post

Each post is one Markdown file named `posts/YYYY-MM-DD-slug.md`, starting with front
matter:

```yaml
---
title: The post's title
slug: the-post-slug
date: 2026-11-02
author: Your Name
categories: []
excerpt: One or two sentences shown in the post list and the RSS feed.
published: true
---
```

The post itself follows as Markdown.

- `published: false` keeps a post off the site while it's being written.
- Put a post's images in `posts/images/` and link them with relative paths. The site copies
  them to its media storage and rewrites the links.
- A post is tracked by its file name: renaming or deleting the file takes the old post
  off the site.

## Publishing

A push to this repository updates the site. A scheduled sync also runs, in case a push
notification is missed.
