# Dr. Chang Liao's Academic Website

[![Deploy Site](https://github.com/changliao/changliao.github.io/actions/workflows/deploy.yml/badge.svg)](https://github.com/changliao/changliao.github.io/actions/workflows/deploy.yml)

This is the source code for the personal academic website of **Dr. Chang Liao**, Earth Scientist at the [Institute of Atmospheric Physics (IAP), Chinese Academy of Sciences (CAS)](http://english.iap.cas.cn/).

**Live Site**: [https://changliao.github.io](https://changliao.github.io)

---

## 🏛️ Overview & Architecture

* **Framework**: Built with [Jekyll](https://jekyllrb.com/) using the modern [al-folio](https://github.com/alshedivat/al-folio) academic theme.
* **Publications**: Powered by `jekyll-scholar` with automated author highlighting and metric badges. Source entries reside in `_bibliography/papers.bib`.
* **Software & Projects**: Maintained in `_projects/` highlighting HexWatershed, PyFlowline, PyEarth, and ECO3D.
* **News & Updates**: Managed in `_news/` as individual dated announcement entries.
* **Continuous Deployment**: Automated via GitHub Actions (`.github/workflows/deploy.yml`), compiling on Ruby 3.3.5 and deploying the production build to the `gh-pages` branch.

## 💾 Historical Backups

* The prior `AcademicPages`-based site is permanently preserved at Git branch `backup-academicpages` and Git tag `v1.0-academicpages`.
