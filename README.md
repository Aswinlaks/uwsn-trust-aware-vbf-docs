# Documentation website: Multi-Observer Passive Attribution of Selective Forwarding Attacks in HH-VBF-Based Underwater Acoustic Sensor Networks

This repository holds the source of the project's documentation website (final-year project 23CSE498, Group 103). It is built
with [MkDocs](https://www.mkdocs.org/) and published with GitHub Pages by the workflow in `.github/workflows/deploy-pages.yml`.

The research code is kept in a separate repository; the simulation outputs and the paper are not in this repository.

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
