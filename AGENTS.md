# Agent Instructions: Clean BibTeX Entries for a LaTeX Manuscript

You are cleaning a BibTeX database for an academic manuscript. Your job is to improve metadata quality, citation rendering, and bibliography hygiene while preserving the manuscript's citation style and author intent.

Do not merely prettify entries. Treat this as a source-backed audit. Every substantive change must be traceable to reliable metadata or to an explicit style rule.

## Operating Principles

1. Preserve the manuscript's existing citation style unless the user explicitly changes it.
2. Work from the active citation set first. Use generated `.aux` files when available.
3. Verify publication status and metadata from reliable sources before changing entries.
4. Avoid silent inference. If a publication date, issue, page range, DOI, or publisher location is uncertain, record the uncertainty and leave the field unchanged unless the evidence is strong.
5. Keep a written report of all substantive changes, sources checked, and verification commands.
6. Do not delete entries solely because they are uncited. Delete only duplicates, malformed commented records that BibTeX still scans, or entries the user explicitly asks you to remove.

## Initial Scope

Before editing:

1. Identify the manuscript root.
2. Identify all `.tex`, `.aux`, `.bib`, `.bst`, and bibliography-related style files.
3. If `.aux` files are missing or stale, compile the manuscript far enough to regenerate them.
4. Extract the active citation keys from the main manuscript and all appendices.
5. Identify the `.bib` file or files actually used by the build.
6. Record the target journal, style guide, or house style.
7. Record the access date that should be used for online sources.

Treat active cited entries as the primary cleanup target. Also scan the full `.bib` database for duplicate keys and syntax problems because those can break future BibTeX runs.

## Preferred Evidence Hierarchy

Use the strongest available source for each metadata decision:

1. Publisher or journal landing page for the item.
2. DOI resolver landing page.
3. Crossref, DataCite, PubMed, JSTOR, Cambridge, Oxford, Wiley, SAGE, Taylor & Francis, Elsevier, Springer, or another publisher database.
4. Official book publisher page or library catalog.
5. Official institutional, government, think-tank, preprint, SSRN, APSA Preprints, arXiv, OSF, or author page.
6. The cited web page itself.
7. Reliable news or archival sources.

Do not use citation aggregators as the only source when a publisher, DOI, or official page is available.

## Entry-Type Rules

### Published Journal Articles

Use `@article` for published journal articles. Prefer complete fields:

```bibtex
@article{key,
  author  = {...},
  title   = {...},
  journal = {...},
  year    = {...},
  volume  = {...},
  number  = {...},
  pages   = {...},
  doi     = {...}
}
```

Use `pages = {1--22}` with a double hyphen. Store DOI values without `https://doi.org/`.

For online-first articles that are published online but do not yet have assigned volume, issue, or page numbers, default to a journal-name comma plus `volume = {forthcoming}` pattern. The comma inside the `journal` field is intentional for local `.bst` styles that would otherwise print an awkward space or punctuation mark before the status label. Do not remove it as a typo.

```bibtex
@article{Horiuchi2026Civilian,
  author  = {Horiuchi, Yusaku and Tago, Atsushi},
  title   = {Civilian Control and Casualty Sensitivity in a Pacifist Democracy: Evidence from Japan's 2021 Evacuation Mission},
  journal = {Conflict Management and Peace Science,},
  volume  = {forthcoming},
  year    = {2026}
}
```

Use `forthcoming` as the default status label unless the user, journal, or publisher uses another equivalent label. User-selected alternatives such as `FirstView`, `Advance online publication`, or a publisher-specific online-first label are acceptable, but use the chosen label consistently and explain it in the report. Do not add temporary page ranges for online-first articles unless the publisher has assigned them as stable article pages.

### Working Papers and Preprints

Use `@misc` unless the local style has a better working-paper entry type. Include the repository, working-paper series, preprint server, or author/institutional page in `howpublished`. Preserve a DOI if one exists.

Recommended pattern:

```bibtex
@misc{key,
  author       = {...},
  title        = {...},
  year         = {...},
  howpublished = {\textit{SSRN}, available at \url{...}, last accessed July 7, 2026},
  doi          = {...}
}
```

### News, Policy, Government, and Web Sources

Use `@misc` with source, date if known, URL, and access date in `howpublished`.

Recommended pattern:

```bibtex
@misc{key,
  author       = {...},
  title        = {...},
  year         = {...},
  howpublished = {\textit{The New York Times}, June 14, available at \url{https://...}, last accessed July 7, 2026}
}
```

Keep the URL in `howpublished` when the target `.bst` renders separate `url` fields poorly.

Remove source names from titles when they were imported by Zotero or a browser extension, for example changing `Title - The New York Times` to `Title`.

### Books

Use `@book` for authored or edited books. Include publisher location only if the manuscript's house style uses publisher locations.

```bibtex
@book{key,
  author    = {...},
  title     = {...},
  year      = {...},
  publisher = {...},
  address   = {...}
}
```

Normalize locations conservatively, such as `Chicago, IL`, `New York, NY`, `Ithaca, NY`, `Princeton, NJ`, or `New Haven, CT`.

### Chapters and Edited Volumes

Use `@incollection` for chapters in edited volumes. Include chapter author, title, booktitle, editor, publisher, address if used, year, and pages.

## Title and Capitalization Rules

1. Follow the target bibliography style's capitalization convention.
2. Preserve acronyms and country names with braces, such as `{U.S.}`, `{US}`, `{UK}`, `{UN}`, `{EU}`, `{IO}`, `{NATO}`, and `{APSA}`.
3. Preserve proper nouns and terms that BibTeX might downcase incorrectly.
4. Do not over-brace entire titles unless the local style already does so.
5. Remove imported website suffixes from titles.
6. Normalize punctuation without changing the author's meaning.

## Field Hygiene

1. Remove empty fields such as `number = {}`.
2. Normalize page ranges to `--`.
3. Normalize DOI fields to the bare DOI.
4. Keep stable publisher links for books and journal articles out of visible web-citation fields unless the target style requires them.
5. For online-first articles without final issue/page metadata, keep the intentional comma in `journal = {Journal Name,}` and put the status label in `volume`.
6. Use `url` or `howpublished` consistently with the `.bst` behavior.
7. Avoid duplicate metadata in both `url` and `howpublished` unless the style requires it.
8. Preserve existing BibTeX keys unless there is a duplicate-key conflict.
9. Do not invent missing authors, dates, journals, page ranges, or issue numbers.

## Duplicate and Syntax Audit

Run a full database audit even when only active citations are being cleaned:

1. Detect duplicate BibTeX keys.
2. Detect entries hidden inside LaTeX `comment` environments that BibTeX may still scan.
3. Detect stray characters between entries.
4. Detect unbalanced braces and malformed fields.
5. Remove exact duplicate entries only after confirming they are identical or clearly inferior duplicates.
6. If two entries share a key but contain different metadata, preserve the better-supported entry and report the decision.

## Verification Commands

Use the manuscript's normal build command when known. Typical commands:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
bibtex main.aux
bibtex appendix.aux
```

Check:

1. No BibTeX repeated-entry warnings.
2. No undefined citations.
3. No missing bibliography fields that affect active references.
4. Rendered references display web citations as intended.
5. Book and chapter entries render publisher locations if the house style expects them.
6. Remaining warnings are unrelated to bibliography metadata or are explicitly reported.

## Required Cleanup Report

Return a Markdown report with:

1. Date checked and access date used.
2. Scope and files inspected.
3. Conventions applied.
4. Table of substantive metadata and publication-status changes.
5. Table of web and working-paper formatting changes.
6. Table of title, capitalization, and style cleanup.
7. Table of publisher-location changes, if relevant.
8. Table of duplicate-key and database-hygiene changes.
9. Items checked but left unchanged, with reasons.
10. Verification commands and results.
11. Remaining warnings or risks.

## Stop Conditions

Stop and ask the user before:

1. Changing the citation style policy.
2. Renaming many BibTeX keys.
3. Removing non-duplicate uncited entries.
4. Replacing the active `.bst` or LaTeX bibliography package.
5. Making broad changes to entries that are outside the active citation set.
6. Publishing the cleaned bibliography or report to a public repository when the manuscript is unpublished or sensitive.
