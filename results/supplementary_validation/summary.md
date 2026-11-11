# Supplementary validation: short summary

**Design:** 4,000 randomly sampled bot-like accounts (score ≥0.7), compared with 4,000 accounts sampled across seven 0.1 score bands below 0.7. Comparison results use population weights; the lower-score accounts are not verified humans.

**Main result:** the high-score accounts share more URL-containing and media-containing content. These differences remain within retweet and non-retweet subsets. This is independent behavioral evidence of different sharing patterns, but it does not establish that the accounts are automated.

| Mean per-account measure | Bot-like | Comparison, weighted |
| --- | ---: | ---: |
| Share of observed tweets with URL evidence | 72.23% | 47.90% |
| Share of observed tweets with media evidence | 26.56% | 17.84% |
| Share of observed tweets with @mentions | 27.09% | 19.65% |
| Mean @mentions per observed tweet | 1.46 | 0.38 |

**Export correction:** retweet text is often truncated in the main export. All 12,104 sampled native retweets were successfully reconstructed from their embedded original posts. Measures include shared content and exclude the artificial `RT @author` mention. Raw-export results and tweet-type comparisons are retained in the workbook.

**Network/profile descriptions:** these overlap the model’s inputs and therefore are not used as independent validation.

- Recorded handles containing letters and numbers: **46.2% vs 36.5%**. Returned-profile flags use only accounts with available flags.
- Default profile setting, among returned profiles with flag: **90.3% vs 71.6%**. Returned-profile flags use only accounts with available flags.
- Default profile image, among returned profiles with flag: **15.7% vs 5.6%**. Returned-profile flags use only accounts with available flags.
- Median follower/following ratio: **0.163 vs 0.493**. Means (25.30 vs 6.78) are strongly affected by extreme values; zero-following ratios are undefined.

**Saved account status, checked 11 November 2026:**

| Status | Bot-like | Comparison, weighted |
| --- | ---: | ---: |
| public profile returned | 83.50% | 77.78% |
| protected | 1.43% | 3.57% |
| confirmed suspended | 5.75% | 6.09% |
| explicitly deactivated | 0.18% | 0.14% |
| unknown unavailability or lookup error | 9.15% | 12.42% |

Unknown unavailability is not deletion. Recent inactivity, redirects, impersonation and spam were not established from the available records.

The available original-text repetition check shows no clear difference; only 250 bot-like and 61 comparison accounts have at least five original posts for that check.

**Interpretation:** the results are consistent with more link/media-oriented broadcasting among high-score accounts, a pattern that can occur in automated feeds as well as human-operated organizations. They do not establish coordinated behavior, true bot prevalence, or score calibration. Most sampled accounts have only one observed topic-matching tweet, limiting individual behavioral diagnoses.

[Account spreadsheet](supplementary_validation.xlsx) · [Full methods and results](methods.md) · [Bot-like pictures](bot_like_profile_mosaic.jpg) · [Comparison pictures](comparison_profile_mosaic.jpg)
