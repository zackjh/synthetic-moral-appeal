# Synthetic moral appeal

Research on Twitter/X accounts in Ukraine/Russia discussions, combining historical BotometerLite scores, tweet behavior, moral-language measures, and later account status.

## Start here

| What you want | Open |
| --- | --- |
| Short comparison of bot-like and lower-score accounts | [Supplementary summary](results/supplementary_validation/summary.md) |
| Browse or filter the 8,000 sampled accounts | [Account workbook](results/supplementary_validation/supplementary_validation.xlsx) |
| Analyze the sampled accounts programmatically | [Account CSV](results/supplementary_validation/sampled_accounts.csv) |
| Full-dataset relationship between score and suspension | [Suspension report](results/account_status/report.md) |
| Exact suspension statistics and sensitivity tables | [Suspension tables](results/account_status/tables.xlsx) |
| Supplementary methods, limitations, and comparisons | [Supplementary methods](results/supplementary_validation/methods.md) |
| View actual profile pictures | [4,000 bot-like positions](results/supplementary_validation/bot_like_profile_mosaic.jpg) · [4,000 comparison positions](results/supplementary_validation/comparison_profile_mosaic.jpg) |

At the default score threshold of 0.7, high-score accounts do not have higher observed suspension rates among resolved outcomes. The supplementary sample shows more URL/media sharing among high-score accounts. These findings describe score-defined groups; they do not establish bot-classification accuracy or coordinated automation.

## Data

- [Recovered scores](data/bot_scores_recovered.csv): 386,327 accounts with exact IDs, recorded handles, and historical scores.
- [Account statuses](data/account_status.csv): the same 386,327 accounts, checked on **11 November 2026, Asia/Singapore**.
- `data/raw/`: the two original source CSVs, retained locally and gitignored. Tweets span November 2021–December 2022; score records span July 2020–June 2023.

Keep account IDs as strings. Join on exact account IDs, because handles can change or be reused. For the stratified supplementary sample, use the supplied sampling weights when estimating comparison-population averages.

Read the [data dictionary](docs/data_dictionary.md) and [methods, checksums, and provenance](docs/provenance.md) before interpreting fields or planning another analysis.

## Where things live

```text
data/       Final datasets; original inputs in ignored raw/
results/    Reports, workbooks, account CSV, and essential figures
docs/       Data definitions, methods, and research provenance
archive/    Ignored, verified historical working files and code
```

The repo is intentionally organized around final outputs. Scripts, notebooks, raw API responses, cached images, pilots, intermediate exports, and obsolete reports are preserved in the local archive dated **12 November 2026**. Its inventory and restoration instructions are in [the archive guide](archive/2026-11-12/README.md). The archive and original raw data are local files and are not included by Git.

## Questions for the next analysis

- Do high-score accounts show repeated synchronized retweeting beyond chance, accounting for activity, popular content, and news-event timing?
- Do behavioral differences persist with richer observations per account and closer alignment between score dates and tweet dates?
- How do historical score-defined groups differ in moral-language use, with appropriate treatment of retweets, repeated accounts, and sampling weights?
- How sensitive are conclusions to accounts with unknown availability or insufficient behavioral observations?

Network counts, handle patterns, and default-profile settings overlap BotometerLite's inputs, so they remain descriptive comparisons rather than independent validation. Restoration of historical code is available for future work; no scraping or analysis was rerun during this cleanup.
