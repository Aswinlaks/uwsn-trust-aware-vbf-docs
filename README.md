# Documentation portal: passive attribution in HH-VBF (O1 vs B-PIPE)

This repository holds only the source of the project's documentation website. It is built with [MkDocs](https://www.mkdocs.org/) and published with GitHub Pages by the workflow in `.github/workflows/deploy-pages.yml`.

The research code, the simulation outputs and the research paper are **not** in this repository.

## Contents

| Path | Purpose |
|---|---|
| `mkdocs.yml` | Site configuration and navigation |
| `docs/` | The pages (Markdown) and figures (SVG) |
| `requirements.txt` | MkDocs and its dependencies, pinned to the versions used for the validated build |
| `.github/workflows/deploy-pages.yml` | Builds the site in strict mode and deploys it to GitHub Pages |

## Preview locally

```
python -m pip install -r requirements.txt
python -m mkdocs serve
```

## Status

- Links to the code repository, the paper and the demonstration video are marked **PENDING** on the site until they exist.
- No licence has been chosen for this repository yet.
