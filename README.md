# CV Repository

LaTeX source for a one-page, ATS-friendly resume (header: **Backend Engineer**).
Builds to `main.pdf` with `latexmk`.

## Prerequisites

- A LaTeX distribution with `latexmk`, e.g. TeX Live or MiKTeX.
- The `charter` package and other packages listed in `main.tex` (all standard).

## Build

```sh
latexmk -pdf main.tex
```

The output is `main.pdf`. Clean up build artifacts with:

```sh
latexmk -c
```

## Project structure

```
main.tex                     # Entry point; includes sections in order
header/header.tex            # Name, title, contact links
profile/profile.tex          # Short profile paragraph
skills/skills.tex            # Skills list
experience/                  # Work experience
projects/                    # Project entries (one file per project)
education/education.tex      # Education
extracurriculars/            # Extracurriculars
certificates/certificates.tex# Certificates (languages merged here)
languages/languages.tex      # Optional; unused by default
```

## Customizing

- **Sections included** are controlled in `main.tex` via `\input{...}`.
- **Projects**: comment/uncomment entries in the `Projects` section. Active by
  default: `projects/briefly`, `projects/catalyst`, and the inline `latch-store`
  npm package entry. Available but commented out: `tabibi`, `pivot`,
  `signspeak`, `orbit`, `walletwatch`, `taskwave`.
- **Experience**: `kiosk-pos` is active; `nti-mean-stack` is commented out.
- **Fonts**: `main.tex` uses the serif `charter`. Alternatives are commented out
  near the top (Fira Sans, Roboto, Noto Sans, Source Sans Pro).

## ATS notes

- `glyphtounicode.tex` plus `\pdfgentounicode=1` produce machine-readable,
  ATS-parsable text.
- Margins and spacing are tuned for exactly one page; adjust section files
  rather than the geometry if content changes.

## Repository

Git remote: `https://github.com/seifsheikhelarab/CV.git`

## Use as a template

Clone the repo and start from a clean copy of your own:

```sh
git clone https://github.com/seifsheikhelarab/CV.git my-cv
cd my-cv
rm -rf .git   # start fresh history
git init
```

Then make it yours:

1. **Header** — edit `header/header.tex`: name, title, location, email, phone,
   and links.
2. **Profile** — rewrite `profile/profile.tex` as a 1–2 line summary.
3. **Skills** — update `skills/skills.tex` to match your stack.
4. **Experience** — add/edit files under `experience/` and include them in
   `main.tex`.
5. **Projects** — add a file per project under `projects/` and toggle which ones
   render by commenting/uncommenting their `\input` in `main.tex`.
6. **Education / Extracurriculars / Certificates** — edit the matching files
   under their folders.
7. Build and check it still fits on one page:

```sh
latexmk -pdf main.tex
```

Push to your own remote when ready:

```sh
git remote add origin <your-repo-url>
git push -u origin main
```

## MIT License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file
for details.
