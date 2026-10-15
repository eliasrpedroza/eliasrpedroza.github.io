# How to Edit the Portfolio

## Map: what lives where

| To change… | Edit this file |
|---|---|
| A project's text, photos, team, results | `_projects/<project>.md` |
| Home page intro (name + education) | `index.html` |
| About intro paragraphs | `about.html` |
| Experience, education, skills, leadership, About photos | `_data/about.yml` |
| Resume | replace `assets/Elias_Pedroza_Resume.pdf` (keep the name) |
| Colors, fonts, spacing, card layout | `assets/css/style.css` |
| Email / LinkedIn / GitHub links, site title | `_config.yml` |
| Header, footer, project page structure | `_includes/` and `_layouts/` (rarely needed) |

Pictures go in `assets/img/…` and videos in `assets/video/…`.

---

## Two ways to make edits

### A. Quick edits in the browser (no setup)
Good for fixing text or swapping a photo.
1. Go to `github.com/eliasrpedroza/eliasrpedroza.github.io` and open the file.
2. Click the **pencil icon**, make the change, then click **Commit changes**.
3. To add images, open the folder (e.g. `assets/img/projects/iris`), then **Add file → Upload files**, drag them in, and click **Commit**.
4. The site updates in about a minute. Check the **Actions** tab: green ✓ means it's live, red ✗ means something broke (see Troubleshooting).

### B. Bigger edits on your laptop (VS Code + Git)
Good for new projects or many changes at once.
1. Open the site folder in **VS Code**.
2. Make your changes.
3. In the terminal:
   ```bash
   git pull                       # get anything you changed on the website first
   git add .
   git commit -m "Add winter project"
   git push
   ```

**Rule of thumb:** always `git pull` before you start editing on your laptop, so you have the latest version.

---

## Editing text

### Project pages (`_projects/*.md`)
Each file has two parts:

**1. The settings block** between the `---` lines at the top (called "front matter"). It controls the card, header, team, and results box:
```yaml
title: Mobile Manipulator Maze Challenge
summary: One sentence shown on the card and under the title.
team: ["Armon Choudhry"]
results:
  - "**Bold part** then normal text"
```

**2. The body** below the second `---`, written in Markdown:
```markdown
## Section heading
### Sub-heading
Normal paragraph text. **Bold**, *italic*, [a link](https://example.com).

- Bullet point
- Another bullet
```

### About page
- Intro paragraphs: `about.html`, the two `<p>…</p>` lines near the top. Only change the words between the tags.
- Everything else: `_data/about.yml`. For example, a new leadership line:
  ```yaml
  leadership:
    - Secretary, American Society of Mechanical Engineers (ASME)
    - New role here
  ```

### ⚠️ Two formatting rules for the settings blocks and `.yml` files
1. **Indentation matters.** Use spaces, not tabs, and match the lines around it.
2. **If text contains a colon followed by a space (`: `), wrap it in quotes:**
   `- "Course Grader, Mechatronics: Haptics (graduate)"`
   Without quotes, the site shows garbled text or fails to build.

---

## Pictures and video

### Add a picture to a project page
1. Upload it into that project's folder, e.g. `assets/img/projects/iris/new-photo.jpg`.
2. Choose one of these ways to show it:

**Single image with a caption** (put it anywhere in the body):
```html
<figure>
  <img src="/assets/img/projects/iris/new-photo.jpg" alt="What it shows">
  <figcaption>Caption text.</figcaption>
</figure>
```

**A row of images** in the body:
```html
<div class="gallery">
  <figure><img src="/assets/img/projects/iris/a.jpg" alt="…"></figure>
  <figure><img src="/assets/img/projects/iris/b.jpg" alt="…"></figure>
</div>
```

**Easiest: a gallery at the bottom of the page**, listed in the settings block:
```yaml
gallery:
  - src: /assets/img/projects/iris/a.jpg
    caption: Optional caption
  - src: /assets/img/projects/iris/b.jpg
```

**Video (or photo) with notes beside it**, like the circuits page:
```html
<div class="demo demo--video">
  <video class="demo-media" src="/assets/video/my-project/clip.mp4" poster="/assets/video/my-project/clip.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
  <div class="demo-text">
    <h3>Clip title</h3>
    <p>One sentence on what it shows.</p>
    <ul>
      <li><strong>How:</strong> …</li>
    </ul>
  </div>
</div>
```
Video cards span the full width with the notes underneath. Clips with `data-autoplay` play silently while on screen; the controls let viewers pause, scrub, or go full screen. For a photo with notes beside it, use `<div class="demo">` (no `demo--video`) and swap the `<video …>` line for `<img class="demo-media" src="…" alt="…">`.

### Swap a picture
Upload the new file **with the same name** to replace the old one. Nothing else needs to change.

### Change a project's card image or top image
Edit `thumb:` (the card on the home page) and `hero_image:` or `hero_video:` (the top of the project page).

### About page photos
Add entries under `photos:` in `_data/about.yml`. You can also add a picture beside an experience entry by un-commenting its `image:` line.

### Size tips
- Photos: resize to about **1600 px wide**, JPG, under about 500 KB. Phone photos are around 5 MB and slow the site down.
- Video: MP4 (H.264), under about 20 MB, 10–40 s. iPhone `.mov` files can be converted with **HandBrake** (free).
- File names: lowercase with dashes, no spaces (`pool-test.mp4`, not `Pool Test FINAL.mov`).

---

## Adding a new project
1. Create a folder for its media: `assets/img/projects/<name>/`, and upload the photos there.
2. Copy `_templates/new-project.md` into `_projects/` and rename it, e.g. `_projects/ergodic-control.md`. **The file name becomes the URL:** `/projects/ergodic-control/`.
3. Fill in the settings block and replace the placeholder sections.
4. Set `order:` so it appears where you want, and renumber the other projects if needed.
5. Commit and push (or upload on the website).

**MSR checklist:** video first, a one-sentence summary, a results box, short hierarchical sections, teammates named, and a repo link if there is one. The repo's README should link back to the page.

---

## Changing the look

All colors are defined at the top of `assets/css/style.css`:
```css
--accent: #2f7a4c;      /* link + tag text */
--accent-fill: #3f9a62; /* lines, borders, chart */
--accent-soft: #e2f2e6; /* tag backgrounds */
--btn-bg: #a8dcb6;      /* resume button */
--bg: #f5f3ee;          /* page background */
```
Change a hex code, save, and push; the whole site updates. The block under `@media (prefers-color-scheme: dark)` holds the same colors for dark mode.

Other common tweaks in the same file:
- **Card grid columns:** `.grid { grid-template-columns: repeat(3, …) }`. Change 3 to 2 for bigger cards.
- **Wide first card:** the lines marked `first featured project`. Delete them to make every card the same size.
- **Fonts:** `--sans` and `--mono`. The fonts are loaded in `_layouts/default.html`.

**Tip:** in Chrome, right-click an element → **Inspect** to see which CSS rule styles it. You can try changes there live before editing the file.

---

## Troubleshooting
- **Actions tab shows a red ✗:** click it to see the error. It names the file and line, and it's usually a YAML indentation problem or an unquoted `: `.
- **Image doesn't show:** check the path. It's case-sensitive and must start with `/assets/…`.
- **Change isn't showing:** wait a minute, then hard-refresh (Ctrl + Shift + R).
- **Optional: preview on your laptop before pushing.** Install Ruby, then run `gem install bundler jekyll` and `jekyll serve` inside the folder, and open http://localhost:4000.
