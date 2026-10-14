# Website Maintenance & Update Guide

This document outlines how to maintain and update the academic website for **Dr. Chang Liao** ([https://changliao.github.io](https://changliao.github.io)).

---

## ⚡ Quick Start: The Git Workflow

The website deployment is fully automated via GitHub Actions (`.github/workflows/deploy.yml`). Whenever you commit and push to your working branch (`al-folio-migration` or `main`), GitHub Actions automatically compiles the site using Jekyll, `jekyll-scholar`, and PurgeCSS, and deploys the production build to the `gh-pages` branch.

```bash
# 1. Ensure you are on your working branch
git checkout al-folio-migration

# 2. Make your edits (papers, news, bio, CV...)

# 3. Commit and push
git add .
git commit -m "content: add new publication"
git push origin al-folio-migration
```

Deployment takes ~2 minutes. You can monitor the progress under your repository's **Actions** tab on GitHub.

---

## 📄 Common Updates Guide

### 1. Adding a New Publication
* **File**: `_bibliography/papers.bib`
* Add a standard BibTeX entry to the bottom of the file:
  ```bibtex
  @article{liao2027example,
    abbr         = {JAMES},                    # Venue badge defined in _data/venues.yml
    bibtex_show  = {true},                     # Shows expandable "Bib" button
    title        = {Your Paper Title Here},
    author       = {Liao, Chang and Collaborator, Name},
    journal      = {Journal of Advances in Modeling Earth Systems},
    year         = {2027},
    doi          = {10.1029/xxxxxxxx},
    html         = {https://doi.org/10.1029/xxxxxxxx},
    pdf          = {2027/mypaper.pdf},         # Optional: if placed in assets/pdf/2027/
    code         = {https://github.com/changliao1025/myrepo},
    selected     = {true},                     # Set to true to showcase on the Homepage
    abstract     = {Brief 1-2 paragraph abstract summarizing key findings.}
  }
  ```
* **Important**: Do **not** add `---` front-matter markers at the top of `.bib` files.
* Your name (`Liao, Chang` / `Liao, C.`) is automatically bolded across all entries.

---

### 2. Adding News & Announcements
* **Directory**: `_news/`
* Create a new file with a descriptive name, e.g. `_news/announcement_2027_grant.md`:
  ```markdown
  ---
  layout: post
  date: 2027-03-01 09:00:00-0400
  inline: true
  related_posts: false
  ---

  Our research group received a new National Natural Science Foundation grant to develop next-generation kilometer-scale land surface and river network models at CAS IAP!
  ```
* The latest announcements automatically appear in the **News** widget on the homepage and on the `/news/` page.

---

### 3. Updating Biography & Profile Picture
* **Bio & Interests**: Edit `_pages/about.md` to update your research statement, affiliations, and homepage sections.
* **Profile Image**: Replace `assets/img/profile.png` with a square/circular photo (recommended size: 500x500px or larger).

---

### 4. Updating CV & Career History
* **File**: `_data/cv.yml`
* Update sections under `cv.sections`:
  * `Education`: Degrees, institutions, advisors, highlights.
  * `Experience`: Appointments (CAS IAP, PNNL), titles, dates, descriptions.
  * `Skills`: Modeling frameworks, programming languages (Python, Fortran, C++), HPC tools.
  * `Service` / `Awards`: Editorial boards, journal review activities, honors.

---

### 5. Adding or Updating Software Projects
* **Showcase Page**: Create or edit a file in `_projects/`, e.g. `_projects/hexwatershed.md`:
  ```markdown
  ---
  layout: page
  title: HexWatershed
  description: Mesh-independent flow direction and watershed delineation model.
  importance: 1
  category: Hydrology & Modeling
  related_publications: true
  ---

  Detailed description, methodology, installation links, and visual diagrams.
  ```
* **GitHub Repository Cards**: Edit `_data/repositories.yml` to specify which GitHub repositories appear on `/repositories/`.

---

### 6. Managing Social Profiles, Affiliations & Badges
* **Social Networks & External IDs**: Edit `_data/socials.yml` (Google Scholar, ORCID, GitHub, ResearchGate, CAS IAP URL).
* **Journal Venue Badges**: Edit `_data/venues.yml` to customize badge background colors and journal homepage URLs.
* **Global Site Settings**: Edit `_config.yml` for website title, contact note, and SEO descriptions.

---

## 🔀 Merging to `main` (Optional)

Both `main` and `al-folio-migration` are configured to trigger the automated build workflow.

If you prefer having `main` as your primary default branch on GitHub:
```bash
git checkout main
git merge al-folio-migration
git push origin main
```
After merging, you can work and push directly on `main`.

---

## 🛡️ Rollback & Backups

Your historical `AcademicPages` website is permanently preserved:
* **Remote Git Branch**: `backup-academicpages`
* **Remote Git Tag**: `v1.0-academicpages`
* **Local Folder Backup**: `c:\Users\chang_78tgbcd\workspace\github\changliao.github.io_backup_academicpages`
