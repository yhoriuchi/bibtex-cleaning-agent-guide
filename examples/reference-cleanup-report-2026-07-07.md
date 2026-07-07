# Reference Cleanup Report for Journal of Politics Submission

Date checked: July 7, 2026

## Scope

I cleaned the bibliography used by `main.tex` and the appendix through `bibfiles/IHJM_cleaned.bib`, using the generated `main.aux` and `appendix.aux` citation lists as the active manuscript reference set. I also ran a duplicate-key scan over the full `.bib` file because duplicate keys can affect future BibTeX runs even when the duplicate entry is not currently cited.

Conventions applied:

- Article and report titles were normalized to Title Case, with braces added where needed to preserve acronyms such as `{U.S.}`, `{US}`, `{UK}`, `{UN}`, and `{IO}`.
- Web articles and working papers now use `@misc` with a formatted `howpublished` field, following the pattern `\textit{Source}, date when known, available at \url{...}, last accessed July 7, 2026`.
- For online-first journal articles, I used the journal's own online-publication label where applicable. In `durso2025place`, this is represented as `journal = {Political Science Research and Methods,}` and `volume = {FirstView}` so the generated reference reads as FirstView.
- I kept fully published journal articles as `@article`; stable publisher links in Zotero metadata for books or journal articles were not converted into visible web citations.

## Substantive Publication-Status and Metadata Changes

| BibTeX key | Change made | Source or status check |
|---|---|---|
| `horiuchi2025cooperation` | Updated title to `South Korean Democratic Backsliding and American Public Perceptions of the Alliance`; kept as an unpublished working paper; converted to `@misc` with SSRN `howpublished`; retained DOI metadata. | [SSRN DOI 10.2139/ssrn.5718082](https://doi.org/10.2139/ssrn.5718082) |
| `durso2025place` | Changed from `@misc` forthcoming entry to `@article`; set journal to `Political Science Research and Methods,`, volume to `FirstView`, pages to `1--22`, and added DOI. | [Cambridge DOI 10.1017/psrm.2025.10017](https://doi.org/10.1017/psrm.2025.10017) |
| `gidronWhyMassesSupport2025` | Added assigned AJPS issue metadata: volume 70, number 2, pages 720--737, and DOI; normalized title case. | [AJPS DOI 10.1111/ajps.12958](https://doi.org/10.1111/ajps.12958) |
| `inouyeDemocraticSolidarityDoes2025` | Updated year to 2026; kept as an unpublished working paper; converted to `@misc` with SSRN `howpublished`; retained DOI metadata. | [SSRN DOI 10.2139/ssrn.5226460](https://doi.org/10.2139/ssrn.5226460) |
| `inouyeDemocraticBackslidingDamages2026` | Kept as an unpublished working paper; normalized title case; converted to `@misc` with SSRN `howpublished`; retained DOI metadata. | [SSRN DOI 10.2139/ssrn.5610710](https://doi.org/10.2139/ssrn.5610710) |
| `inouyeMoreEqualOthers2025` | Updated title to `More Equal Than Others: Race and Religion Alter Support to Countries in Conflict`; converted to `@misc` with APSA Preprints `howpublished`; retained DOI metadata. | [APSA Preprints DOI 10.33774/apsa-2026-bkpx6-v2](https://doi.org/10.33774/apsa-2026-bkpx6-v2) |
| `appel2024democratic` | Added the cited Working Paper entry and converted it to `@misc` with URL and July 7 access date in `howpublished`. | Working paper URL in entry |
| `TerritorialDiversionDiversionary` | Added pages 413--425 and DOI; normalized title case. | [JOP DOI 10.1017/S0022381609990879](https://doi.org/10.1017/S0022381609990879) |
| `recchiaValidatingThreatIO2021` | Added volume 65, number 4, and DOI; normalized title case. | [ISQ DOI 10.1093/isq/sqab032](https://doi.org/10.1093/isq/sqab032) |
| `henrich2010beyond` | Corrected the entry to the published article `The Weirdest People in the World?`; changed pages to 61--83 and added DOI. | [Behavioral and Brain Sciences DOI 10.1017/S0140525X0999152X](https://doi.org/10.1017/S0140525X0999152X) |
| `ondercoFriendsNeighborsGeographic2025` | Normalized title case and added DOI. | [CMPS DOI 10.1177/07388942251325159](https://doi.org/10.1177/07388942251325159) |
| `phillips2021ethics` | Removed empty `number = {}` field and added DOI. | [Annual Review DOI 10.1146/annurev-polisci-041719-101956](https://doi.org/10.1146/annurev-polisci-041719-101956) |
| `kahlConstructingSeparatePeace1998` | Added volume 8, number 2-3, and pages 94--144. | [Security Studies DOI 10.1080/09636419808429376](https://doi.org/10.1080/09636419808429376) |
| `koch2016death` | Added missing cited journal-article entry with AJPS volume 60, number 4, pages 932--946, and DOI. | [AJPS DOI 10.1111/ajps.12230](https://doi.org/10.1111/ajps.12230) |
| `gilensPoliticalIgnoranceCollective2001` | Added missing cited journal-article entry with APSR volume 95, number 2, pages 379--396, and DOI. | [APSR DOI 10.1017/S0003055401002222](https://doi.org/10.1017/S0003055401002222) |
| `renshonIdentitySocialConstruction2025` | Normalized title case; converted to `@misc`; later added the working-paper URL and July 7, 2026 access date. | [Renshon works-in-progress page](https://www.jonathanrenshon.com/currentwork); [Identity and Reputation page](https://www.jonathanrenshon.com/identity); [linked working paper PDF](https://www.dropbox.com/scl/fi/qpkrnnfw11cw8sbak340w/IdentityAndReputation.pdf?dl=0&rlkey=uzsls2nucvp9d5aoflxsgbui4) |

## Web and Working Paper @misc Formatting

For these active web, news, policy, government, and working-paper entries, I used `@misc` and moved the source, date when known, URL, and access date into `howpublished`. This produces rendered references like: `\textit{The New York Times}, June 14, available at \url{...}, last accessed July 7, 2026`.

| BibTeX key | Main change |
|---|---|
| `rona100InternationalLaw2026` | Converted to `@misc`; `howpublished` now uses Just Security, April, URL, and July 7 access date; preserved `{U.S.}` and `{UN}` capitalization. |
| `USStrikesIran2026` | Converted to `@misc`; `howpublished` now uses Politico, March, URL, and July 7 access date. |
| `naishadhamSpainClosesAirspace2026` | Kept as `@misc`; `howpublished` now uses PBS News, March, URL, and July 7 access date. |
| `govellaWhatAreImplicationsFri03/20/2026-12:00` | Kept as `@misc`; `howpublished` now uses Center for Strategic and International Studies, March 20, URL, and July 7 access date. |
| `hathawayOpinionYouCant2026` | Converted to `@misc`; `howpublished` now uses The New York Times, June 21, URL, and July 7 access date. |
| `boardOpinionAutocracyIndex2026` | Converted to `@misc`; `howpublished` now uses The New York Times, May 13, URL, and July 7 access date. |
| `HeresHowMuch2026` | Kept as `@misc`; removed source suffix from title; `howpublished` now uses Council on Foreign Relations, February, URL, and July 7 access date. |
| `goldsmith2026iranstrike` | Kept as `@misc`; `howpublished` now uses Executive Functions, URL, and July 7 access date. |
| `Rubenstein2026EpicFury` | Kept as `@misc`; `howpublished` now uses U.S. Department of State, Office of the Legal Adviser, April, URL, and July 7 access date. |
| `hathawayOpinionTrumpsStrikes2025` | Converted to `@misc`; fixed malformed URL field; `howpublished` now uses The New York Times, June 23, URL, and July 7 access date. |
| `pewresearchGlobalViewsIran2013` | Kept as `@misc`; `howpublished` now uses Pew Research Center, June 11, URL, and July 7 access date. |
| `shearBritainReinforcesThat2026` | Converted to `@misc`; `howpublished` now uses The New York Times, April 7, URL, and July 7 access date. |
| `WhereAreUS2026` | Converted to `@misc`; `howpublished` now uses The Independent, June, URL, and July 7 access date. |
| `venturaIranWarnsUK2026` | Converted to `@misc`; `howpublished` now uses Time, March 20, URL, and July 7 access date. |
| `UKApprovesUSiranbase` | Kept as `@misc`; `howpublished` now uses Reuters, March 20, URL, and July 7 access date. |
| `ahnIranWarTimeline2026` | Converted to `@misc`; `howpublished` now follows the requested pattern: The New York Times, June 14, URL, and July 7 access date. |
| `TimingImpendingCrude` | Kept as `@misc`; `howpublished` now uses Brookings, May, URL, and July 7 access date. |
| `AsiaEmbracesEnergy` | Kept as `@misc`; `howpublished` now uses CNN, March 25, URL, and July 7 access date. |
| `goldsmithLawIrrelevantUS2026` | Kept as `@misc`; `howpublished` now uses Executive Functions, January, URL, and July 7 access date. |
| `wikeUSImageDeclines2025` | Kept as `@misc`; standardized existing `howpublished` punctuation and access date. |
| `IranWarTurned2026` | Kept as `@misc`; removed source suffix from title; `howpublished` now uses Council on Foreign Relations, June, URL, and July 7 access date. |
| `TrumpRenewsCriticism2026` | Kept as `@misc`; `howpublished` now uses Japan Wire by Kyodo News, April, URL, and July 7 access date. |
| `dailyTrumpPressuresSouth2026` | Kept as `@misc`; `howpublished` now uses The Chosun Daily, May 5, URL, and July 7 access date. |
| `USJapanSouthKoreaTrilateral2024` | Kept as `@misc`; `howpublished` now uses Quincy Institute for Responsible Statecraft, April, URL, and July 7 access date. |
| `schenkkanCenturysNewDemocracy2026` | Kept as `@misc`; corrected title case and replaced separate URL/access fields with `howpublished` using The Century Foundation, URL, and June 30, 2026 access date. |
| `sutherlandWhichCountriesHave2025` | Kept as `@misc`; `howpublished` now uses TIME, November, URL, and July 7 access date. |
| `schneidUSIranWarNumbers2026` | Kept as `@misc`; `howpublished` now uses Time, June 21, URL, and July 7 access date. |
| `robertsonComparingNorthSouth2024` | Kept as `@misc`; `howpublished` now uses Asia Times, November, URL, and July 7 access date. |
| `australiairaqwarinvolvement` | Kept as `@misc`; `howpublished` now uses Anzac Portal, March, URL, and July 7 access date. |
| `tillettTrumpAgainLashes2026` | Kept as `@misc`; `howpublished` now uses Australian Financial Review, April 17, URL, and July 7 access date. |

The generated `.bbl` output now renders these as inline `\url{...}` entries inside the `howpublished` sentence rather than as separate `\harvardurl{...}` lines.

## Other Title and JOP Style Cleanup

| BibTeX key | Change made |
|---|---|
| `groeling2008crossing` | Changed journal from `The journal of politics` to `Journal of Politics`. |
| `peez2025` | Protected `{US}` in the title. |
| `renshonIdentitySocialConstruction2025` | Normalized title case and converted to `@misc` with `howpublished` listing the working-paper URL and July 7, 2026 access date. |

## Publisher Location Normalization

Although recent CMS guidance no longer requires publisher locations, we kept them as the manuscript's preferred house style. I added or normalized locations for all active cited books and book chapters with publishers.

| BibTeX key | Change made |
|---|---|
| `chapman2011securing` | Added `address = {Chicago, IL}` for University of Chicago Press. |
| `thompsonChannelsPowerSecurity2015` | Added `address = {Ithaca, NY}` for Cornell University Press. |
| `recchia2025strategies` | Added `address = {New Haven, CT}` for Yale University Press. |
| `bouldingConflictDefenseGeneral1963` | Split the old `publisher = {New York : Harper}` into `publisher = {Harper}` and `address = {New York, NY}`. |
| `foyle1999counting` | Normalized the multi-place address to `address = {New York, NY}` for Columbia University Press. |
| `mutzImprovingExperimentalTreatments2021` | Corrected `address = {New York, NJ}` to `address = {New York, NY}` for Cambridge University Press. |
| `deutschPoliticalCommunityNorth1957` | Added `address = {Princeton, NJ}` for Princeton University Press. |
| `russettGraspingDemocraticPeace1994` | Added `address = {Princeton, NJ}` for Princeton University Press. |
| `zallerNatureOriginsMass1992a` | Normalized Cambridge University Press address to `address = {New York, NY}`. |
| `mandelbaum1981nuclear` | Added `address = {New York, NY}` for Cambridge University Press. |
| `snyderAlliancePolitics1997` | Normalized `address = {Ithaca, N.Y}` to `address = {Ithaca, NY}` for Cornell University Press. |

## BibTeX Database Hygiene

| BibTeX key or location | Change made |
|---|---|
| `termanPunishmentPoliticizationInternational2022` | Removed duplicate copy of an identical entry. |
| `sabbaghTrumpsTargetingAlleged2025` | Removed duplicate copy of an identical entry. |
| `zegart2007cloaks` | Removed an old `@article` record inside a LaTeX `comment` environment because BibTeX can still scan `@article{...}` there; retained the fuller `@incollection` record. |
| `walshRethinkingFiveEyes2016` | Removed the shorter duplicate entry and retained the fuller entry already present later in the file. |
| before `nye1990bound` | Removed a stray standalone backtick line between BibTeX entries. |

## Checked But Left Unchanged

| BibTeX key | Reason |
|---|---|
| `LessonsLearnedWhat` | I did not find reliable current Crossref metadata matching the existing Australian Army Journal-style entry, so I left the existing volume/issue information unchanged. |

## Verification

Commands/checks run:

- `latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex`
- `bibtex main.aux` and `bibtex appendix.aux` were rerun by `latexmk`.
- Duplicate-key scan over `bibfiles/IHJM_cleaned.bib`: no duplicate keys remain.
- Active book/chapter scan: all cited `@book` and `@incollection` entries with publishers now have publisher locations.
- Rendered-reference spot checks: confirmed that `ahnIranWarTimeline2026`, `USStrikesIran2026`, `horiuchi2025cooperation`, `inouyeDemocraticSolidarityDoes2025`, `inouyeMoreEqualOthers2025`, `Rubenstein2026EpicFury`, and `wikeUSImageDeclines2025` now render in the requested `@misc`/`howpublished` style.
- Warning scan over `main.blg`, `appendix.blg`, and `main.log`: no BibTeX warnings, no undefined citations, and no repeated-entry warnings.

Remaining non-fatal layout warnings in `main.log` are unrelated to bibliography metadata: underfull boxes, one bibliography overfull box caused by a long URL, duplicate PDF destinations for front-matter page numbering, and one duplicate citation anchor involving an appendix citation.
