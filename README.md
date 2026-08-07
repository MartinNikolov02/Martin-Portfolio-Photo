# Martin Nikolov — Photography Portfolio

Built with [Hugo](https://gohugo.io) + the [digio-theme](https://github.com/danapixels/digio-theme)
(pixel/retro Hugo theme), customized into a photo + video portfolio.

## What's here

- **Home** (`content/_index.md`) — intro, status box, and two link cards:
  Photo Portfolio / Video Portfolio (replaces the theme's original "watching" box)
- **`/photos/`** — gallery section. Each shoot is its own folder (page bundle)
  with its own images and a pure-CSS lightbox (no JS)
- **`/videos/`** — each entry embeds a YouTube/Vimeo URL automatically
- **`/me/`** — likes / dislikes / hobbies, plus a pets section (cat & dog) with
  little pixel-style HP bars

## Run it locally

You need [Hugo Extended](https://gohugo.io/installation/) v0.146.0+ (this was
built and tested against v0.163.0).

```bash
hugo server -D
```

Then open http://localhost:1313/

## Things to edit before you publish

1. **`content/_index.md`**
   - `portraitImage` — currently points at a placeholder. I can't generate a
     stylized image of your actual face, so make this yourself: take a photo,
     run it through a pixelate/pixel-art tool (pixelit.js, a Photoshop mosaic
     filter, an app like Pixel Studio), and drop the result in as
     `static/portrait.png`.
   - `introTitle` / `introBody` — edit freely.
   - `statusText` — whatever you're currently working on / your next shoot.

2. **`content/me.md`**
   - `likes` / `dislikes` / `hobbies` — pre-filled with a starting point, edit
     as you like.
   - `[[pets]]` — swap in your cat's and dog's actual names/emoji/hp. `hp` is
     just 0–100 and purely decorative (how full the little bar looks).

3. **`content/photos/`**
   - Delete `content/photos/example-shoot/` once you have real ones.
   - To add a shoot: create a folder `content/photos/your-shoot-name/`
     containing an `index.md` (copy the example's front matter — `title`,
     `date`, `category`) plus your image files (jpg/png) right in that same
     folder. The first image becomes the cover on the gallery grid.

4. **`content/videos/`**
   - Same pattern — one folder per project, `index.md` with a `videoUrl`
     pointing at a YouTube or Vimeo link.

## Publish it as its own GitHub repo + GitHub Pages

This is fully separate from any other site/repo you have — nothing here
touches anything else.

1. Unzip this project locally, then from inside the folder:

   ```bash
   git init
   git add .
   git commit -m "Initial portfolio site"
   ```

2. Create a new, empty repo on GitHub (no README/license — you already have
   files), e.g. `martin-photography`. Then:

   ```bash
   git branch -M main
   git remote add origin https://github.com/<your-username>/martin-photography.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Build and deployment → Source →
   "GitHub Actions"**. That's it — the included workflow
   (`.github/workflows/hugo.yml`) builds and deploys the site automatically
   on every push to `main`. Your first push will already trigger it; check
   the **Actions** tab for progress.

4. Your site will be live at `https://<your-username>.github.io/martin-photography/`
   (or your custom domain, if you set one up in the Pages settings).

Note: the theme is vendored directly into `themes/digio-theme/` (not a git
submodule), so the repo is self-contained and works right after `git push` —
no submodule init step needed. If you'd rather track the theme as a submodule
so you can pull upstream updates, that's an easy swap later:
`git submodule add https://github.com/danapixels/digio-theme themes/digio-theme`.
