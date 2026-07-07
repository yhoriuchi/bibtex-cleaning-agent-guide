# 2026-07-06 Reference Cleanup by Codex

## Metadata

- Date: 2026-07-06
- Time zone: Asia/Tokyo
- Model: OpenAI Codex GPT-5
- Reasoning level: High
- Project: Takei-Horiuchi
- Manuscript: *When Is Belligerence Costly? A Meta-Analysis of Audience-Cost Experiments*
- Workspace: `/Users/yh25m/Dropbox/Apps/Overleaf/Takei-Horiuchi`
- File changed: `bibfiles/main.bib`
- Documentation file: `project_history/2026-07-06 reference cleanup by Codex.md`
- Scope: BibTeX records currently cited in `main.aux` and `appendix.aux`
- Bibliography style left unchanged: `bibfiles/apsa-leeper.bst`
- Verification: `latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex` completed successfully after the edits.

## Style Basis

- International Organization's Cambridge author instructions say that the reference list should include the complete facts of publication or availability for each source cited, and that IO-style citations are not required at submission as long as citations follow a generally accepted standard. Source: <https://www.cambridge.org/core/journals/international-organization/information/author-instructions/preparing-your-materials>
- Chicago author-date guidance says journal articles should normally include volume, issue, page range, and a DOI-based URL where available. Source: <https://www.chicagomanualofstyle.org/tools_citationguide/citation-guide-2.html>
- For article records with verified online publication but no assigned volume/issue/page range, I used a consistent status label such as `FirstView` or `forthcoming` rather than a placeholder page range.
- Crossref metadata was consulted for several recently published or online-first records. DOI additions are source-data improvements, but this project's current `.bst` does not print article DOI fields in the PDF.

## General Cleanup Applied

- Normalized page ranges from single hyphens or Unicode dashes to BibTeX double hyphens, for example `849-865` to `849--865`.
- Removed stray terminal periods from article titles where the bibliography style already supplies punctuation.
- Changed sentence-style or inconsistent capitalization to title case for cited titles where appropriate.
- Protected acronyms and special terms inside braces, for example `{U.S.}`, `{IR}`, `{US}`, and `{II}`.
- Added missing volume, issue, page, and DOI metadata for published articles where metadata could be verified.
- Reworked unpublished-manuscript entries so the printed bibliography now reads as "Unpublished manuscript. Available from author."
- Converted the Kyiv Independent news item from a technical-report record to a news/article-style record so the output no longer says "Technical report."

## Entry-by-Entry Changes

- `HoriuchiTagoForthcoming`
  - Changed the publication status from a note to the journal/volume fields so the PDF prints `Conflict Management and Peace Science, forthcoming`.
  - Changed `journal = {Conflict Management and Peace Science}` to `journal = {Conflict Management and Peace Science,}` and added `volume = {forthcoming}`. This is a local `.bst` formatting workaround to avoid a stray space before the period.
  - Removed the SSRN note text from the entry.
  - Removed the SSRN DOI `10.2139/ssrn.4186385`, because it is not the journal article DOI.
  - Kept the SSRN URL in the BibTeX data.

- `Fearon1994`
  - Removed the terminal period from the title.

- `Fearon1997`
  - Removed the terminal period from the title.

- `Tomz2007`
  - Removed the terminal period from the title.

- `Partell1999`
  - Changed `pages = {389-405}` to `pages = {389--405}`.
  - Removed the terminal period from the title.

- `Kurizaki2015`
  - Changed `pages = {949-980}` to `pages = {949--980}`.
  - Removed the terminal period from the title.

- `Levy2015`
  - Changed `pages = {988-1001}` to `pages = {988--1001}`.
  - Removed the terminal period from the title.

- `Quek2017`
  - Changed `pages = {1438-1443}` to `pages = {1438--1443}`.
  - Changed `Type II Audience Costs.` to `Type {II} Audience Costs`.

- `Kertzer2016`
  - Changed `pages = {234-249}` to `pages = {234--249}`.
  - Removed the terminal period from the title.

- `Nomikos2019`
  - Changed `pages = {575-588}` to `pages = {575--588}`.
  - Removed the terminal period from the title.

- `LinGreenberg2019`
  - Changed `pages = {559-574}` to `pages = {559--574}`.
  - Removed the terminal period from the title.

- `Trager2011`
  - Changed `pages = {559-574}` to `pages = {559--574}`.
  - Removed the terminal period from the title.

- `Davies2013`
  - Changed `pages = {963-973.}` to `pages = {963--973}`.
  - Changed the title capitalization from `Audience Costs among the British Public: the Impact...` to `Audience Costs among the British Public: The Impact...`.
  - Removed the terminal period from the title.

- `Huddleston2019`
  - Changed `pages = {108-119}` with a Unicode dash to `pages = {108--119}`.
  - Removed the terminal period from the title.

- `Schwartz2020`
  - Changed `pages = {872-895}` to `pages = {872--895}`.
  - Removed the terminal period from the title.

- `Li2021`
  - Changed `pages = {543-560}` to `pages = {543--560}`.
  - Removed the terminal period from the title.

- `Tomz2013`
  - Changed `pages = {849-865}` to `pages = {849--865}`.

- `Levendusky2012`
  - Changed `pages = {323-338}` to `pages = {323--338}`.

- `Kertzer2022`
  - Changed `pages = {539-553}` to `pages = {539--553}`.

- `Fazal2019`
  - Changed `pages = {74-83}` to `pages = {74--83}`.
  - Removed the terminal period from the title.

- `Croco2021`
  - Changed `pages = {8-22}` to `pages = {8--22}`.

- `Dafoe2018`
  - Changed the page range from a Unicode dash to `pages = {399--416}`.

- `Takei2023`
  - Added `Doi = {10.1093/fpa/orad008}`.

- `Takei2023c`
  - Removed the extra period in the title.
  - Changed `type = {{PhD} dissertation.}` to `type = {{PhD} dissertation}`.

- `Bassan-Nygate2025`
  - Protected acronyms in the title: `{IR}` and `{U.S.}`.
  - Standardized author initials: `Jessica LP` to `Jessica L. P.` and `Chagai M` to `Chagai M.`.
  - Did not add a DOI. A Crossref check returned a preprint DOI rather than a verified journal-article DOI.

- `Shandler2025`
  - Added `Volume = {52}`.
  - Added `Number = {2}`.
  - Added `Pages = {270--294}`.
  - Added `Doi = {10.1080/03050629.2025.2478145}`.
  - Kept `Year = {2025}` because the verified online publication date is 2025, even though the issue assignment is 2026.

- `Lee2025`
  - Protected `{US}` in the title.
  - Changed the title to title case.
  - Added `Volume = {46}`.
  - Added `Number = {4}`.
  - Added `Pages = {948--976}`.
  - Added `Doi = {10.1080/13523260.2025.2474872}`.

- `Casler2021`
  - Added `Number = {6}`.
  - Added `Pages = {1098--1130}`.
  - Added `Volume = {65}`.
  - Added `Doi = {10.1177/0022002721994085}`.

- `Quek2016`
  - Changed `pages = {925-940}` to `pages = {925--940}`.

- `Hetherington2003`
  - Changed `pages = {37-42}` to `pages = {37--42}`.

- `Berinsky2021`
  - Changed `pages = {370-384}` to `pages = {370--384}`.

- `Katzenstein1996`
  - Removed the terminal period from the book title.

- `vanBeek2024`
  - Changed the title from `A Preferences-based Theory...` to `A Preferences-Based Theory...`.
  - Changed the record type from `@unpublished` to `@techreport` as a local `.bst` formatting workaround.
  - Removed the old `Institution = {Unpublished manuscript}` field.
  - Replaced the old note-based unpublished status with `Type = {Unpublished manuscript.}` and `Institution = {Available from author}`.
  - The printed bibliography now reads: `A Preferences-Based Theory of Audience Costs. Unpublished manuscript. Available from author.`

- `Cho2017`
  - Changed the record type from `@unpublished` to `@techreport` as a local `.bst` formatting workaround.
  - Removed the old `institution = {Unpublished manuscript}` field.
  - Replaced the old note-based unpublished status with `type = {Unpublished manuscript.}` and `institution = {Available from author}`.
  - The printed bibliography now reads: `Provocation and Audience Costs: An Experimental Approach. Unpublished manuscript. Available from author.`

- `Zadorozhnyy2025`
  - Changed the record type from `@techreport` to `@article`.
  - Replaced `institution = {The Kyiv Independent}` with `journal = {The Kyiv Independent}`.
  - Moved the URL and access date into the note field.
  - Removed the separate URL field.
  - This prevents the bibliography from labeling the news item as a technical report.

- `Mead2014`
  - Changed the title to title case: `The Return of Geopolitics: The Revenge of the Revisionist Powers`.
  - Expanded `Foreign Aff.` to `Foreign Affairs`.
  - Added `number = {3}`.
  - Changed `pages = {69}` to `pages = {69--79}`.
  - Removed the article `publisher` field.

- `NPR2021`
  - Changed title capitalization from `Civilian Casualties In Afghanistan Reach A Record High` to `Civilian Casualties in Afghanistan Reach a Record High`.

- `UNAMA2021`
  - Changed title capitalization from `Afghanistan: Record number of women and children killed or wounded` to `Afghanistan: Record Number of Women and Children Killed or Wounded`.

- `Eichenberg2003`
  - Changed `1990-2003` in the title to `1990--2003`.
  - Changed `author = {Eichenberg, Richard C}` to `author = {Eichenberg, Richard C.}`.

- `Sarkar2026`
  - Changed the title from `Meta-reanalysis` to `Meta-Reanalysis`.
  - Changed the online-first publication status to print as `American Political Science Review, FirstView`.
  - Changed `journal = {American Political Science Review, FirstView}` to `journal = {American Political Science Review,}` and added `volume = {FirstView}`. This is a local `.bst` formatting workaround to avoid a stray space before the period.
  - Removed the temporary online page range `pages = {1--22}` because no final volume/issue page range has been assigned.
  - Removed the article `publisher` field.
  - Added `doi = {10.1017/S0003055426101695}`.

## Verification Notes

- `latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex` completed successfully.
- BibTeX completed without `empty field` warnings after the final unpublished-manuscript adjustments.
- Remaining build warnings are not BibTeX data problems: duplicate citation destinations for `Palmer2016` and `Takei2023` come from separate main and appendix bibliographies, and there are small pre-existing minitoc/overfull-box warnings.
- I did not clean uncited entries in `bibfiles/main.bib`. The file contains many older unused records with single-hyphen page ranges or sentence-style titles, but IO's instructions focus the submitted reference list on directly cited sources.
