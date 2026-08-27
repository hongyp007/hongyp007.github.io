# hongyp007.github.io

Personal academic website for YoungPyo Hong.
Plain HTML + CSS in a single file — no Jekyll, no build step, no dependencies.

Live at **https://hongyp007.github.io** once deployed.

---

## Deploy (about 5 minutes, one time)

1. On GitHub, create a **public** repository named exactly:

   ```
   hongyp007.github.io
   ```

   The name must match your username exactly or GitHub Pages will not serve it at the root URL.

2. From this folder, on your own machine:

   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/hongyp007/hongyp007.github.io.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.

4. Wait 1–2 minutes, then open https://hongyp007.github.io

To update anything later: edit `index.html`, then

```bash
git add . && git commit -m "Update" && git push
```

The live site refreshes within a minute.

---

## Files to add into `assets/`

The site is built to degrade gracefully — it looks correct right now with none of these
present, and each one appears automatically the moment you add the file with the right name.

| Filename | Used by | Status |
|---|---|---|
| `CV_YoungPyo_Hong.pdf` | Hero button | Converted from .docx — re-export from Word to fix layout |
| `profile.jpg` | Hero portrait | Cropped square from your photo |
| `grb-sed.png` | GRB 251013C card | **Re-export larger** — only 573 px wide |
| `filter-transmittance.png` | Filter card | OK |
| `followup-system.jpg` | Follow-up card | AI-generated illustration |
| `gcn-bot.jpg` | GCN bot card | AI-generated illustration |
| `gecko-candidate.png` | GECKO card | Sci / Sub / Ref cutouts |

Two images are AI-generated illustrations rather than photographs. Their `alt` text says
"Illustration of…" rather than implying they are real instrument photos — keep that wording
if you edit them.

Figures: export at roughly 1200 px wide with readable axis labels. A figure that is
unreadable on a phone is worse than no figure. Project cards use `object-fit: contain`,
so figures are never cropped — any aspect ratio is safe.

A card whose image file is missing automatically falls back to a dark gradient panel with
an icon, so the grid never breaks.

---

## Interactive pieces

All of it is vanilla JS in the one `<script>` block at the bottom — no libraries.

- **Animated sky** (`Sky()`): parallax star layers that follow the cursor, drifting meteors,
  and an occasional gamma-ray burst — a point that flares and throws an expanding shell
  outward. Click anywhere on the hero to trigger one. Runs on `<canvas>` only while
  on screen and only while the tab is focused, so it costs nothing in a background tab.
  Tune via the `opts` passed to `Sky()`: `density`, `meteors`, `bursts`.
- **Card tilt**: any element with `class="tilt"` gets 3D tilt plus a cursor-following
  spotlight. Disabled on touch devices.
- **Accordions**: the Schools / Workshops / Awards panels. Add a `.acc` block to add another.
- Scroll progress bar, scroll reveal, and active-section nav highlighting.

Everything respects `prefers-reduced-motion` — the sky renders one static frame, tilt is
off, reveals are instant. If JS fails entirely the page is still fully readable.

## Editing notes

- Everything lives in `index.html`, including the CSS in the `<style>` block. One file.
- Colors are CSS variables at the top of that block (`--accent` is the one blue accent).
- Research entries are `<div class="project">` blocks. Copy one to add another.
- Status badges: `<span class="tag published">`, `<span class="tag ongoing">`, or plain `<span class="tag">`.
- Your own name is wrapped in `<span class="me">` in author lists so it bolds automatically.
- Each `<figure>` carries the `hidden` attribute and un-hides itself via JS once its
  image loads. Leave `hidden` in place; do not remove it.
- ORCID and ADS links are commented out in the header — uncomment and fill in the IDs
  once you have them.

## Custom domain (optional, later)

Buy a domain, add a `CNAME` file containing just the domain name, and point the DNS
records at GitHub Pages. Not needed for applications; `hongyp007.github.io` is perfectly
respectable and costs nothing.
