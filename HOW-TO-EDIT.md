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

**Text beside a picture** (picture on the right, stacks on phones; used on IRIS "The Problem"). Leave the blank lines inside the inner `<div>` so the text is still read as Markdown:
```html
<div class="split" markdown="1">
<div markdown="1">

Your **paragraphs** go here.

</div>
<figure>
  <img src="/assets/img/projects/iris/new-photo.jpg" alt="What it shows">
  <figcaption>Caption text.</figcaption>
</figure>
</div>
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

**Grid of video/photo cards with notes underneath**, like the circuits page (two across on laptops, one on phones):
```html
<div class="demo-grid">
  <div class="demo">
    <video class="demo-media" src="/assets/video/my-project/clip.mp4" poster="/assets/video/my-project/clip.jpg" muted loop playsinline controls preload="metadata" data-autoplay></video>
    <div class="demo-text">
    <h3>Clip title</h3>
    <p>One sentence on what it shows.</p>
    <ul>
      <li><strong>How:</strong> …</li>
    </ul>
    </div>
  </div>
  <!-- copy the <div class="demo"> … </div> block for each card -->
</div>
```
- For a photo card, swap the `<video …>` line for `<a class="demo-media-link" href="/path/photo.jpg"><img class="demo-media" src="/path/photo.jpg" alt="…"></a>` (clicking it opens the full-size photo). Add `demo-media-link--fit` next to `demo-media-link` to show the whole photo instead of cropping it to fill the frame.
- For a **slideshow** that cross-fades between photos (like the op-amp card), use this in place of the media line. Add `slide--contain` to a slide to show the whole image instead of filling the frame; change the speed with `data-interval="3500"` (milliseconds) on the outer div:
  ```html
  <div class="demo-media slideshow">
    <a class="slide is-active" href="/path/one.jpg" data-label="First label"><img src="/path/one.jpg" alt="…"></a>
    <a class="slide" href="/path/two.jpg" data-label="Second label"><img src="/path/two.jpg" alt="…"></a>
  </div>
  ```
- Clips with `data-autoplay` play silently while on screen; the controls allow pause and full screen.
- Add `wide: true` to the page's settings block to give a grid page a wider column.

### Swap a picture
Upload the new file **with the same name** to replace the old one. Nothing else needs to change.

### Change a project's card image or top image
Edit `thumb:` (the card on the home page) and `hero_image:` or `hero_video:` (the top of the project page).
Add `hero_max_width: 680px` to shrink a landscape top video (used on GOAL!). With `hero_side: true`, a `hero_slides:` list (each item has `src:`, `label:`, `alt:`) shows a cross-fading slideshow instead of a video, like the RC Landing Gear page. You can also add a `side_photos:` list (each item has `src:` and `alt:`) to show a row of small portrait photos under the Results box, like the Wig Wag page. Add `hero_side: true` to show a smaller hero video beside the Results box (used on IRIS); remove it to put the video back on top at full size.

### About page photos
Add entries under `photos:` in `_data/about.yml`. You can also add a picture beside an experience entry by un-commenting its `image:` line.

### Size tips
- Photos: resize to about **1600 px wide**, JPG, under about 500 KB. Phone photos are around 5 MB and slow the site down.
- Video: MP4 (H.264), under about 20 MB, 10–40 s. iPhone `.mov` files can be converted with **HandBrake** (free).
- File names: lowercase with dashes, no spaces (`pool-test.mp4`, not `Pool Test FINAL.mov`).

---

### The "Now" line on the home page
Edit the sentence inside `<p class="now-note">` in `index.html` (it sits above the project cards), e.g. to name a project you're building. Delete the whole line to remove it.

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
Change a hex code, save, and push; the whole site updates. The block under `:root[data-theme="dark"]` holds the same colors for dark mode (the moon/sun button in the header switches modes; light is the default).

Other common tweaks in the same file:
- **Card grid columns:** `.grid { grid-template-columns: repeat(3, …) }`. Change 3 to 2 for bigger cards.
- **Fonts:** `--sans` and `--mono`. The fonts are loaded in `_layouts/default.html`.

**Tip:** in Chrome, right-click an element → **Inspect** to see which CSS rule styles it. You can try changes there live before editing the file.

---

## Troubleshooting
- **Actions tab shows a red ✗:** click it to see the error. It names the file and line, and it's usually a YAML indentation problem or an unquoted `: `.
- **Image doesn't show:** check the path. It's case-sensitive and must start with `/assets/…`.
- **Change isn't showing:** wait a minute, then hard-refresh (Ctrl + Shift + R).
- **Optional: preview on your laptop before pushing.** Install Ruby, then run `gem install bundler jekyll` and `jekyll serve` inside the folder, and open http://localhost:4000.
