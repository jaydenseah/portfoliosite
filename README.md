# Jayden Seah Photography — Eleventy + Decap CMS

This site now auto-builds from your content. Add a shoot or post through the
admin panel, push (or the CMS pushes for you), and the site rebuilds itself —
no more copying entries into HTML by hand.

## How it fits together
- `src/index.njk`, `src/about.njk`, `src/blog.njk` — page templates
- `src/_includes/base.njk` — shared header/footer/layout
- `src/_includes/post.njk` — layout used for each individual blog post
- `src/content/portfolio/*.md` — one file per shoot (title, category, photo, date)
- `src/content/blog/*.md` — one file per blog post
- `src/admin/` — the Decap CMS login + editor screen
- `src/styles.css`, `src/images/` — copied straight into the built site untouched

Eleventy reads everything in `src/content/portfolio/` into `collections.portfolio`
and everything in `src/content/blog/` into `collections.blog`, and the templates
loop over those automatically. Add a new `.md` file (by hand or through the CMS)
and it just appears on the site next build — nothing else to wire up.

## Setup steps

1. **Push this whole folder to a GitHub repo.**
2. **Edit `src/admin/config.yml`** — replace `your-github-username/your-repo-name`
   with your actual repo path.
3. **Deploy to Netlify**, connected to that repo. It reads `netlify.toml`
   automatically (`npm run build`, publishes `_site`). Netlify also has the
   simplest built-in login (Git Gateway) for Decap CMS.
4. **Point jaydenseah.com's DNS** at the Netlify site once you're happy with it,
   and retire the WordPress hosting.
5. Log in at `yoursite.com/admin` to add shoots and posts — they'll show up on
   the live site automatically after the next deploy (usually under a minute).

## Local preview (optional)
If you want to see changes before pushing:
```
npm install
npm run start
```
This serves the site locally and rebuilds as you edit files.

## Notes
- Delete the two `sample-entry.md` files (or just edit them via the admin
  panel) once you've added real shoots and posts.
- Portfolio items don't get their own page — they're grid tiles on the
  homepage. Blog posts do get their own page, at `/blog/<slug>/`.
