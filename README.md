# pelegkremer.com (Quarto site)

Source for Peleg Kremer's personal academic website. Built with [Quarto](https://quarto.org) and hosted as a static site.

## What's here

| File / folder       | What it is |
|--------------------|-------------|
| `_quarto.yml`      | Site config and navigation |
| `styles.scss`      | Site styling (Field Notebook palette) |
| `index.qmd`        | Home |
| `about.qmd`        | About / bio |
| `research.qmd`     | Research themes overview |
| `projects/`        | One page per project (NSF, NIH, WPF, etc.) |
| `publications.qmd` | Publications list, grouped by year |
| `teaching.qmd`     | Courses taught |
| `students.qmd`     | Current advisees + alumni |
| `cv.qmd`           | Summary CV, links to full PDF |
| `news.qmd`         | Dated news / lab activity |
| `contact.qmd`      | Email, office, social links |
| `assets/`          | Photos, CV PDF, favicons |

## One-time setup

### 1. Install Quarto

Download from [quarto.org/docs/get-started/](https://quarto.org/docs/get-started/) (Windows installer, no admin needed). After install, open a new PowerShell and run:

```powershell
quarto --version
```

You should see something like `1.6.x` or higher.

### 2. Drop in your photos

In `assets/`, add:
- `portrait.jpg` – the hero portrait on the home page (recommended ~1200x1500px, JPEG)
- `hero.jpg` – optional wider banner image (e.g. Philadelphia skyline, community garden)
- `favicon.ico` – browser tab icon

In `assets/projects/`, add per-project images that will go onto each project page (see TODO notes in each `projects/*.qmd`).

### 3. Drop in your CV PDF

Save the latest CV as `assets/Kremer_CV.pdf`. The CV page links to this filename.

## Preview locally

From the site folder:

```powershell
cd ~/Dropbox/Claude_code/pelegkremer_site
quarto preview
```

This opens a live browser preview at `http://localhost:port/`. Edits to `.qmd` and `.scss` files auto-reload.

## Build for deployment

```powershell
quarto render
```

This produces a static site in `_site/`. Don't edit `_site/` directly, it gets overwritten on every render.

## Publish

The current plan is GitHub Pages with a custom domain (e.g., `pelegkremer.com`). Steps to wire up:

1. Create a GitHub repo (e.g., `pelegkremer/pelegkremer-site`).
2. From this folder: `git init`, `git add .`, `git commit -m "initial site"`, then push.
3. Add a GitHub Action that renders Quarto and deploys to the `gh-pages` branch (Quarto has a 2-line workflow at [quarto.org/docs/publishing/github-pages.html](https://quarto.org/docs/publishing/github-pages.html)).
4. Buy `pelegkremer.com` from Namecheap or Cloudflare (~$12/yr) and point the DNS at GitHub Pages (instructions in the Quarto guide above).

I (Peleg) can walk through this once the site looks good locally.

## Editing workflow

The whole site is just text files. To make an edit:

1. Open the `.qmd` file in your editor.
2. Change the text.
3. Save. If `quarto preview` is running, the browser refreshes automatically.

Quarto uses Pandoc markdown plus extensions. The main thing to know: `:::` blocks like `::: {.theme-card}` are custom containers I styled in `styles.scss`. Don't worry about them, leave the markers alone and just edit the text inside.

For most updates, you only ever touch:
- `news.qmd` – add a new entry at the top
- `publications.qmd` – add a new entry near the top
- `students.qmd` – move students between sections
- `cv.qmd` – every annual review

## TODO items still in the site

Search for `TODO` to find spots that need real content:
- Education years and prior degrees (in `about.qmd` and `cv.qmd`)
- Office room number (in `contact.qmd`)
- Google Scholar / ORCID / GitHub URLs (in `_quarto.yml` footer and `contact.qmd`)
- Photos in `assets/` and `assets/projects/`
