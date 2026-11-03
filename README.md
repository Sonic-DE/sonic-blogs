# Sonic-DE blog

The posts of the Sonic-DE blog on [sonicde.org](https://sonicde.org).

This repository is the only place posts are written. The site copies them into its blog
one way, from here; the site's own post editor is turned off, so a change made anywhere
else won't last.

## Layout

```text
categories/
  release-notes.md
posts/
  2026/
    2026-11-02-first-post.md
    images/
      screenshot.png
```

Every `.md` file below `posts/`, at any depth, is a post. Every `.md` file directly in
`categories/` is a category.

## Writing a post

A post file has three parts: settings, a line containing only `;;`, then the post itself
as Markdown.

```ini
title = "First post"
date = "2026-11-02 09:00"
excerpt = "One or two sentences shown in the post list and the RSS feed."
published = 1
categories[] = "release-notes"
teaser = "images/teaser.png"
;;
Sonic-DE 6.8 is out
===================

Here's what changed.

![The new panel](images/screenshot.png)
```

| Setting | Required | Default |
| --- | --- | --- |
| `title` | Yes | |
| `slug` | No | The file name without `.md` and without a leading `YYYY-MM-DD-` |
| `date` | No | The date in the file name, else the date of the commit that added the file. UTC |
| `excerpt` | No | The text before a `<!-- more -->` line, else the start of the post |
| `published` | No | `1`. Use `0` for a draft |
| `categories[]` | No | None. One line per category slug |
| `teaser` | No | None. Teaser image, as a path relative to the post's file |

- Only the first `;;` line splits the file, so Markdown headings underlined with `===` or
  `---` work normally.
- The author is the Git author of the commit that first added the file, so a post sent as
  a pull request is credited to the person who wrote it, however the pull request is merged
  (a squash merge keeps them as the author). Later edits and renames by other people don't
  change it, and a new file is always its own post, even if it was copied from another one.
  There is no author setting in the file.
- A post with a future `date` stays hidden until then.
- Link images with paths relative to the post's file. The site stores them and rewrites
  the links. Only Markdown image syntax (`![alt](path)`) is handled.
- The `teaser` image is shown to the left of the post in the blog lists, and as the image
  when the post is shared on social media (cropped to 1200×630, so keep the subject near the
  middle and use at least that size). It isn't shown in the post itself. Without a teaser,
  the list shows no image and social media gets the site's default image.

## URLs

A post's URL is its folder path below `posts/` plus its slug, all lower-case:
`posts/2026/2026-11-02-first-post.md` becomes `/blog/2026/first-post`.

- Folder and file names may only use a-z, 0-9, `-` and `_`.
- The first folder can't be `page`, `category` or `rss.xml`.
- Moving or renaming a file keeps the same post and author. If its URL changes, the old
  URL redirects to the new one.
- Deleting a file deletes the post and its images from the site.

## Categories

A category file is `categories/<slug>.md`; the file name is the slug, 3 to 64 characters.

```ini
name = "Release Notes"
parent = "news"
;;
Notes for every Sonic-DE release.
```

`name` is required and `parent` is optional. The Markdown below `;;` is the category's
description; it can't contain images. A category slug used by a post but with no file is
created automatically.

## Publishing

A push to `master` updates the site. A scheduled sync also runs, in case a push
notification is missed. A file with an error (for example a missing `;;` line) is skipped
and logged, and the site keeps its previous version.
