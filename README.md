# yeonsukwak

Personal academic website for **Yeonsu Kwak**, Ph.D. candidate in Chemical and Biomolecular
Engineering at the University of Delaware.

Served from this repository at the custom domain in `CNAME`. See `PUBLISH.md` for the publishing
checklist.

## Built with

Plain HTML, CSS, and vanilla JavaScript. No build step, no dependencies, no framework. Served
directly by GitHub Pages from `main`.

Type is [Spectral](https://fonts.google.com/specimen/Spectral) and
[IBM Plex Sans](https://fonts.google.com/specimen/IBM+Plex+Sans).

## Structure

```
├── index.html          all content
├── assets/
│   ├── css/style.css   design tokens are the custom properties at the top
│   ├── js/main.js      nav, scroll spy, reveal, publication tabs
│   └── img/
├── cv/                 CV as PDF
├── CNAME               custom domain for GitHub Pages
├── PUBLISH.md          publishing checklist, in Korean
└── .nojekyll           serve files as-is, no Jekyll processing
```

## Running it locally

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Notes

Colors, spacing, and the type scale are CSS custom properties at the top of `assets/css/style.css`,
so the whole palette changes from one block. The page is responsive, works without JavaScript,
and its text clears WCAG AA contrast.
