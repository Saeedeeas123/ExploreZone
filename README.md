# Saeed — profile site

Static HTML, served from GitHub Pages at **https://saeedeeas123.github.io/ExploreZone/**.
No build step, no trackers, no CDN.

## Pages (two, deliberately)

| File | Page | Content |
|---|---|---|
| `index.html` | **About** | Who Saeed is, in his own words. Short on purpose — it grows as things come to mind. |
| `work.html` | **Work** | One post per module: name, one-line description, link to the repository. |

## Design

Neubrutalism (classic variant) + self-hosted Montserrat. One shared stylesheet (`assets/style.css`)
carries the whole theme, so a restyle never requires touching the markup.

## History

- 2026-10-11 — site created as a portfolio + open lab notebook (home, work, notebook, 10 notes, about).
- 2026-10-15 — **reset to two pages by Saeed's order**: the notebook, the notes, the old work page and
  the old about page were deleted, and the brand changed to `Saeed · ExploreZone`. Everything removed
  is still recoverable from git history; the working copy of the old pages is also kept at
  `/sdcard/Download/OperitProjects/lab-notebook/`.

## Publishing

The live site is served from this repository's `main` branch. Deletions must be staged with `git rm`
(a plain file copy never removes anything on the remote).
