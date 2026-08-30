# velocipartners.com

Marketing site for **Veloci Partners** — accounting, tax and advisory for owner-led businesses. Lagos · London · Berlin.

Static site. One HTML file plus image assets. No build step, no dependencies, no framework. Edit and push.

```
.
├── index.html            the entire site (HTML + CSS + JS inline)
├── 404.html              styled not-found page
├── assets/
│   ├── logo-lockup.png       "Veloci Partners" lockup, full colour (light backgrounds)
│   ├── logo-lockup-white.png "Veloci Partners" lockup, knockout — used in nav + footer
│   ├── logo.png              supplied "Veloci" mark, full colour
│   ├── logo-white.png        supplied "Veloci" mark, knockout
│   ├── favicon.ico       16/32/48px browser icon
│   ├── favicon.png       512px icon
│   ├── apple-touch-icon.png
│   └── og-image.png      1200×630 social share card
├── CNAME                 custom domain for GitHub Pages
├── robots.txt            + sitemap.xml for search engines
├── .nojekyll             stops GitHub Pages running Jekyll
├── .gitignore
└── LAUNCH-GUIDE.md       full deploy + DNS walkthrough
```

---

## Push it to GitHub

Already initialised on `main` with a commit made. Create an empty repo at [github.com/new](https://github.com/new) (**don't** tick "Add a README"), then:

```bash
git remote add origin https://github.com/YOUR_USERNAME/velocipartners-site.git
git push -u origin main
```

Prefer clicking? Install [GitHub Desktop](https://desktop.github.com) → *Add Local Repository* → point it here → *Publish repository*.

> Keep this folder **outside OneDrive**. Git and OneDrive fight over file locks.

---

## Publish it

**Repo → Settings → Pages → Source: "Deploy from a branch" → Branch `main` / `root` → Save.**

Live in about a minute at `https://YOUR_USERNAME.github.io/velocipartners-site/`, then at `www.velocipartners.com` once DNS points at GitHub (Step 6 of the launch guide).

Every `git push` redeploys automatically.

---

## Before you go live

- [ ] **Replace `YOUR_FORM_ID` in `index.html`** with your Formspree ID — the contact form does nothing until you do
- [ ] Replace or delete the placeholder quote section (marked `<!-- ==== QUOTE ==== -->`)
- [ ] Trim the "Who We Serve" pills to industries you actually serve
- [ ] Confirm the Lagos / London / Berlin descriptions match how you actually operate
- [ ] Remove any claim you can't substantiate

Contact details are already in: `clients@velocipartners.com`, `+234 806 268 6488`, `+234 806 368 0464`.

The hero visual is a decorative globe — no figures, no data, nothing to fact-check.

---

## Editing

Everything visual lives in `index.html`. The palette is the first block of CSS:

```css
--ink:       #23282C;   /* graphite — nav, dark bands, headings */
--brand:     #8BC34A;   /* Veloci green — buttons, accents, rules */
--brand-dk:  #6FA436;   /* hover state */
--brand-txt: #5A8A2A;   /* green dark enough for small text on white */
--paper:     #FAFAF9;   /* page background */
```

Sections are marked with comment banners (`<!-- ==== SERVICES ==== -->`) so they're easy to find, reorder or delete.

Logo assets were generated from the supplied "Veloci" mark: `#8BC34A` green, `#757575` grey. The word **Partners** was set in **Poppins Regular**, baseline-matched and x-height-matched to the existing wordmark, to form the full lockup.

If you get a vector version of the logo (`.svg`), drop it into `assets/` and swap the `<img src>` — it'll stay crisp at any size. Keep Poppins if you extend the lockup elsewhere.

## License

© Veloci Partners. All rights reserved.
