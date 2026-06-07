# Your Personal Website

A clean, fast personal site for an economist and photographer — no frameworks, no build tools, pure HTML/CSS/JS.

---

## Files

```
your-name-website/
├── index.html        Homepage
├── research.html     Research & CV (two-column: publications left, CV right)
├── photography.html  Photography Portfolio
├── style.css         All shared styles and design tokens
├── nav.js            Active nav-link highlighting
├── papers/           Your publication PDFs go here (see below)
├── images/           Your photos go here
└── README.md         This file
```

---

## Editing Your Content

Every placeholder is marked with a comment like:

```html
<!-- !! UPDATE: Replace with your real name !! -->
```

Search for `!! UPDATE` across all files to find every one.

---

## Hosting Publication PDFs on GitHub

This is the recommended approach — your PDFs live right in the repo alongside your HTML.

### Setup

1. Create a folder called `papers/` in your project root (next to `index.html`)
2. Name your PDFs clearly, e.g.:
   - `papers/smith-jones-2024-labor.pdf`
   - `papers/smith-2023-housing.pdf`
   - `papers/working-paper-2025.pdf`
3. Upload them to GitHub the same way you upload any file (drag and drop in the web interface)

### Linking a PDF in research.html

For each publication, the title is already set up as a download link:

```html
<!-- With PDF: use an <a> tag -->
<a href="papers/smith-jones-2024-labor.pdf" class="pub-title" download>
  Title of Your Paper
</a>

<!-- Without PDF yet: use a plain <p> tag -->
<p class="pub-title">Title of Paper Without PDF</p>
```

The `download` attribute tells the browser to download the file instead of opening it.
A small ↓ arrow is automatically added after the title via CSS when `download` is present.

The "PDF ↓" link in the `pub-links` row below should point to the same file:

```html
<a href="papers/smith-jones-2024-labor.pdf" class="pub-link" download>PDF ↓</a>
```

---

## Adding a New Section (e.g. Blog, Music)

1. Duplicate any existing page: copy `research.html` → `blog.html`
2. Clear out the content and write your new section
3. Add a nav link in **all** existing pages:
   ```html
   <li><a href="blog.html">Writing</a></li>
   ```
4. Styles and nav are already shared — nothing else to change

---

## Adding Photos

1. Put your image files in the `/images/` folder (JPG recommended, under 2MB each)
2. Open `photography.html`
3. Replace each placeholder `<div class="photo-placeholder">` with:
   ```html
   <img src="images/your-filename.jpg" alt="Brief description" loading="lazy" />
   ```
4. Set `data-category` on the `.photo-cell` to: `landscape`, `architecture`, `documentary`, or `portrait`
   (add your own categories by also adding a matching filter button)

---

## Deploying to GitHub Pages

### First time

1. Go to github.com → New repository
2. Name it exactly: `yourusername.github.io`
3. Upload all files (drag and drop in the GitHub web interface, or use `git push`)
4. Go to **Settings → Pages** → Source: `Deploy from a branch` → Branch: `main` → Folder: `/ (root)`
5. Your site is live at `https://yourusername.github.io` within a couple of minutes

### Updating the site

**Via GitHub web interface:** Navigate to the file → click the pencil icon → commit changes.

**Via git (faster for multiple files):**
```bash
git add .
git commit -m "Update publications"
git push
```

---

## Adding a Custom Domain (Optional)

1. Buy a domain (~$12/year via Namecheap or Cloudflare)
2. Add these DNS records at your registrar:
   ```
   A     @    185.199.108.153
   A     @    185.199.109.153
   A     @    185.199.110.153
   A     @    185.199.111.153
   CNAME www  yourusername.github.io
   ```
3. In GitHub: **Settings → Pages → Custom domain** → enter your domain → Save
4. Check "Enforce HTTPS" once it appears (a few minutes)

---

## Customizing Colors

All colors are CSS variables at the top of `style.css`:

```css
:root {
  --cream:        #FAF8F4;  /* page background */
  --ink:          #1C1A17;  /* primary text */
  --muted:        #6B6760;  /* secondary text */
  --accent:       #3B4D3A;  /* forest green — links, highlights */
  --accent-light: #8FA98E;  /* lighter green — labels */
  --rule:         #D9D5CC;  /* borders and dividers */
}
```

Change any value once and it updates everywhere on the site.
