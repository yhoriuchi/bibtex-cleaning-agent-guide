---
title: BibTeX Cleaning Agent Guide
---

<link rel="stylesheet" href="assets/site.css">

<main class="page-shell" markdown="1">

<section class="hero" markdown="1">

# BibTeX Cleaning Agent Guide

A source-backed protocol for agentic AI systems that clean BibTeX entries for LaTeX manuscripts without damaging citation style, publication metadata, or rendered references.

<div class="hero-actions" markdown="1">
[Read the Agent Protocol](agent-protocol.html){: .button .button-primary}
[Copy the Prompt](copy-paste-prompt.html){: .button}
[Use the Report Template](cleanup-report-template.html){: .button}
</div>

</section>

<section class="summary-grid" markdown="1">

<div class="summary-card" markdown="1">

## What the Agent Must Do

- Work from active citations in `.aux` files.
- Verify publication status and metadata before changing entries.
- Preserve the manuscript's style unless the user changes it.
- Compile the manuscript and inspect BibTeX warnings.
- Return a complete cleanup report.

</div>

<div class="summary-card" markdown="1">

## What the Agent Must Avoid

- Inventing metadata.
- Renaming keys unnecessarily.
- Deleting uncited entries by default.
- Changing `.bst` or citation packages casually.
- Publishing manuscript-specific cleanup details without approval.

</div>

</section>

## Core Workflow

<ol class="workflow">
  <li><strong>Establish scope.</strong> Identify the manuscript root, bibliography style, `.bib` files, and active citation keys from `main.aux`, appendix `.aux` files, or a regenerated build.</li>
  <li><strong>Audit the database.</strong> Scan the full `.bib` file for duplicate keys, malformed entries, stray characters, and records inside LaTeX comments that BibTeX may still parse.</li>
  <li><strong>Verify metadata.</strong> Check publisher pages, DOI landing pages, Crossref, official preprint servers, institutional pages, and cited web pages before changing fields.</li>
  <li><strong>Normalize by entry type.</strong> Use `@article` for published journal articles, `@book` and `@incollection` for books and chapters, and `@misc` for working papers, web, news, policy, and government sources.</li>
  <li><strong>Protect rendering.</strong> Preserve acronyms such as `{U.S.}`, `{US}`, `{UK}`, `{UN}`, `{EU}`, `{IO}`, and `{NATO}` where BibTeX might downcase them.</li>
  <li><strong>Build and inspect.</strong> Run the manuscript build, rerun BibTeX as needed, inspect `.blg` and `.log` files, and spot-check rendered references.</li>
  <li><strong>Report every decision.</strong> The final Markdown report should document substantive metadata changes, style cleanup, duplicate handling, verification commands, and remaining risks.</li>
</ol>

## Recommended Web Citation Pattern

Use `@misc` for web, news, policy, government, and many working-paper records when the bibliography style renders `url` fields poorly.

```bibtex
@misc{key,
  author       = {...},
  title        = {...},
  year         = {...},
  howpublished = {\textit{The New York Times}, June 14, available at \url{https://...}, last accessed July 7, 2026}
}
```

For working papers and preprints with DOIs, keep the DOI while formatting the source and URL in `howpublished`.

```bibtex
@misc{key,
  author       = {...},
  title        = {...},
  year         = {...},
  howpublished = {\textit{SSRN}, available at \url{https://...}, last accessed July 7, 2026},
  doi          = {10.2139/ssrn.0000000}
}
```

## Metadata Evidence Hierarchy

1. Publisher or journal landing page.
2. DOI resolver landing page.
3. Crossref, DataCite, PubMed, JSTOR, Cambridge, Oxford, Wiley, SAGE, Taylor & Francis, Elsevier, Springer, or another publisher database.
4. Official book publisher page or library catalog.
5. Official institutional, government, think-tank, preprint, SSRN, APSA Preprints, arXiv, OSF, or author page.
6. The cited web page itself.
7. Reliable news or archival sources.

Do not rely only on citation aggregators when a stronger source exists.

## Style Rules Worth Making Explicit

- Normalize titles to the target style, but preserve acronyms and proper nouns with braces.
- Remove imported website suffixes from titles.
- Normalize page ranges to `--`.
- Store DOI values without `https://doi.org/`.
- Remove empty fields such as `number = {}`.
- Preserve existing BibTeX keys unless resolving duplicate-key conflicts.
- Keep stable publisher links for books and journal articles out of visible web-citation fields unless the target style requires them.
- Add publisher locations only if the manuscript's style already uses them.

## Verification Checklist

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
bibtex main.aux
bibtex appendix.aux
```

The exact commands may differ, but the agent should always check:

- no repeated-entry warnings;
- no undefined citations;
- no BibTeX warnings that affect active references;
- no malformed `@misc` web references;
- rendered references for a sample of articles, working papers, books, and web sources;
- remaining LaTeX warnings, separated from bibliography problems.

## Report Structure

The final cleanup report should include:

- date checked and access date used;
- scope and files inspected;
- conventions applied;
- substantive publication-status and metadata changes;
- web and working-paper formatting changes;
- title, capitalization, and style cleanup;
- publisher-location normalization if relevant;
- duplicate-key and database-hygiene changes;
- entries checked but left unchanged;
- verification commands and results;
- remaining warnings or risks.

Use the [cleanup report template](cleanup-report-template.html) to keep this consistent across projects.

## Case Study Lessons

The included [July 7, 2026 example report](case-study.html) illustrates common repairs:

- converting web, news, policy, and working-paper records to `@misc`;
- moving source, date, URL, and access date into `howpublished`;
- adding DOI, volume, issue, page, and online-first metadata after verification;
- protecting `{U.S.}`, `{US}`, `{UK}`, `{UN}`, and `{IO}` capitalization;
- preserving publisher locations when the manuscript style expects them;
- removing duplicate keys and malformed records that BibTeX still scans;
- verifying with `latexmk`, `bibtex`, `.blg`, `.log`, and rendered-reference spot checks.

</main>
