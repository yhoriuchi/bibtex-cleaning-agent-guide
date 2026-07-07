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
2. Check the original source of each active item as much as possible before changing an entry.
3. Use publisher pages, DOI landing pages, Crossref, official preprint servers, official institutional pages, official news/web pages, or the cited page itself as evidence. Do not rely only on citation exports or aggregators when an original source is available.
4. Do not invent metadata. Leave uncertain fields unchanged and report the uncertainty.
5. Preserve BibTeX keys unless there is a duplicate-key problem.
6. Use `@article` for published journal articles.
7. For articles published online before final volume, issue, or page numbers are assigned, use `@article` with an intentional comma after the journal name and put the online-first status in `volume`. Default to `volume = {forthcoming}` unless the user chooses `FirstView` or another equivalent publisher label.

```bibtex
@article{Horiuchi2026Civilian,
  author  = {Horiuchi, Yusaku and Tago, Atsushi},
  title   = {Civilian Control and Casualty Sensitivity in a Pacifist Democracy: Evidence from Japan's 2021 Evacuation Mission},
  journal = {Conflict Management and Peace Science,},
  volume  = {forthcoming},
  year    = {2026}
}
```

8. Do not remove the comma in `journal = {Journal Name,}` for online-first records; it is a local `.bst` rendering workaround, not a typo.
9. Use `@misc` for unpublished manuscripts, working papers, preprints, newspaper articles, policy sources, government pages, and web sources unless the local style requires another type. Add a public URL in `howpublished` whenever one exists.
10. For web and working-paper entries, prefer:

```bibtex
howpublished = {\textit{Source}, Month Day, available at \url{https://...}, last accessed Month Day, Year}
```

11. Protect acronyms and country names with braces, such as `{U.S.}`, `{US}`, `{UK}`, `{UN}`, `{EU}`, `{IO}`, and `{NATO}`.
12. Normalize page ranges to `--`, DOI fields to bare DOI values, and remove empty fields.
13. Add publisher locations for books and chapters unless the style guide explicitly omits them; for example, use `address = {New York, NY}` with `publisher = {Cambridge University Press}` so the rendered reference can show `New York, NY: Cambridge University Press`.
14. Check whether the target style requires Title Case or sentence case, apply it consistently, and protect acronyms or proper nouns that BibTeX might downcase.
15. Keep stable publisher links for books and journal articles out of visible web-citation fields unless the style requires them.
16. Compile and verify the bibliography after editing.

## Deliverables

1. Updated `.bib` file.
2. Markdown cleanup report with:
   - date checked and access date used;
   - AI model and reasoning level or intelligence setting, for example `Codex GPT-5.5` and `Extra High`;
   - project/manuscript name, workspace, file changed, bibliography style, and verification status;
   - files inspected;
   - summary of the cleaning process and results;
   - conventions applied;
   - substantive metadata changes with sources;
   - web and working-paper formatting changes;
   - title/capitalization/style cleanup;
   - entry-by-entry changes;
   - original sources checked;
   - publisher-location changes;
   - duplicate-key and database-hygiene changes;
   - entries checked but left unchanged;
   - verification commands and results;
   - remaining warnings or risks.

Do not stop after making edits. Build the manuscript, inspect BibTeX warnings, and report the final state.
