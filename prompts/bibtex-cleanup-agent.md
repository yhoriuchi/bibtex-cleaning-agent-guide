# Copy-Paste Prompt: BibTeX Cleanup Agent

You are cleaning a BibTeX database for an academic LaTeX manuscript. Follow the protocol below exactly.

## Inputs

- Manuscript root: `[PATH]`
- Main TeX file: `[MAIN_TEX]`
- Appendix TeX file(s): `[APPENDIX_TEX_OR_NONE]`
- BibTeX file(s): `[BIB_FILES]`
- Bibliography style file or journal style: `[BST_OR_STYLE]`
- Target journal or house style: `[STYLE_DESCRIPTION]`
- Access date for online sources: `[MONTH DAY, YEAR]`

## Task

Clean the active BibTeX entries used by the manuscript and appendix. Use `.aux` files to identify active citation keys. If `.aux` files are missing or stale, compile the manuscript far enough to regenerate them.

Also scan the full `.bib` database for duplicate keys, malformed entries, and commented-out entries that BibTeX may still parse.

## Rules

1. Preserve the existing citation style unless explicitly instructed otherwise.
2. Verify publication status and metadata from reliable sources before changing an entry.
3. Use publisher pages, DOI landing pages, Crossref, official preprint servers, official institutional pages, or the cited page itself as evidence.
4. Do not invent metadata. Leave uncertain fields unchanged and report the uncertainty.
5. Preserve BibTeX keys unless there is a duplicate-key problem.
6. Use `@article` for published journal articles.
7. Use `@misc` for working papers, preprints, news, policy, government, and web sources unless the local style requires another type.
8. For web and working-paper entries, prefer:

```bibtex
howpublished = {\textit{Source}, Month Day, available at \url{https://...}, last accessed Month Day, Year}
```

9. Protect acronyms and country names with braces, such as `{U.S.}`, `{US}`, `{UK}`, `{UN}`, `{EU}`, `{IO}`, and `{NATO}`.
10. Normalize page ranges to `--`, DOI fields to bare DOI values, and remove empty fields.
11. Keep stable publisher links for books and journal articles out of visible web-citation fields unless the style requires them.
12. Compile and verify the bibliography after editing.

## Deliverables

1. Updated `.bib` file.
2. Markdown cleanup report with:
   - date checked and access date used;
   - files inspected;
   - conventions applied;
   - substantive metadata changes with sources;
   - web and working-paper formatting changes;
   - title/capitalization/style cleanup;
   - duplicate-key and database-hygiene changes;
   - entries checked but left unchanged;
   - verification commands and results;
   - remaining warnings or risks.

Do not stop after making edits. Build the manuscript, inspect BibTeX warnings, and report the final state.
