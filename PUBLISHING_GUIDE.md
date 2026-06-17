# Publishing Guide — GitHub & Portfolio

A step-by-step, professional checklist for putting **InsureAllBI** on GitHub and showcasing it in your portfolio.

---

## Part 0 — Before you push (do this first) ⚠️

1. **Remove hardcoded credentials.** Open `RestApiProject/misc/Utilities.py` and replace the hardcoded `username`/`password` defaults with Databricks Secrets (see the snippet in `README.md → Configuration & Security`). If those were real credentials that were ever shared publicly, **rotate them**.
2. **Drop stray files.** Delete `manifest.mf` and rename `DownloadDatabaseBakFile.txt.txt` to something clean like `docs/data_source.md` (or remove it). The `.gitignore` already excludes these.
3. **Add the new files** from this package to the project root: `README.md`, `LICENSE`, `.gitignore`, and the `docs/` folder.
4. **Decide on the data backup.** Don't commit the `.bak` file. Instead, keep the download link inside `README.md` or `docs/` so others can fetch it themselves.

Your final structure should match the "Repository Structure" section of the README.

---

## Part 1 — Put it on GitHub

### Option A — Command line (recommended)

> Prerequisite: [Git installed](https://git-scm.com/downloads) and a [GitHub account](https://github.com).

1. **Create the repo on GitHub**
   - Go to github.com → **New repository**
   - Name: `insureallbi-databricks-pipeline` (clear, searchable, hyphenated)
   - Description: *"End-to-end Medallion lakehouse on Databricks: REST API → Bronze/Silver/Gold with PySpark, Delta Lake & Unity Catalog."*
   - **Public**, do **not** initialize with a README (you already have one)

2. **Initialize and push** (run from your project folder)
   ```bash
   cd path/to/RestApiProject-root
   git init
   git branch -M main
   git add .
   git commit -m "Initial commit: InsureAllBI medallion lakehouse pipeline"
   git remote add origin https://github.com/<your-username>/insureallbi-databricks-pipeline.git
   git push -u origin main
   ```

3. **Verify** the README renders and the architecture diagram displays on the repo home page.

### Option B — Web upload (no command line)

1. Create the repo as in Option A (this time **check** "Add a README" so the repo isn't empty, then you'll overwrite it).
2. Click **Add file → Upload files**, drag your folders/files in, and commit.
3. Repeat per folder if the uploader limits you.

### Option C — Databricks Repos (keeps notebooks in sync)

In Databricks: **Repos → Add Repo → link your GitHub repo**. You can then commit notebook changes from inside Databricks. Good if you'll keep iterating.

---

## Part 2 — Make the repo look professional

- [ ] **About panel** (gear icon, top-right of repo): add the description, your portfolio URL, and **topics**: `databricks`, `pyspark`, `delta-lake`, `data-engineering`, `medallion-architecture`, `unity-catalog`, `etl`, `spark-sql`.
- [ ] **Pin the repo** on your GitHub profile (Profile → Customize your pins).
- [ ] **Commit history:** a few meaningful commits read better than one giant dump. If you have time, commit layer by layer (bronze → silver → gold → docs).
- [ ] **Dashboard screenshot (later):** you don't have one yet — that's fine. When you build a Databricks SQL / Power BI dashboard on the Gold tables, add the screenshot to `docs/` and embed it in the README. It's the single highest-impact addition for recruiters, so it's worth doing as a follow-up.
- [ ] **Profile README:** if you don't have one, create a repo named exactly your username and feature this project there.

---

## Part 3 — Add it to your portfolio

### What to include for each portfolio entry
1. **Title:** "InsureAllBI — Insurance Analytics Lakehouse on Databricks"
2. **One-line hook:** *"Built an end-to-end Medallion pipeline ingesting 8 REST API datasets into a governed Bronze/Silver/Gold lakehouse, surfacing CLV, profitability, and fraud KPIs."*
3. **The architecture diagram** (`docs/architecture.svg`)
4. **3–5 highlights** (see `CASE_STUDY.md`)
5. **Two buttons:** **View Code (GitHub)** and, if available, **View Dashboard**

### Where to host the portfolio — GitHub Pages (your choice)

GitHub Pages is free, developer-credible, and lives right next to your code. Two easy paths:

**Path 1 — Profile/portfolio repo with a theme (fastest)**
1. Create a repo named `<your-username>.github.io` (this becomes your site root).
2. Add an `index.md` and paste in the content from `CASE_STUDY.md`. Embed the diagram with `![Architecture](architecture.svg)` and copy `architecture.svg` into the repo.
3. Go to **Settings → Pages → Source: Deploy from a branch → `main` / root**, then **Save**.
4. In a minute your site is live at `https://<your-username>.github.io`. Optionally pick a theme under **Settings → Pages → Theme chooser**.

**Path 2 — Project-level Pages (per repo)**
1. In the `insureallbi-databricks-pipeline` repo, **Settings → Pages → Deploy from branch → `main` / `/docs`**.
2. Put an `index.md` (your case study) inside the `docs/` folder alongside `architecture.svg`.
3. Site publishes at `https://<your-username>.github.io/insureallbi-databricks-pipeline/`.

> Tip: for a more designed look later, GitHub Pages supports Jekyll themes (e.g. `minimal`, `cayman`) — set `theme: jekyll-theme-cayman` in a `_config.yml`. The simple Markdown approach above is enough to launch today.

A ready-to-paste case study is provided in **`CASE_STUDY.md`** — drop it straight into `index.md`.

---

## Part 4 — Talk about it well (résumé & interview)

**Résumé bullets** (tighten with your real numbers):
- Engineered an end-to-end Medallion (Bronze/Silver/Gold) lakehouse on Databricks, ingesting 8 REST API datasets with pagination, auth, and rate-limit retry into Delta Lake.
- Designed a Kimball star schema with MD5 surrogate keys and idempotent Delta `MERGE` loads, governed via Unity Catalog.
- Delivered 9 curated Gold tables powering KPIs (customer lifetime value, loss ratio, fraud detection rate, MoM/YoY growth).

**Be ready to explain:** why medallion; full-load vs. incremental MERGE; how the schema registry enforces types; how you'd add orchestration, data-quality checks, and CI/CD; and how you secured credentials.

---

## Quick checklist

- [ ] Credentials removed / rotated
- [ ] Stray files cleaned, `.gitignore` added
- [ ] README + LICENSE + diagram in place
- [ ] Repo public, pushed, renders correctly
- [ ] Topics + About + pinned
- [ ] Case study added to portfolio
- [ ] Repo linked on LinkedIn & résumé
