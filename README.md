# abigailfuesler.com

Personal academic website for Abigail Fuesler, Ph.D. student in Forest and
Conservation Sciences at the University of Montana.

Single static HTML file. No build step, no dependencies. Hosted on GitHub Pages.

## Updating the site

Everything you would normally want to change lives in one place. Open
`index.html`, scroll to the bottom, and find the section marked
`EDIT YOUR CONTENT HERE`. Three lists live there:

- **`PUBLICATIONS`**: papers, reports, posters, thesis. Set `featured: true` to
  promote one into the two large cards at the top of the section.
- **`GALLERY`**: the six field photos and their captions.
- **`NEWS`**: the field notes list.

To add an entry, copy an existing block from `{` to `},` inclusive, paste it at
the top of the list, and change the text between the quote marks. Save, commit,
push. The site rebuilds automatically in about a minute.

To change the name, tagline, or permit block, search the file for `MASTHEAD`.

When Abi advances to candidacy, search for `Ph.D. student` (lowercase, two
spots: the meta description and the About paragraph) and change each to
`Ph.D. candidate`. Then search for `Ph.D. Student` (capitalized, one spot:
the permit block) and change it to `Ph.D. Candidate`.

## Photos and CV

Drop these into `img/` and `cv.pdf` at the root:

| File                       | Where it appears                  |
|----------------------------|-----------------------------------|
| `img/abi.jpg`              | Portrait in the About section     |
| `img/photo-1.jpg` … `-6`   | The six In the Field plates       |
| `cv.pdf`                   | Curriculum Vitae links            |

Until a photo exists, a designed placeholder shows in its place, so the site
never looks broken. Portrait reads best at 4:5, gallery plates at 3:2.

## Local preview

No server needed. Open `index.html` in a browser. For a closer match to
production:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deployment

Pushing to the default branch publishes automatically via GitHub Pages.

### Custom domain

`CNAME` in the repo root contains `abigailfuesler.com`.

In the repo: **Settings → Pages → Custom domain**, enter `abigailfuesler.com`,
save. Then tick **Enforce HTTPS** once DNS resolves.

At the domain registrar, create these records and nothing else:

**A records on `@`** (apex), pointing at GitHub Pages:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**AAAA records on `@`** for IPv6:

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**CNAME record on `www`** pointing to `USERNAME.github.io`
(replace `USERNAME` with the GitHub account that owns this repo).

GitHub redirects `www` to the bare domain automatically.

### Troubleshooting

- DNS changes can take up to 24 hours, though usually minutes.
- Extra or leftover A, AAAA, or CNAME records are the most common reason the
  HTTPS certificate fails to issue. Only the records above should exist.
- On Cloudflare, set these records to **DNS only** (gray cloud, proxy off).
- If HTTPS stays stuck, remove the custom domain in Settings → Pages, save, then
  add it back to restart certificate provisioning.

## Conventions

See `CLAUDE.md` for design tokens, motion rules, and constraints.
