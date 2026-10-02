# Gabriel Tomassini – academic website

Personal website hosted on GitHub Pages.

## Structure

```
.
├── index.html              # page content
├── .nojekyll               # tells GitHub Pages to serve files as-is
├── assets/
│   ├── css/
│   │   └── style.css       # all styling (colours, fonts, layout)
│   └── img/
│       ├── photo.jpg       # profile photo (square, ~400×400 px)
│       ├── afgl4106.jpg    # SPHERE image (ESO potw2608)
│       └── favicon.png     # optional browser-tab icon
└── files/
    └── CV_Tomassini.pdf    # full CV
```

## Files to add

| File | Where |
|------|-------|
| Profile photo | `assets/img/photo.jpg` |
| AFGL 4106 image (from the ESO potw page, keep the credit) | `assets/img/afgl4106.jpg` |
| CV | `files/CV_Tomassini.pdf` |
| Favicon (optional) | `assets/img/favicon.png` |

Then fill in every `[...]` placeholder in `index.html`.

## Deploy on GitHub Pages

1. Create a public repository named `<username>.github.io`.
2. Push the contents of this folder to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Initial website"
   git branch -M main
   git remote add origin https://github.com/<username>/<username>.github.io.git
   git push -u origin main
   ```
3. In the repository, go to **Settings → Pages** and check the source is `main` / root.
4. The site is live at `https://<username>.github.io` within a minute or two.

## Updating

- **Text**: edit `index.html`.
- **Look** (colours, fonts, spacing): edit the variables at the top of `assets/css/style.css`.
- **CV**: replace `files/CV_Tomassini.pdf` with the new version (keep the same name so links don't break).

Preview locally with `python3 -m http.server` in this folder, then open http://localhost:8000.
