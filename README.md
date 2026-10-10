# ExploreZone — lab·notebook

**Author, owner & publisher: Saeed** · venture: **ExploreZone**

A hand-written static site: portfolio + open lab notebook.
No generator, no build step, no JavaScript, no external assets, no analytics.

Live site: `https://saeedeeas123.github.io/ExploreZone/` (GitHub Pages, served from `main` / root)

## Files

```
index.html        CV / landing page — positioning, capabilities, selected work, key numbers
projects.html     full project inventory with honest status labels
notebook.html     index of notebook entries
about.html        method, capabilities, environment, timeline, explicit limits
notes/            one file per notebook entry
assets/style.css  the only stylesheet (light + dark, responsive)
.nojekyll         tells GitHub Pages to serve files as-is (no Jekyll processing)
```

## Publishing to GitHub Pages

1. Create a repository named `lab-notebook` (or any name).
2. Push these files to the default branch.
3. Repository → Settings → Pages → Source: *Deploy from a branch* → branch `main`, folder `/ (root)`.
4. The site appears at `https://<username>.github.io/lab-notebook/`.

For the site to live at `https://<username>.github.io/` instead, the repository must be named exactly
`<username>.github.io`.

Notes:

* `.nojekyll` is required so that filenames beginning with an underscore are served verbatim and no Jekyll
  build is attempted.
* Only static files are served — no server-side code, no custom headers, no redirect rules.
* GitHub Pages is not permitted as a free host for a commercial site (e-commerce, SaaS, a business
  landing page). Personal CV, portfolio, blog and project documentation are the intended uses.
* Visitor IP addresses are logged by GitHub for security purposes, regardless of sign-in.

## Editing an entry

Every note is a self-contained HTML file in `notes/`. To add one:

1. Copy an existing note, change the `<title>`, the header block, and the body.
2. Add a line for it in `notebook.html` (and in the "Latest" list on `index.html` if it belongs there).
3. Keep the notebook policy: mark whether each claim is measured, inferred, or reported by a third party —
   and mark unfinished findings as drafts rather than publishing them as results.

## Design rules

* English only.
* No external requests of any kind — the page must render identically offline.
* No claim without a number, or an explicit statement that it is unverified.
* Status labels stay unflattering. "Shipped" means it ran; "rebuilding" means testing rejected the design.

## Licence

Content is not yet licensed. Before this repository is made public, add an explicit licence
(for example CC BY 4.0 for the writing, MIT for any code) — an unlicensed public repository is not
reusable by anyone, which defeats the point of publishing it.
