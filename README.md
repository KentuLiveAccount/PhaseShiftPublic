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

The production site is generated in `public/`, excluding drafts. The live blog is
https://kentuliveaccount.github.io/PhaseShiftPublic/. Its project-site `baseURL`
is configured in `hugo.toml`; change it if hosting elsewhere.

## GitHub Pages deployment

GitHub Pages uses **GitHub Actions** as its source (Settings > Pages).
`.github/workflows/pages.yml` builds with Hugo 0.158.0 and deploys the generated
`public/` directory on every push to `main`. You can also run **Deploy Hugo site
to Pages** manually from the Actions tab on `main`. When updating Hugo in the
workflow, update the archive's SHA-256 checksum as well.

After pushing, wait for both the build and deployment jobs to succeed in Actions.
Check the home-page article link, the published article, and its styling at the
live URL. The generic [publishing test](https://kentuliveaccount.github.io/PhaseShiftPublic/posts/publishing-test/)
is a permanent smoke-test page; its source is `content/posts/publishing-test.md`.

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
   them as
   `![Descriptive alternative text](/PhaseShiftPublic/images/my-image.jpg)`.
   Root-relative URLs must include `/PhaseShiftPublic/` for this project site;
   the layouts already include it in navigation and stylesheet links.
4. Preview with `hugo server -D`, then set `draft = false` when ready to include
   the article in a production build.
5. Review the production output with `hugo --cleanDestinationDir`, then commit
   and push the selected public files to `main` to publish them. If branch rules
   require a pull request, merge it into `main` instead. Confirm the deployment
   succeeds and open the live article.

Alternatively, run `hugo new content posts/my-article.md` to create a draft with
front matter, then replace its content with the selected article.

**This repository is public:** committed and pushed drafts, images, and Git
history are visible even when Hugo excludes a draft from the built site.
Review copied files for private information before adding them.

`content/posts/welcome.md` is generic sample content; replace or remove it.
Settings are in `hugo.toml`, layouts in `layouts/`, and styling in
`static/css/site.css`.
