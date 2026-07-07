# BibTeX Cleaning Agent Guide

This repository contains a detailed protocol for agentic AI systems that clean BibTeX databases for LaTeX manuscripts. It is designed for research workflows where bibliography quality matters: journal manuscripts, appendices, online-first articles, working papers, web citations, and style-specific rendering.

The main instructions are in [AGENTS.md](AGENTS.md). A publishable GitHub Pages version is in [index.md](index.md).

## What This Repo Provides

- A step-by-step agent protocol for cleaning `.bib` files without changing citation style by accident.
- A copy-paste prompt in [prompts/bibtex-cleanup-agent.md](prompts/bibtex-cleanup-agent.md).
- A structured cleanup report template in [templates/cleanup-report.md](templates/cleanup-report.md) that records date, AI model, reasoning level, process summary, verification results, and entry-by-entry changes.
- A GitHub Actions workflow that can publish the site with GitHub Pages.

## Suggested Use

Give the agent:

1. The manuscript root directory.
2. The active `.tex`, `.aux`, `.bib`, `.bst`, and appendix files.
3. The target journal or house style.
4. The access date to use for web sources.
5. The instructions in [AGENTS.md](AGENTS.md) or the prompt in [prompts/bibtex-cleanup-agent.md](prompts/bibtex-cleanup-agent.md).

Require the agent to return both a cleaned `.bib` file and a detailed Markdown cleanup report that records the AI model, reasoning level, cleaning process, verification results, and every substantive entry-by-entry metadata change.

## GitHub Pages

This repo includes `.github/workflows/pages.yml`, which builds the site from `index.md` and publishes it through GitHub Pages.

After pushing this repository to GitHub:

1. Open the repository settings.
2. Go to **Pages**.
3. Set the source to **GitHub Actions**.
4. Push to `main` or run the workflow manually.

The page will publish at:

```text
https://USERNAME.github.io/REPOSITORY/
```

## Suggested Repository Name

```text
bibtex-cleaning-agent-guide
```

The guide is intentionally example-free so users can apply the protocol without exposing manuscript-specific cleanup logs.
