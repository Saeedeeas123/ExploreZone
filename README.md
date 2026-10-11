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

The **git repository lives on the Linux side** at `/root/projects/ExploreZone`, not on `/sdcard`.
git cannot run on the Android FUSE mount: it reports `detected dubious ownership` (fixed once with
`git config --global --add safe.directory <path>`) and then fails to write `.git/objects/*` at all
(`No such file or directory`) — the same atomic-write limitation that breaks Obsidian MCP writes.

**Publish procedure**

```
# 1. copy the authoring copy into the repo — NOTE: tar is ADDITIVE
cd /sdcard/Download/OperitProjects/lab-notebook
tar --exclude='./.git' -cf - . | tar -xf - -C /root/projects/ExploreZone

# 2. IMPORTANT: deletions at the source do NOT propagate.
#    If you deleted files, remove them from the repo too, e.g.:
#      cd /root/projects/ExploreZone && git rm -q <paths>
#    (or use rsync -a --delete --exclude=.git <src>/ <repo>/)

# 3. commit + push
cd /root/projects/ExploreZone
git add -A && git commit -m "..." && git push origin main
```

The token is read from the vault credentials note into `/tmp/ghtok` by `_tools/ghtok.py` and passed through a
credential helper so it never appears in the remote URL. `/tmp/ghtok` is lost when the terminal session
changes — re-run the script.

Then: Repository → Settings → Pages → Source: *Deploy from a branch* → branch `main`, folder `/ (root)`.
The site is at `https://saeedeeas123.github.io/ExploreZone/`.

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
