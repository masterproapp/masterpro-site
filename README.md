# MasterPro Website

Everything for masterpro.app in one folder. Drag this folder to Netlify and it goes live.

---

## What's in here

```
masterpro-site/
├── index.html            →  masterpro.app          (the main site)
├── 404.html              →  shown for any bad URL
├── thd/index.html        →  masterpro.app/thd      (Home Depot portal)
├── _template/index.html  →  starter for new pages (NOT published)
│
├── logo.png              →  logo for use inside pages
├── favicon.ico           →  browser tab icon
├── favicon-16x16.png
├── favicon-32x32.png
├── apple-touch-icon.png  →  icon when saved to a phone home screen
├── icon-192.png
├── icon-512.png
├── site.webmanifest
├── robots.txt
└── netlify.toml          →  Netlify settings (caching, security)
```

**The rule:** a folder with an `index.html` inside becomes a URL path.
`thd/index.html` becomes `masterpro.app/thd`. That's the whole system.

Folders starting with `_` are ignored by Netlify, which is why `_template`
never shows up as a live page.

---

## Adding a new page

Example: creating `masterpro.app/requirements`

1. Copy the `_template` folder
2. Rename the copy to `requirements`
3. Open `requirements/index.html` and edit the title and content
4. Re-deploy (see below)

Done. The page is live at `masterpro.app/requirements`.

Some naming rules for folders: lowercase, no spaces (use hyphens, like
`retail-partners`), and no accents. The folder name IS the URL.

---

## Deploying updates

### Option A: Drag and drop (what you're doing now)

1. Go to your site in Netlify
2. Click the **Deploys** tab
3. Drag this whole folder onto the drop area

**Important:** always drag the ENTIRE folder, never a single file.
Each deploy replaces the whole site, so dragging one file would delete
everything else.

### Option B: GitHub (recommended once you have several pages)

This is worth setting up because you get automatic deploys, version
history, and one-click rollback if something breaks.

1. Create a free account at github.com
2. Create a new repository named `masterpro-site` (keep it Private)
3. Upload this folder's contents to it (GitHub's web uploader works fine,
   no command line needed: "Add file" → "Upload files")
4. In Netlify: **Site configuration → Build & deploy → Link repository**
5. Choose GitHub, pick `masterpro-site`
6. Leave the build command EMPTY, set publish directory to `.`

From then on, every time you change a file on GitHub, Netlify rebuilds
the site automatically in about 30 seconds.

---

## Rolling back a bad deploy

Netlify keeps every version. In **Deploys**, click any earlier deploy and
press **Publish deploy**. The site reverts instantly. Nothing is lost.

---

## Previewing before going live

Under **Deploys**, each deploy has its own preview URL (something like
`68a3f2--masterpro.netlify.app`). Open it to check a page before
publishing it to the real domain.

---

## Linking between pages

Use paths starting with `/`:

```html
<a href="/">Home</a>
<a href="/thd">Home Depot Portal</a>
<a href="mailto:hello@masterpro.app">Contact</a>
```

The leading slash matters: it works the same from any page, at any depth.

---

## Shared images

Put images in the top-level folder (or create an `assets/` folder) and
reference them with a leading slash:

```html
<img src="/logo.png" alt="MasterPro">
<img src="/assets/van.jpg" alt="MasterPro fleet">
```

---

## One thing to plan for

The main page still loads photos and video from Wix. See the section at
the bottom of this file: "Cutting ties with Wix".

---

## Custom domain

If masterpro.app isn't pointed at Netlify yet:
**Site configuration → Domain management → Add a domain**, then follow
Netlify's DNS instructions. HTTPS is automatic and free.


---

## Cutting ties with Wix (IMPORTANT before you cancel)

Right now the main page loads its 21 service photos, the two panel
photos, the hero video and its poster frame from Wix's servers. If you
cancel Wix, all of them go blank.

Fixing it takes about 10 minutes:

1. While your Wix site is still active, open **download-wix-assets.html**
   in your browser (just double-click it).
2. Click **Download All**. It saves all 25 files with exactly the names
   the site expects. If your browser asks to allow multiple downloads,
   click Allow.
3. Move all 25 downloaded files into the **assets** folder here.
4. Delete `index.html`, then rename `index-local-assets.html` to
   `index.html`.
5. Re-deploy the folder to Netlify.

Now nothing points at Wix, and you can cancel it safely.

`assets/README.txt` has the full checklist of required filenames. If a
file failed to download automatically, the downloader page turns that row
into a link: click it, then right-click the image and Save As using the
filename shown.

**Tip:** the hero video may be large. If the site feels slow afterward,
tell me and I can compress it.
