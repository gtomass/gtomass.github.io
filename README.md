# gtomass.github.io

Personal academic website of Gabriel Tomassini, hosted on GitHub Pages.

> **Status:** the repository is currently **private**, so the site is not online yet.
> See [Going public](#going-public) when ready.

## Structure

```
.
├── index.html              # homepage content
├── cv/
│   └── index.html          # the CV (source of the PDF) – edit this one
├── assets/
│   ├── css/style.css       # homepage styling (colours/fonts as variables at the top)
│   └── img/                # photo, figures, favicon
├── files/
│   └── CV_Tomassini.pdf    # generated automatically – never edit by hand
├── .github/workflows/
│   └── build-cv.yml        # rebuilds the CV PDF on every CV change
├── .nojekyll               # tells GitHub Pages to serve files as-is
└── .gitignore
```

## Everyday workflow

Always start by pulling: the GitHub Action adds its own commit (the PDF), so a push
without a pull first will be rejected.

```bash
cd ~/Documents/Git_Repo/Webpage
git pull                     # 1. get the latest version (incl. the rebuilt PDF)
# ... edit files ...
git add .
git commit -m "Describe the change"
git push                     # 2. send it to GitHub
```

## Updating the CV

1. Edit `cv/index.html`.
2. Commit and push.
3. The **Build CV PDF** action (tab **Actions** on GitHub) regenerates
   `files/CV_Tomassini.pdf` in about a minute.
4. `git pull` to get the new PDF locally.

The PDF must stay on **one page**: after a change, open the CV page locally and check
File → Print preview.

## Preview locally

```bash
python3 -m http.server
```

Then open <http://localhost:8000> in a browser. The VS Code preview does not resolve
folder links such as `cv/`, so use this (or the *Live Server* extension) instead.

## Going public

GitHub Pages only works on **public** repositories with a free account.

1. Check that nothing confidential is in the repository (e.g. unpublished manuscripts):
   it will be readable by anyone, including the git history.
2. On GitHub: **Settings → General → Danger Zone → Change visibility → Public**.
3. **Settings → Pages → Source:** branch `main`, folder `/ (root)`.
4. The site is live at <https://gtomass.github.io> within a few minutes.

## Troubleshooting

| Problem | Fix |
|---------|-----|
| `git push` rejected (*fetch first* / *non-fast-forward*) | `git pull`, then push again |
| `gh` asks to log in again / `mkdir ~/.config/gh: permission denied` | `sudo chown -R $(whoami) ~/.config`, then `gh auth login` |
| The CV action fails at the push step | **Settings → Actions → General → Workflow permissions → Read and write permissions** |
| A link to `cv/` does not open in VS Code preview | Normal – use `python3 -m http.server` |