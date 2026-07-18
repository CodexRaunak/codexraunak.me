# codexraunak.me

My personal site — a minimal engineer portfolio and blog. Built with
[Hugo](https://gohugo.io/), hand-rolled layouts (no third-party theme), deployed to Vercel.

## Structure

```
content/
├── _index.md               # home intro
├── about.md                # /about
├── projects.md             # /projects
└── blog/
    ├── drafts/             # blog-compose writes here (draft: true) — NOT rendered
    └── published/          # blog-publish moves approved posts here — served at /posts/
layouts/                    # baseof, index (home), list, single, partials
assets/css/main.css         # the whole design system, one file
hugo.toml                   # config: content mounts, frontmatter map, menus, params
vercel.json                 # Vercel build settings (Hugo)
```

### How posts flow onto the site

The blog pipeline lives in the `personal-website` repo and treats Brain + Foundry as
read-only inputs:

```
Brain (thesis/voice) ─┐
                      ├─► blog-compose ─► content/blog/drafts/*.md
Foundry (evidence) ───┘                        │  (you review & approve)
                                               ▼
                              blog-publish ─► content/blog/published/ ─► /posts/
```

- `content/blog/drafts/` is **not mounted** into Hugo, and drafts carry `draft: true`, so they
  never appear on the built site.
- `content/blog/published/` is mounted as the `posts` section. `created:` in a post's front
  matter is read as its date (see `[frontmatter]` in `hugo.toml`).
- Publishing is a **human-gated** step in the `blog-publish` skill: it only moves a draft you've
  explicitly approved (REVIEW trailer removed, `draft: false`).

## Develop

```sh
hugo server -D=false        # preview at http://localhost:1313 (drafts hidden, as in prod)
```

## Build

```sh
hugo --gc --minify          # output in ./public
```

## Deploy (Vercel)

`vercel.json` pins `HUGO_VERSION` and sets the build command. To go live:

1. Create a Vercel project pointing at this repo (or `vercel link` locally).
2. Add the custom domain **codexraunak.me** in the Vercel dashboard and update DNS.
3. Pushes to the default branch build and deploy automatically.

Until the Vercel project is linked and the domain is bought, `blog-publish` builds locally and
reports the `public/` path + commit instead of deploying — it never deploys without an explicit
human go-ahead.
