# MasterPro — masterpro.app

Single-page site for MasterPro. Home services and appliance installation across CA, OR, WA, TX, OK and LA.

**Always By Your Side.**

---

## Contents

```
index.html              the whole site — HTML, CSS and JS in one file
images/
  masterpro-logo.png        dark logo (light backgrounds)
  masterpro-logo-light.png  light logo (dark backgrounds)
  max-02-thumbs-up.png      Max in the nav bar
  max-09-phone-clipboard.png  Max in the "Meet Max" section
  appliances/               product and part photos, transparent PNG
.nojekyll               stops GitHub Pages running Jekyll
```

No build step, no dependencies, no framework. Open `index.html` and it works.

---

## Publishing on GitHub Pages

1. Create a repository and upload everything in this folder (keep the structure).
2. **Settings → Pages → Source:** Deploy from a branch → `main` → `/ (root)`.
3. Wait a minute, then load `https://<user>.github.io/<repo>/`.

### Custom domain

1. Add a file named `CNAME` at the root containing one line: `masterpro.app`
2. At your DNS provider add four A records for the apex pointing at
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`,
   and a CNAME for `www` pointing at `<user>.github.io`.
3. **Settings → Pages → Custom domain:** enter the domain and tick *Enforce HTTPS*.

---

## Sections

| Section | Notes |
| --- | --- |
| Nav | Logo, Max peeking over the bar, tagline, **Work With Us** |
| Hero | Orange poster — *Always by your side.* |
| Metrics | Six operational figures |
| Meet Max | The mascot and what he stands for |
| Can MasterPro install this? | Two-step picker: appliance → modification → answer |
| Reviews | Three customer quotes |
| Every job, end to end | Seven-step retail partner timeline |
| Coverage | Dot map + service van |
| Final CTA | Request Installation + phone |
| Footer | Links, contact, social |

---

## Editing

Everything lives in `index.html`.

**Text** — search for the wording and change it.

**Phone / email** — `(341) 344-9850` and `hello@masterpro.app` appear in the final CTA, the footer, and the sticky mobile bar. Search and replace both the visible text and the `tel:` / `mailto:` links.

**Coverage map** — near the bottom of the file, look for `class="coverage-map"`. It's a grid of `<circle>` elements. Orange `#E56A2C` / `#F08E58` marks an active state, `#c9bea1` is everywhere else. To light up a new state, change the `fill` on the circles in that position.

**Picker options** — in the `<script>` block, the `steps` array holds both questions. Each option is `{l: label, img: photo, a: "Problem?", b: "Answer."}`. Add an entry and drop a matching transparent PNG into `images/appliances/`.

**Colours** — the `:root` block at the top of the `<style>`:

```css
--orange:  #E56A2C
--paper:   #F1E9D7
--ink:     #171614
```

---

## Responsive

Tested with no horizontal overflow at 1440, 1024, 768 and 390 px.

| Width | Layout |
| --- | --- |
| ≥1180px | Full desktop |
| ≤1180px | Timeline to 4 columns, picker to 4 |
| ≤1024px | Meet Max and Coverage stack, picker result stacks |
| ≤820px | Timeline to 2 columns, picker to 3 |
| ≤680px | Single column, picker to 2, type scales down |
| ≤400px | Tighter padding, smaller nav |

Touch devices get 44px minimum tap targets and no hover transforms.

---

## Images

All images are full-resolution 24-bit RGBA PNGs with transparency, exactly as cut from the
source files — no downscaling, no palette reduction. Total around 26 MB, which is well within
GitHub Pages limits (1 GB repo, 100 GB/month bandwidth).

If you later want faster first loads without touching the originals, the safe options are
serving WebP alongside the PNGs, or adding `loading="lazy"` to images below the fold.
Neither changes the source files.

---

## Still open

- **Contact is `mailto:`** — every CTA opens an email. A form posting to an inbox would convert better and would not depend on the visitor having a mail client set up.
- **Reviews are placeholders** — swap in real ones, ideally pulled from Google.
- **Metrics** — confirm the six figures before launch.
- **Range photo** — the picker has no range image; the cooktop tile covers that case for now.
- **Social links** in the footer point to `#`.
