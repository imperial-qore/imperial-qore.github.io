# QORE Website — Static Copy

A self-contained static mirror of the **QORE (Quality of Service Research Lab)**
website of the Department of Computing, Imperial College London, originally at
<https://qore.doc.ic.ac.uk/> (a WordPress site).

All internal links, stylesheets, scripts and images have been localized so the
site runs as plain static files — no PHP, database or WordPress runtime required.
It is ready to deploy on GitHub Pages.

## Contents

| Path | Page |
|------|------|
| `index.html` | Home |
| `members/` | Members |
| `research/` | Research |
| `join-us/` | Join us |
| `publications/` | Publications (archive) |
| `qos-management-publications/`, `computer-system-modelling-publications/`, `dependability-and-fault-tolerance-publications/` | Publication categories |
| `publication/<slug>/` | Individual publication pages |
| `projects/`, `project/radon-h2020/`, `project/ibids-epsrc/` | Projects |
| `wp-content/`, `wp-includes/` | Theme CSS/JS, images and other assets |

External links (Imperial College, GitHub `imperial-qore`, DOI/arXiv/IEEE/ACM,
Google Scholar, Web of Science, the footer *Login*, Google Fonts) intentionally
still point to their live locations.

## What was changed vs. the live site

- The theme's PHP-generated stylesheets (`style.php`, `style-custom.php`) were
  fetched and saved as static `style.css` / `style-custom.css`.
- Assets hosted on the separate `wp.doc.ic.ac.uk/qore/` host (including the QORE
  logo) were downloaded into `wp-content/`.
- WordPress `?p=<id>` short-links were rewritten to their canonical pretty URLs;
  duplicate short-link pages and RSS feed files were removed.
- Absolute `https://qore.doc.ic.ac.uk/…` URLs were converted to relative paths.
- Dead WordPress `<head>` metadata (pingback, RSS, oEmbed, XML-RPC, EditURI) was
  stripped.

## Run locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000/
```

(Open via a web server, not `file://`, so the pretty directory URLs resolve.)

## Deploy on GitHub Pages

**Option A — GitHub Actions (included).** Push to GitHub, then in
*Settings → Pages → Build and deployment* set **Source = GitHub Actions**. The
workflow in `.github/workflows/pages.yml` publishes the repository root on every
push to `main`.

**Option B — Deploy from a branch.** In *Settings → Pages* set
**Source = Deploy from a branch**, branch `main`, folder `/ (root)`.

The `.nojekyll` file disables Jekyll processing so all files are served verbatim.
