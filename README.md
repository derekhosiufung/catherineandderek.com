# catherineandderek.com

Static-HTML migration of Catherine and Derek's wedding website (previously
hosted on Wix). Everything in this repo is plain HTML, CSS, JavaScript,
images, and fonts — **no server-side code or build step is required to
host it.**

## What's here

```
.
├── index.html                       Home (Invitation / Our Story / RSVP / Registry)
├── event.html                       Wedding event details + map
├── the-wedding-team.html            The Wedding Party
├── getting-to-our-wedding.html      Travel to Paris
├── where-to-stay.html               Accommodation guide
├── what-to-do.html                  What to See in Paris
├── what-to-eat.html                 What to Eat
├── other-travel-tips.html           Travel Tips
├── pre-wedding-photos.html          32-photo gallery (click to enlarge)
└── assets/
    ├── images/                      All photos and graphics
    └── fonts/                       Web fonts (Raleway, Didot, Brandon, DIN Next)
```

## Preview locally

Any static file server works. Easiest:

```sh
# Python (already installed on macOS / most Linux):
python3 -m http.server 8000
# then open http://localhost:8000/
```

Or with Node:
```sh
npx serve .
```

## Hosting

The site is 100% static — pick any free static host.

### GitHub Pages (free, easiest)

1. Push this repo to GitHub.
2. Repo Settings → Pages → Source: **Deploy from a branch** → Branch:
   **main**, folder: **/ (root)** → Save.
3. Site goes live at `https://<username>.github.io/<repo>/` within a minute.
4. To use a custom domain (e.g. `catherineandderek.com`), add a `CNAME` file
   containing the domain, then point a CNAME DNS record at
   `<username>.github.io`.

### Cloudflare Pages, Netlify, Vercel

All three accept a GitHub repo as input, deploy on every push, and give
you a free `*.pages.dev` / `*.netlify.app` / `*.vercel.app` URL plus
custom-domain support. No configuration needed — they auto-detect this
as a static site.

### Self-hosted (Nginx, Apache, Caddy, S3)

Drop the files behind any HTTP server. Sample nginx snippet:
```nginx
server {
  listen 80;
  server_name catherineandderek.com;
  root /var/www/catherineandderek;
  index index.html;
  try_files $uri $uri/ =404;
}
```

## Caveats vs. the live Wix site

- The **RSVP form**, **member login**, and **chat widget** required Wix's
  backend and are not part of this static version. The contact email
  `catherinederek0915@gmail.com` is linked from every page.
- The pre-wedding **photo gallery** uses a clean CSS grid instead of
  Wix's collage layout — same 32 photos, click any one to enlarge.
- The **Google Map** under "The Wedding Day" is a real interactive Google
  Maps embed (no API key needed). The pin shows "Shangri-La Paris" rather
  than the custom "C&D's Wedding" label, which lives in Wix's saved map
  state and can't be exported.

## Size

- Total: ~47 MB (mostly the 116 photos in `assets/images/`).
- HTML: ~1.6 MB across the 9 pages.
- Fonts: ~480 KB.
