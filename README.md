# Rohit Bansal's Website

This is my personal website for DSCI 521. It has a home page, an about
page, and a blog with two computational posts — one in R, one in Python.

## What you need installed

- [Quarto](https://quarto.org/docs/get-started/) 1.10.18 (or later)
- [uv](https://docs.astral.sh/uv/getting-started/installation/) (any recent
  version)
- [R](https://cran.r-project.org/) 4.6.1 (or later)

## How to build the site

Run these one at a time, from the top level of the repo.

**1. Clone the repo**

```bash
git clone git@github.com:Rohitb10/Rohitb10.github.io.git
cd Rohitb10.github.io
```

**2. Set up Python (in the shell)**

```bash
uv sync
```

This installs the exact Python packages from `pyproject.toml` and
`uv.lock` into a `.venv` folder.

**3. Set up R (open an R console from the top level)**

```bash
R
```

Then run this inside R:

```r
renv::restore()
```

Say yes if it asks to install packages. Once it's done, close R:

```r
q()
```

(say no to saving the workspace)

**4. Render the site (back in the shell, top level)**

```bash
uv run quarto render
```

Make sure you always run this from the top level, not from inside a post's
folder, otherwise R and renv won't work properly.

## Where the site goes

Rendering builds the site into the `docs/` folder. You can open
`docs/index.html` in a browser to see it, or run:

```bash
uv run quarto preview
```

to view it locally with auto-reload.

The live site is published from `docs/` at
https://rohitb10.github.io

## Where the data comes from

- **R post** (`posts/worldcup-analysis/`): uses the `worldcup` dataset,
  which ships inside the [`faraway`](https://cran.r-project.org/package=faraway)
  R package. No network access is needed to build this post — the data
  comes in with the package when `renv::restore()` installs it.
- **Python post** (`posts/fitness-analysis/`): uses the `linnerud`
  dataset, which ships inside `scikit-learn`. No network access is needed
  to build this post either — the data comes in with the package when
  `uv sync` installs it.

Both datasets come bundled with their packages, so building the site does
not need internet access to get the data — it's already installed along
with the package itself in step 2 and 3.