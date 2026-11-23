# PhaseShiftPublic

A minimal public Hugo blog with local layouts and no external theme dependencies.

## Preview and build

Install [Hugo](https://gohugo.io/installation/) 0.158.0 or newer (the standard
edition is sufficient). From this repository, run:

```powershell
hugo server -D
```

Open http://localhost:1313/ to preview, including drafts. Stop with Ctrl+C.

```powershell
hugo --cleanDestinationDir
```

The production site is generated in `public/`, excluding drafts. Before
publishing elsewhere, set `baseURL` in `hugo.toml` to the site's actual URL.
No hosting or deployment is configured.

## Manually publish an article

PhaseShift is the private drafting repository; PhaseShiftPublic is the public
Hugo destination. Select and copy only articles you want to make public.
There is no automatic synchronization.

1. Copy a selected Markdown article into `content/posts/my-article.md`.
2. Add front matter at the beginning:

   ```toml
   +++
   title = "My article"
   date = 2026-01-01
   draft = true
   description = "A short summary of the article."
   +++
   ```

3. Put images in `static/images/` (create the directory when needed) and reference
   them as `![Descriptive alternative text](/images/my-image.jpg)`.
4. Preview with `hugo server -D`, then set `draft = false` when ready to include
   the article in a production build.

Alternatively, run `hugo new content posts/my-article.md` to create a draft with
front matter, then replace its content with the selected article.

**This repository is public:** committed and pushed drafts, images, and Git
history are visible even when Hugo excludes a draft from the built site.
Review copied files for private information before adding them.

`content/posts/welcome.md` is generic sample content; replace or remove it.
Settings are in `hugo.toml`, layouts in `layouts/`, and styling in
`static/css/site.css`.
