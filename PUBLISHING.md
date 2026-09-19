# Publishing & Updating the Portfolio

## Part 1: First-time setup (about 15 minutes)

### 1. Create the repository on GitHub
1. Sign in at github.com as **eliasrpedroza**.
2. Click **+ → New repository**.
3. Name it exactly **`eliasrpedroza.github.io`**. This special name tells GitHub to host it at that URL.
4. Set it to **Public**. Do **not** add a README, because this folder already has one. Click **Create repository**.

### 2. Install Git and introduce yourself (one time per computer)
Windows: install from https://git-scm.com and use the **Git Bash** app it installs. Then run:

```bash
git config --global user.name  "Elias Pedroza"
git config --global user.email "eliasrpedroza@gmail.com"
```

### 3. Push this folder to GitHub
Unzip the site, open Git Bash **inside the folder** (right-click → *Open Git Bash here*), and run:

```bash
git init                      # turn this folder into a Git repository
git add .                     # stage every file for the first snapshot
git commit -m "Initial portfolio"   # save the snapshot locally
git branch -M main            # name the main branch "main"
git remote add origin https://github.com/eliasrpedroza/eliasrpedroza.github.io.git
git push -u origin main       # upload to GitHub (a browser sign-in window will pop up)
```

### 4. Turn on GitHub Pages
In the repository go to **Settings → Pages**. Under *Build and deployment* choose **Deploy from a branch**, then **main** and **/ (root)**, and click Save.
After about a minute, the site is live at **https://eliasrpedroza.github.io**. You can watch each build under the repo's **Actions** tab.

---

## Part 2: Editing
See **HOW-TO-EDIT.md**.

---

## To-do
- [ ] Add IRIS final results (final demo or test outcome) to `_projects/iris.md`
- [ ] Add videos from your phone: GOAL! gameplay, maze run, finger grasping, wig wag motor running
- [ ] Optional: add a NEO photo to the 1X entry, if you get permission (see `_data/about.yml`)
- [ ] Cancel the Wix plan and domain once the new site is live
