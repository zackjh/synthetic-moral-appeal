# Methods and provenance

Cleanup date: **12 November 2026, Asia/Singapore**. This file consolidates the final identity, collection, and validation findings. Detailed original records remain in the local archive. Cleanup moved and packaged outputs without rerunning scraping, image retrieval, or statistical analysis.

## Sources and identity recovery

The original tweet CSV contains **945,686 tweets and 131 fields**, covering November 2021–December 2022. The original kc score CSV contains **389,142 records**, with associated timestamps spanning July 2020–June 2023. The exact source collection queries and the original score timestamp semantics are not documented locally.

The recovered account dataset contains **386,327 unique exact numeric-string IDs**. It retains 206,648 originally integer-form IDs and 179,679 IDs recovered from historical tweet authors. Recovery required a single historical handle-to-ID match consistent with the exported ID's original decimal rounding precision. Converting rounded scientific notation directly to an integer cannot recover an ID.

Excluded: **2,809 unresolved IDs** and all **six records** for the three ambiguous duplicated handles `NewsDigestNGR`, `Rus_Government`, and `paularsweet`. The final audit found no missing IDs, duplicate IDs, altered scores, or tweet author-ID disagreements. All retained IDs occur in the historical tweet export. Eleven malformed recorded handles were retained because their exact IDs are supported. There are 1,496 recorded handles that differ from the historical tweet username for the same ID.

The separate 38-case identity investigation found **38 current handles resolving to different numeric IDs and zero exact ID matches**. All 38 historical ID/handle pairs were supported by the tweet export; these were not rounded-ID recovery cases. This supports handle reuse or replacement account objects, not the transfer of an old score to a new account. It does not establish whether the human owner is the same. The current-handle results came from two endpoints of the same provider, so they are consistency checks rather than independent authentication by X.

Use exact IDs for all status linkage. Do not replace historical IDs with current accounts merely because the handles match.

## Account-status collection

Final output: **386,327 rows**, preserving ID strings, scores and row order. The bulk pass used 773 logical batches and 786 successful HTTP requests. A later five-ID diagnostic and 76,024 authorized individual follow-ups resolved the unassigned bulk outcomes.

The main bulk-pass observations ran from **11 November 2026, 03:38:00 to 03:54:46 Singapore time**; recovery and diagnostic requests continued afterward. Individual follow-up ran from **11 November 2026, 04:48:21 to 14:02:40 Singapore time**. The final source summary's UTC timestamps and per-account observations remain archived. The supplementary account table retains exact per-account check times.

| Current label | Rows |
| --- | ---: |
| `active` | 297,743 |
| `protected` | 12,568 |
| `suspended` | 23,864 |
| `unavailable_reason_unknown` | 51,609 |
| `deactivated` | 542 |
| `lookup_error` | 1 |

### Status interpretation

- **Active:** a public profile was returned with a matching numeric ID; this does not establish recent posting.
- **Protected:** an identified private/protected profile was returned.
- **Suspended:** an explicit suspension result was attributable to the queried ID; it does not establish lifetime or permanent suspension.
- **Deactivated:** an explicit provider deactivation message was returned; permanent deletion is not established.
- **Unknown unavailability:** a successful individual response returned an empty/unavailable result without an attributable cause; it is neither confirmed suspension nor deletion.
- **Lookup error:** a request failed after retries. Only ID `1898575466` remains in this category after six historical attempts; other accounts are not inferred to share that error.

Classification version 2 corrected **542 unknown labels to `deactivated`** using explicit `User is deactivated` messages in existing records. Exactly those labels changed; reversing them reproduces the previous CSV checksum. IDs, scores, other statuses and raw responses were preserved. No new API requests were needed for the correction.

Raw provider evidence and billing records are archived. The completed individual follow-up cost **US$7.6024**; the separate five-ID diagnostic cost US$0.0004. Recorded successful bulk-response headers total US$0.0786 and may exclude failed attempts. None of these are cleanup charges.

## Full-dataset suspension analysis

The primary comparison uses **334,175 resolved accounts**: suspended versus active/protected. It excludes 51,609 unknown-unavailable accounts, one lookup error and 542 distinct deactivations. The default threshold is 0.7; other thresholds are exploratory. The full report documents risk ratios, risk differences, confidence intervals, multiplicity adjustment, score-band nonlinearity and unknown-outcome sensitivity.

All six final statistical CSV tables have been consolidated without recalculation into the [suspension workbook](../results/account_status/tables.xlsx), with continuous-score metrics, original validation values, collection metadata and source checksums. The archived separate CSVs are recoverable if machine-readable exports are needed later.

## Supplementary sampling and behavior

**4,000 bot-like accounts** were sampled uniformly without replacement from 5,734 eligible accounts scoring at least 0.7. **4,000 comparison accounts** were sampled nearly equally across seven 0.1 bands below 0.7: 572 from each of the first three bands and 571 from each remaining band. Seed: **20261112**. Design weights are stratum population divided by stratum sample; comparison estimates restore the eligible below-0.7 population of 380,593 accounts. Lower-score accounts are not verified humans.

The sample contains **22,113 observed tweets**. All **12,104 native retweets** were reconstructed from their embedded original posts because the main export frequently truncates their text and omits their URL/media fields. Only the top-level retweeted post supplies shared-content measures; synthetic `RT @author` mentions are excluded. Replies and quotes do not inherit unrelated parent-post content. Raw-export and within-tweet-type sensitivities remain in the workbook.

Primary outcomes are per-account URL share, media share, content-mention share, and mentions per tweet. Missing evidence is not a proven absence in the original platform record. Statistical uncertainty uses stratified sampling without replacement, finite-population corrections and account-level variance; Holm adjustment covers the four primary outcomes. Pooled tweet rates answer a different question and have their own workbook sheet.

Follower/following data are historical profile fields attached to the latest observed tweet record; that tweet's timestamp is not proof of when profile metadata was collected. Network and handle characteristics overlap published Lite inputs and are descriptive rather than independent validation. No recent inactivity, redirects, impersonation or spam judgments were invented.

The picture mosaics each retain 4,000 positions: **3,626 bot-like pictures** and **3,481 comparison pictures** were retrieved on 12 November 2026. Remaining positions are marked unavailable. Historical image URLs were preferred; saved 2026 profile URLs were fallbacks. Download failure does not establish a default avatar, unavailable account or automation. The comparison mosaic depicts the balanced raw sample rather than the population-weighted distribution.

The final independent validation checked all 8,000 accounts, eight primary group means, 6,085 cached image files and exact workbook/CSV ID agreement. It passed, with a maximum mean discrepancy below 4e-12. These historical validation results are preserved; the cleanup acceptance checks cover file integrity and packaging, not a rerun of those analyses.

## Checksums of unchanged datasets

These hashes identify the exact retained files. Paths changed where noted; file contents did not.

| Current path | SHA-256 |
| --- | --- |
| `data/raw/English_100_vectionary_scored.csv` | `02ccfa09a846963be2c48fe0cf653527dedadadf3193e055506f87930d0a12f8` |
| `data/raw/Ukriane_bot_scores_unique_handles_kc.csv` | `e985a03992287b68126967fd359479f54bc90e100de6daf763fd1f6954b6f82f` |
| `data/bot_scores_recovered.csv` | `2d37c7c41a73e923c809180c149c699ced7794331c2fc2f7576d9fdf62886347` |
| `data/account_status.csv` | `71cd82e397445803332ecb481fe1f2dd0497f018d74369748cdf595197c2cb6f` |
| `results/supplementary_validation/sampled_accounts.csv` | `8e97ecfa12ba3f9e8ab17898312786cadc924a33395e50a17fef4d3e54430552` |

## Archived evidence and reproduction

The gitignored local archive is `archive/2026-11-12/research_history.tar.gz`. It preserves **83,130 files** under their original repository-relative paths, including original final deliverables, scripts, notebooks, separate table exports, raw API responses, intermediate snapshots, audit records, logs and cached pictures. Its per-file inventory is `inventory.csv.gz`; the archive and inventory have checksums in `SHA256SUMS`.

**Stored evidence paths are historical references.** Paths in the unchanged account CSV, supplementary workbook, source manifests and audit records refer to members inside that archive. For example, a saved path beginning `tasks/account_status/individual_followup/responses/` is found at that same member path inside the archive. Relative `avatar_cache/...` references are relative to the archived supplementary-validation directory. These are intentionally not rewritten inside byte-preserved deliverables. Sample mosaic slots/rows/columns remain usable with the retained full-resolution mosaics.

Scripts and notebooks have been retired from active research folders, not discarded. To reproduce an old analysis, restore the original layout into the ignored restoration directory and link the retained raw source inputs there. The [archive guide](../archive/2026-11-12/README.md) gives exact instructions. Analysis reproduction is separate from restoring historical collection jobs; no jobs run as part of restoration.

The archive and original source inputs are local-only and are not included in Git. The canonical visible results are the reports, final datasets, existing supplementary workbook and newly consolidated suspension workbook. Neither credentials, Git internals nor the existing Python environment were moved or included in the archive.
