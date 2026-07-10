---
title: BibTeX Cleaning Agent Guide
---

<link rel="stylesheet" href="assets/site.css">

<main class="page-shell" markdown="1">

<section class="hero" markdown="1">

# BibTeX Cleaning Agent Guide

- **Author:** Yusaku Horiuchi
- **Affiliation:** Syde P. Deeb Eminent Scholar in Political Science, Florida State University
- **Created:** July 7, 2026
- **Last revised:** July 10, 2026

![Page views](https://hits.sh/yhoriuchi.github.io/bibtex-cleaning-agent-guide.svg?label=page%20views)

A source-backed protocol for agentic AI systems that clean BibTeX entries for LaTeX manuscripts without damaging citation style, publication metadata, or rendered references.

If you are starting a new manuscript, consider using my [LaTeX Research Article Template](https://github.com/yhoriuchi/latex-research-article-template) so the bibliography, manuscript structure, and compilation workflow are easier for an agent to inspect and maintain.

<div class="hero-actions" markdown="1">
<button type="button" class="button button-primary" id="copy-agent-instructions">Copy Agent Instructions</button>
<span class="copy-status" id="copy-agent-instructions-status" aria-live="polite"></span>
</div>

</section>

## How to Use This Guide

1. Click **Copy Agent Instructions** and paste the instructions into the agent that will clean the bibliography.
2. Give the agent the manuscript root, active `.tex`, `.aux`, `.bib`, `.bst`, and appendix files, plus the target journal or house style.
3. Tell the agent the access date to use for web sources.
4. Require a cleaned `.bib` file and a detailed Markdown cleanup report.

<section class="summary-grid" markdown="1">

<div class="summary-card" markdown="1">

## What the Agent Must Do

- Work from active citations in `.aux` files.
- Check original sources as much as possible before changing entries.
- Record a checked source for every active citation, or mark it unverified with a reason.
- Preserve the manuscript's style unless the user changes it.
- Apply the style guide's Title Case or sentence-case rule consistently.
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
  <li><strong>Verify metadata.</strong> Check original sources as much as possible: publisher pages, DOI landing pages, Crossref, official preprint servers, institutional pages, news pages, government pages, and cited web pages before changing fields. For every active citation key, record at least one source checked; if no original or strong source can be found or accessed, mark the entry as unverified, explain why, and avoid uncertain metadata changes.</li>
  <li><strong>Normalize by entry type.</strong> Use `@article` for published journal articles, `@book` and `@incollection` for books and chapters, and `@misc` with URLs for unpublished manuscripts, working papers, newspaper articles, web, news, policy, and government sources.</li>
  <li><strong>Protect rendering.</strong> Preserve acronyms such as `{U.S.}`, `{US}`, `{UK}`, `{UN}`, `{EU}`, `{IO}`, and `{NATO}` where BibTeX might downcase them.</li>
  <li><strong>Apply the capitalization rule.</strong> Check the style guide's Title Case versus sentence-case convention and apply it consistently.</li>
  <li><strong>Build and inspect.</strong> Run the manuscript build, rerun BibTeX as needed, inspect `.blg` and `.log` files, and spot-check rendered references.</li>
  <li><strong>Report every decision.</strong> The final Markdown report should document substantive metadata changes, style cleanup, duplicate handling, verification commands, and remaining risks.</li>
</ol>

## Recommended Web Citation Pattern

Use `@misc` for unpublished manuscripts, working papers, preprints, newspaper articles, policy sources, government pages, and ordinary web records. Add a public URL in `howpublished` whenever one exists, especially when the bibliography style renders separate `url` fields poorly.

```text
@misc{key,
  author       = {...},
  title        = {...},
  year         = {...},
  howpublished = {\textit{The New York Times}, June 14, available at \url{https://...}, last accessed Month Day, Year}
}
```

For working papers and preprints with DOIs, keep the DOI while formatting the source and URL in `howpublished`.

```text
@misc{key,
  author       = {...},
  title        = {...},
  year         = {...},
  howpublished = {\textit{SSRN}, available at \url{https://...}, last accessed Month Day, Year},
  doi          = {10.2139/ssrn.0000000}
}
```

## Online-First Journal Articles

For articles that are published online before final volume, issue, or page numbers are assigned, default to a journal-name comma plus `volume = {forthcoming}`. The comma after the journal name is intentional for local `.bst` rendering and should not be removed as a typo.

```text
@article{Horiuchi2026Civilian,
  author  = {Horiuchi, Yusaku and Tago, Atsushi},
  title   = {Civilian Control and Casualty Sensitivity in a Pacifist Democracy: Evidence from Japan's 2021 Evacuation Mission},
  journal = {Conflict Management and Peace Science,},
  volume  = {forthcoming},
  year    = {2026}
}
```

Use `forthcoming` as the default status label. Users may choose `FirstView`, `Advance online publication`, or an equivalent publisher-specific label when that better matches the journal's terminology.

## Metadata Evidence Hierarchy

1. Original publisher, journal, book, preprint, institutional, government, news, or web landing page.
2. DOI resolver landing page.
3. Crossref, DataCite, PubMed, JSTOR, Cambridge, Oxford, Wiley, SAGE, Taylor & Francis, Elsevier, Springer, or another publisher database.
4. Official book publisher page or library catalog.
5. Official institutional, government, think-tank, preprint, SSRN, APSA Preprints, arXiv, OSF, or author page.
6. The cited web page itself.
7. Reliable news or archival sources.

Do not rely only on citation aggregators, Zotero imports, Google Scholar, or copied BibTeX records when an original source or stronger source exists.

A bibliography cleanup is not complete unless every active citation is either verified against a recorded source or explicitly listed as unverified with a reason.

## Style Rules Worth Making Explicit

- Check whether the target style requires Title Case or sentence case; normalize titles to that style while preserving acronyms and proper nouns with braces.
- Remove imported website suffixes from titles.
- Normalize page ranges to `--`.
- Store DOI values without `https://doi.org/`.
- Remove empty fields such as `number = {}`.
- For online-first articles without final issue/page metadata, keep `journal = {Journal Name,}` and put `forthcoming`, `FirstView`, or the chosen equivalent in `volume`.
- Preserve existing BibTeX keys unless resolving duplicate-key conflicts.
- Keep stable publisher links for books and journal articles out of visible web-citation fields unless the target style requires them.
- Add publisher locations for books and chapters unless the style guide explicitly omits them, so rendered references can show forms such as `New York, NY: Cambridge University Press`.

## Verification Checklist

```text
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

Every cleanup run should produce a detailed Markdown report. This is important for provenance: the user should be able to see which AI system did the work, how much reasoning was requested, which sources were checked, and what changed entry by entry.

The final cleanup report should include:

- date checked and access date used;
- AI model and reasoning level or intelligence setting, such as `OpenAI Codex GPT-5.5` and `Extra High`;
- project/manuscript name, workspace, file changed, bibliography style, and verification status;
- scope and files inspected;
- summary of the cleaning process and results;
- conventions applied;
- substantive publication-status and metadata changes;
- web and working-paper formatting changes;
- title, capitalization, and style cleanup;
- entry-by-entry changes;
- active-citation source audit, with citation key, active status, source checked, URL or DOI, fields verified, changes made, and remaining uncertainty;
- original sources checked;
- publisher-location normalization;
- duplicate-key and database-hygiene changes;
- entries checked but left unchanged;
- verification commands and results;
- remaining warnings or risks.

<script id="agent-instructions-text" type="text/plain">{% include_relative AGENTS.md %}</script>
<script>
(function () {
  var button = document.getElementById("copy-agent-instructions");
  var source = document.getElementById("agent-instructions-text");
  var status = document.getElementById("copy-agent-instructions-status");

  if (!button || !source) {
    return;
  }

  function setStatus(message) {
    if (!status) {
      return;
    }
    status.textContent = message;
    window.clearTimeout(setStatus.timeout);
    setStatus.timeout = window.setTimeout(function () {
      status.textContent = "";
    }, 2400);
  }

  function fallbackCopy(text) {
    var textarea = document.createElement("textarea");
    textarea.value = text;
    textarea.setAttribute("readonly", "");
    textarea.style.position = "fixed";
    textarea.style.top = "-9999px";
    document.body.appendChild(textarea);
    textarea.select();
    document.execCommand("copy");
    document.body.removeChild(textarea);
  }

  button.addEventListener("click", function () {
    var text = source.textContent.trim();

    if (navigator.clipboard && window.isSecureContext) {
      navigator.clipboard.writeText(text).then(function () {
        setStatus("Copied");
      }).catch(function () {
        fallbackCopy(text);
        setStatus("Copied");
      });
      return;
    }

    fallbackCopy(text);
    setStatus("Copied");
  });
})();
</script>

</main>
