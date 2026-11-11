# Dataset overview

The two files in [`data/raw/`](../data/raw/) contain Twitter/X posts with Vectionary moral-language scores and a separate set of account-level BotometerLite scores. Together, they support comparisons of moral language and posting behavior across accounts with different bot scores.

## `English_100_vectionary_scored.csv`

[File](../data/raw/English_100_vectionary_scored.csv) · approximately 6.3 GiB · **945,686 rows and 131 fields**.

Each row represents one tweet, with its text, engagement counts, posting-account profile, and available reply, reference, media, and location metadata. The file also includes cleaned text and 25 Vectionary scores: five measures for each of care, fairness, loyalty, authority, and sanctity. The content concerns Ukraine/Russia; the exact collection queries and sampling procedure are not documented locally.

Tweets span **1 November 2021–31 December 2022 (UTC)** and cover **390,809 author handles**. Despite the filename, the language labels are not exclusively English: 945,611 rows are labeled `en`, and 75 have other labels. Most rows are retweets (721,781); replies, quotes, and original tweets are also included.

### Fields

Every field is listed below, grouped for readability. Examples are observed values from the existing full-file profile; long text and serialized structures are shortened. Examples across fields need not come from the same row. `Blank` indicates no populated value was found.

For profile fields, **posting account** means the tweet author; **reply recipient** means the account being replied to. Lists and dictionaries are stored as serialized text inside CSV cells.

#### Tweet and derived text

| Field | What it contains | Example value |
| --- | --- | --- |
| `Unnamed: 0.1` | Likely saved DataFrame index from a previous export; not a tweet/account identifier. | `0` |
| `Unnamed: 0` | Likely saved DataFrame index from a previous export; not a tweet/account identifier. | `0` |
| `lang` | Tweet language code. | `en` |
| `author_id` | Posting account identifier; compare with author.id, not the tweet id. | `1433514956364845058` |
| `reply_settings` | Who may reply to the tweet (categorical setting). | `everyone` |
| `edit_history_tweet_ids` | Serialized list of tweet identifiers in the edit history. | `['1458577214480474112']` |
| `in_reply_to_user_id` | Identifier of the account to which this tweet replies; absent for non-replies. | `1.0826045074549391e+18` |
| `created_at` | Tweet creation timestamp. | `2021-11-10T23:28:01.000Z` |
| `referenced_tweets` | Serialized references to other tweets, including reference type and identifier. | `[{'type': 'replied_to', 'id': '1458523890628677636', 'lang': 'en', 'author_id': '1...` |
| `text` | Tweet text supplied in the export. | `@Archer83Able This is what happens when you let a warmongering dictator invade and...` |
| `conversation_id` | Root tweet/conversation identifier. | `1458522456407293960` |
| `possibly_sensitive` | Flag marking potentially sensitive tweet content. | `False` |
| `id` | Tweet identifier; not an account identifier. | `1458577214480474112` |
| `text_full` | Derived/full tweet text; assembly and relation to text are undocumented. | `@Archer83Able This is what happens when you let a warmongering dictator invade and...` |
| `textual_url_number` | Derived count of URLs in text; extraction rules are undocumented. | `0.0` |
| `tweet_clean_list` | Serialized cleaned-token list used for scoring; preprocessing rules are undocumented. | `['Archer83Able', 'happens', 'let', 'warmongering', 'dictator', 'invade', 'steal', ...` |
| `effective_word_count` | Derived number of effective words used for scoring; inclusion rules are undocumented. | `23` |

#### Tweet engagement

| Field | What it contains | Example value |
| --- | --- | --- |
| `public_metrics.retweet_count` | Number of retweets. | `0` |
| `public_metrics.reply_count` | Number of replies. | `1` |
| `public_metrics.like_count` | Number of likes. | `0` |
| `public_metrics.quote_count` | Number of quote tweets. | `0` |
| `public_metrics.impression_count` | Number of impressions, when supplied; missing does not mean zero. | `0` |

#### Posting account

| Field | What it contains | Example value |
| --- | --- | --- |
| `author.verified` | Posting account: verification flag at collection time. | `False` |
| `author.username` | Posting account: account handle; candidate for matching to bot-score screen_name after normalization. | `Wetlettuce70` |
| `author.created_at` | Posting account: account creation timestamp, not tweet creation time. | `2021-09-02T19:40:18.000Z` |
| `author.public_metrics.followers_count` | Posting account: number of followers. | `67` |
| `author.public_metrics.following_count` | Posting account: number of accounts followed. | `213` |
| `author.public_metrics.tweet_count` | Posting account: number of posts reported for the account. | `3676` |
| `author.public_metrics.listed_count` | Posting account: number of public lists containing the account. | `0` |
| `author.description` | Posting account: profile biography text. | `Anti-Moronist\nI never tolerate neither moronism nor aberrant morons/Contemporary ...` |
| `author.name` | Posting account: profile display name; not a unique identifier. | `David Leach` |
| `author.protected` | Posting account: whether the account's posts were protected at collection time. | `False` |
| `author.id` | Posting account: account identifier, stored as text to preserve the exported value. | `1433514956364845058` |
| `author.profile_image_url` | Posting account: profile image URL; not itself a default-image flag. | `https://pbs.twimg.com/profile_images/1574217635293790208/xgVAopg4_normal.jpg` |
| `author.location` | Posting account: free-form, self-reported profile location; not verified geolocation. | `Manc Land` |
| `author.pinned_tweet_id` | Posting account: pinned tweet identifier, when provided. | `1.4241879259993743e+18` |
| `author.entities.description.mentions` | Posting account: profile biography: Serialized account mentions in text. | `[{'start': 146, 'end': 160, 'username': 'wanderer44772'}]` |
| `author.entities.description.hashtags` | Posting account: profile biography: Serialized hashtags in text. | `[{'start': 0, 'end': 10, 'tag': 'Gratitude'}, {'start': 11, 'end': 26, 'tag': 'All...` |
| `author.entities.url.urls` | Posting account: serialized URL metadata for the profile website. | `[{'start': 0, 'end': 23, 'url': 'https://t.co/Jc29vG8Tib', 'expanded_url': 'http:/...` |
| `author.url` | Posting account: profile website URL. | `https://t.co/Jc29vG8Tib` |
| `author.entities.description.urls` | Posting account: profile biography: Serialized URL entities and associated metadata. | `[{'start': 118, 'end': 141, 'url': 'https://t.co/KZM9HSzfX7', 'expanded_url': 'htt...` |
| `author.entities.description.cashtags` | Posting account: profile biography: Serialized financial ticker/cashtag entities in text. | `[{'start': 131, 'end': 135, 'tag': 'EGC'}]` |
| `author.withheld.country_codes` | Posting account: serialized country codes where account content is withheld. | `['IN']` |

#### Reply recipient

| Field | What it contains | Example value |
| --- | --- | --- |
| `in_reply_to_user.verified` | Reply recipient: verification flag at collection time. | `False` |
| `in_reply_to_user.username` | Reply recipient: account handle; candidate for matching to bot-score screen_name after normalization. | `Archer83Able` |
| `in_reply_to_user.created_at` | Reply recipient: account creation timestamp, not tweet creation time. | `2019-01-08T11:46:43.000Z` |
| `in_reply_to_user.public_metrics.followers_count` | Reply recipient: number of followers. | `121215.0` |
| `in_reply_to_user.public_metrics.following_count` | Reply recipient: number of accounts followed. | `1241.0` |
| `in_reply_to_user.public_metrics.tweet_count` | Reply recipient: number of posts reported for the account. | `39400.0` |
| `in_reply_to_user.public_metrics.listed_count` | Reply recipient: number of public lists containing the account. | `3100.0` |
| `in_reply_to_user.description` | Reply recipient: profile biography text. | `Providing in-depth news coverage about the armed conflicts and crises all around t...` |
| `in_reply_to_user.pinned_tweet_id` | Reply recipient: pinned tweet identifier, when provided. | `1.42347421660783e+18` |
| `in_reply_to_user.name` | Reply recipient: profile display name; not a unique identifier. | `Status-6` |
| `in_reply_to_user.protected` | Reply recipient: whether the account's posts were protected at collection time. | `False` |
| `in_reply_to_user.id` | Reply recipient: account identifier, stored as text to preserve the exported value. | `1.0826045074549391e+18` |
| `in_reply_to_user.profile_image_url` | Reply recipient: profile image URL; not itself a default-image flag. | `https://pbs.twimg.com/profile_images/1613909869010059266/2gkxgULI_normal.jpg` |
| `in_reply_to_user.location` | Reply recipient: free-form, self-reported profile location; not verified geolocation. | `Backup: @Archer84Able` |
| `in_reply_to_user.entities.description.mentions` | Reply recipient: profile biography: Serialized account mentions in text. | `[{'start': 146, 'end': 160, 'username': 'wanderer44772'}]` |
| `in_reply_to_user.url` | Reply recipient: profile website URL. | `https://t.co/WKTySa4gWc` |
| `in_reply_to_user.entities.url.urls` | Reply recipient: serialized URL metadata for the profile website. | `[{'start': 0, 'end': 23, 'url': 'https://t.co/WKTySa4gWc', 'expanded_url': 'https:...` |
| `in_reply_to_user.entities.description.urls` | Reply recipient: profile biography: Serialized URL entities and associated metadata. | `[{'start': 103, 'end': 126, 'url': 'https://t.co/gv1AOufYIR', 'expanded_url': 'htt...` |
| `in_reply_to_user.entities.description.hashtags` | Reply recipient: profile biography: Serialized hashtags in text. | `[{'start': 20, 'end': 27, 'tag': 'Russia'}, {'start': 28, 'end': 39, 'tag': 'fuckc...` |
| `in_reply_to_user.withheld.country_codes` | Reply recipient: serialized country codes where account content is withheld. | `['AT', 'BE', 'BG', 'CY', 'CZ', 'DE', 'DK', 'EE', 'ES', 'FI', 'FR', 'GB', 'GR', 'HR...` |
| `in_reply_to_user.entities.description.cashtags` | Reply recipient: profile biography: Serialized financial ticker/cashtag entities in text. | `[{'start': 0, 'end': 5, 'tag': 'TSLQ'}]` |

#### Referenced tweets

| Field | What it contains | Example value |
| --- | --- | --- |
| `referenced_tweets.text` | Text of referenced tweet(s). | `US Secretary of State Blinken: "Our concern is that Moscow may make the serious mi...` |
| `referenced_tweets.type` | Relationship/category: original, replied_to, quoted, retweeted, or combined relationships. | `replied_to` |
| `referenced_tweets.id` | Referenced tweet identifier(s), not posting account identifiers. | `1458523890628677636` |
| `referenced_tweets.author_id` | Account identifier(s) of referenced tweet authors. | `1082604507454939137` |
| `referenced_tweets.possibly_sensitive` | Sensitivity flag for referenced tweet(s). | `False` |
| `referenced_tweets.conversation_id` | Conversation identifier(s) of referenced tweet(s). | `1458522456407293960` |
| `referenced_tweets.lang` | Language code(s) of referenced tweet(s). | `en` |
| `referenced_tweets.source` | Source/client information for referenced tweet(s), as exported. | Blank |
| `referenced_tweets.reply_settings` | Reply permissions for referenced tweet(s). | `everyone` |
| `referenced_tweets.entities` | Serialized entities in referenced tweet(s). | `{'annotations': [{'start': 0, 'end': 1, 'probability': 0.5114, 'type': 'Place', 'n...` |
| `referenced_tweets.public_metrics` | Serialized engagement metrics for referenced tweet(s). | `{'retweet_count': 8, 'reply_count': 4, 'like_count': 37, 'quote_count': 8, 'impres...` |
| `referenced_tweets.attachments` | Serialized attachments for referenced tweet(s). | `{'media_keys': ['7_1458608537425223687'], 'media': [{}]}` |
| `referenced_tweets.author` | Serialized referenced-author metadata; distinct from the posting author. | `{'verified': False, 'username': 'Archer83Able', 'created_at': '2019-01-08T11:46:43...` |

#### Tweet entities

| Field | What it contains | Example value |
| --- | --- | --- |
| `entities.annotations` | Serialized annotations of named entities/topics detected in text. | `[{'start': 89, 'end': 94, 'probability': 0.9729, 'type': 'Place', 'normalized_text...` |
| `entities.mentions` | Serialized account mentions in text. | `[{'start': 0, 'end': 13, 'username': 'Archer83Able', 'id': '1082604507454939137', ...` |
| `entities.hashtags` | Serialized hashtags in text. | `[{'start': 249, 'end': 257, 'tag': 'Ukraine'}, {'start': 258, 'end': 280, 'tag': '...` |
| `entities.urls.expanded_url` | Exported expanded URL value(s); representation may be serialized. | `https://twitter.com/JohnAllenGay/status/1458853703503466500` |
| `entities.urls.expanded_url_total_number` | Derived count of expanded URLs; export counting rules are undocumented. | `1.0` |
| `entities.urls` | Serialized URL entities and associated metadata. | `[{'start': 167, 'end': 190, 'url': 'https://t.co/YjgiFPY4xP', 'expanded_url': 'htt...` |
| `entities.cashtags` | Serialized financial ticker/cashtag entities in text. | `[{'start': 129, 'end': 133, 'tag': 'BTC'}]` |

#### Attachments

| Field | What it contains | Example value |
| --- | --- | --- |
| `attachments.media.urls` | Exported media URL value(s). | `0.0` |
| `attachments.media.url_total_number` | Derived count of media URLs; not necessarily number of attachments. | `0` |
| `attachments.media_keys` | Serialized media identifiers. | `['3_1459626802494652417']` |
| `attachments.media` | Serialized media metadata. | `[{'media_key': '3_1459626802494652417', 'height': 1370, 'width': 819, 'url': 'http...` |
| `attachments.media.type` | Exported media type(s), such as photo or video. | `photo` |
| `attachments.media.url` | Exported media URL field; often contains the literal value 0. | `0` |
| `attachments.poll_ids` | Serialized poll identifiers. | `['1476412217717411843']` |
| `attachments.poll.id` | Expanded poll identifier. | `1.4764122177174118e+18` |
| `attachments.poll.options` | Serialized poll options and associated metadata. | `[{'position': 1, 'label': 'Nuclear Disarmament', 'votes': 1}, {'position': 2, 'lab...` |

#### Geography and withholding

| Field | What it contains | Example value |
| --- | --- | --- |
| `geo.place_id` | Place identifier associated with the tweet. | `4ff0fc2a304db9ad` |
| `geo.id` | Identifier of the expanded place object. | `4ff0fc2a304db9ad` |
| `geo.full_name` | Full place name. | `Oak Ridge, TN` |
| `geo.country` | Country name of the place. | `United States` |
| `geo.geo.type` | Geometry type for the place boundary. | `Feature` |
| `geo.geo.bbox` | Serialized geographic bounding box for the place. | `[-84.347226, 35.962375, -84.1656902, 36.073648]` |
| `geo.name` | Short place name. | `Oak Ridge` |
| `geo.country_code` | Country code of the place. | `US` |
| `geo.place_type` | Category of place, e.g. city. | `city` |
| `geo.coordinates.type` | Geometry type of tweet coordinates. | `Point` |
| `geo.coordinates.coordinates` | Serialized tweet coordinate values; coordinate order requires schema confirmation. | `[-77.0253474, 38.9394606]` |
| `withheld.copyright` | Flag indicating withholding due to a copyright complaint. | `False` |
| `withheld.country_codes` | Serialized country codes where the tweet is withheld. | `['IN']` |

#### Vectionary moral scores

Descriptions of these measures are inferred from their names. Exact formulas, normalization, preprocessing, and theoretical score bounds are not documented in the repository. Positive/negative refer to moral virtue/vice components, rather than general sentiment.

| Field | What it contains | Example value |
| --- | --- | --- |
| `care_valence` | Vectionary care versus harm: signed moral orientation. | `-0.095` |
| `care_positive` | Vectionary care versus harm: positive/virtue component. | `0.0002` |
| `care_negative` | Vectionary care versus harm: negative/vice component. | `0.0952` |
| `care_strength` | Vectionary care versus harm: overall moral signal strength. | `0.0954` |
| `care_ambivalence` | Vectionary care versus harm: co-occurrence or balance of positive and negative signals. | `0.0048` |
| `fairness_valence` | Vectionary fairness versus cheating: signed moral orientation. | `-0.0465` |
| `fairness_positive` | Vectionary fairness versus cheating: positive/virtue component. | `0.0082` |
| `fairness_negative` | Vectionary fairness versus cheating: negative/vice component. | `0.0547` |
| `fairness_strength` | Vectionary fairness versus cheating: overall moral signal strength. | `0.0628` |
| `fairness_ambivalence` | Vectionary fairness versus cheating: co-occurrence or balance of positive and negative signals. | `0.0038` |
| `loyalty_valence` | Vectionary loyalty versus betrayal: signed moral orientation. | `-0.0519` |
| `loyalty_positive` | Vectionary loyalty versus betrayal: positive/virtue component. | `0.0053` |
| `loyalty_negative` | Vectionary loyalty versus betrayal: negative/vice component. | `0.0573` |
| `loyalty_strength` | Vectionary loyalty versus betrayal: overall moral signal strength. | `0.0626` |
| `loyalty_ambivalence` | Vectionary loyalty versus betrayal: co-occurrence or balance of positive and negative signals. | `0.0035` |
| `authority_valence` | Vectionary authority versus subversion: signed moral orientation. | `-0.0246` |
| `authority_positive` | Vectionary authority versus subversion: positive/virtue component. | `0.0199` |
| `authority_negative` | Vectionary authority versus subversion: negative/vice component. | `0.0445` |
| `authority_strength` | Vectionary authority versus subversion: overall moral signal strength. | `0.0643` |
| `authority_ambivalence` | Vectionary authority versus subversion: co-occurrence or balance of positive and negative signals. | `0.0051` |
| `sanctity_valence` | Vectionary sanctity/purity versus degradation: signed moral orientation. | `-0.0601` |
| `sanctity_positive` | Vectionary sanctity/purity versus degradation: positive/virtue component. | `0.0011` |
| `sanctity_negative` | Vectionary sanctity/purity versus degradation: negative/vice component. | `0.0612` |
| `sanctity_strength` | Vectionary sanctity/purity versus degradation: overall moral signal strength. | `0.0624` |
| `sanctity_ambivalence` | Vectionary sanctity/purity versus degradation: co-occurrence or balance of positive and negative signals. | `0.0022` |

### Important notes

- Tweet IDs (`id`) identify posts; `author_id` and `author.id` identify posting accounts and agree throughout this file. Treat identifiers as strings. Some other identifier fields already contain decimal/scientific-notation values, so string loading alone cannot recover lost precision.
- Reply, reference, media, poll, and geographic fields are often blank. `referenced_tweets.source` is blank throughout. Blank metadata does not establish that a feature was absent, and a blank count should not automatically become zero.
- Account profiles and engagement counts describe collection snapshots. They do not necessarily describe the account today or at the exact time the tweet was written. Profile locations are self-reported.
- `Unnamed: 0.1` and `Unnamed: 0` appear to be saved export indexes, rather than substantive variables. The construction of `text_full`, cleaned tokens, and derived URL counts is not documented.
- The large CSV contains embedded newlines and bare carriage returns in profile text. The local notebooks read it in chunks and normalize carriage returns in parser input; their audited parse produces 945,686 records with 131 fields each. Use that approach if a default CSV reader splits records incorrectly.

## `Ukriane_bot_scores_unique_handles_kc.csv`

[File](../data/raw/Ukriane_bot_scores_unique_handles_kc.csv) · approximately 20.4 MiB · **389,142 rows and 4 fields**.

Each row contains an account identifier, handle, timestamp, and BotometerLite score. The file has **389,139 distinct handles** and no blank fields. Scores observed in the file range from **0 to 1**, with higher values interpreted as more bot-like. Recorded timestamps span **30 July 2020–1 June 2023 (UTC)**; the precise timestamp semantics are not documented locally.

| Field | What it contains | Example value |
| --- | --- | --- |
| `user_id` | Exported Twitter/X account ID; many large IDs appear rounded in scientific notation. | `324` (also values such as `1.43351E+18`) |
| `screen_name` | Account handle, without a leading @; candidate key for linking to tweet authors. | `chrisfralic` |
| `time_stamp` | UTC timestamp associated with the score record; not a tweet creation date. | `2023-05-29 19:24:27+00:00` |
| `botometerlite_score` | Numeric BotometerLite account score, used as an indicator of bot-like behavior. | `0.12` |

### Important notes

- Despite the filename, three handles occur twice: `NewsDigestNGR`, `Rus_Government`, and `paularsweet`. Their records have different IDs, timestamps, and scores; resolve or exclude these ambiguous records before joining.
- `user_id` has only **298,838 distinct exported values**. Many large IDs appear to have lost precision, causing different handles to share an ID. Converting rounded scientific notation to integers cannot restore the original identifiers.
- Bot scores are model outputs, not verified bot/human labels. The analysis notebooks use **0.7** as a bot-like cutoff; this is an analysis choice rather than a supplied ground-truth label.

## Historical source matching

The original matching audit matched tweet **`author.username`** to bot-score **`screen_name`**, trimming whitespace, removing an optional leading @, and lowercasing both. The existing matching audit finds score-file matches for **934,465 tweets (98.8%)** before resolving duplicate handles. Require a many-to-one join after resolving those duplicates to avoid multiplying tweet rows.

Handles can change or be reused, and the two files cover different time periods, so handle matches are not definitive identity verification. Use posting-account fields for this link; reply recipients and referenced authors describe other accounts. Repeated tweets from the same account also mean tweet-level observations are not independent account-level observations.

These source summaries use the CSV headers, observed values and historical audits. The bot-score summary notebook is preserved at `tasks/bot_scores_dataset_summary.ipynb` inside the local archive. Two other notebook paths named by the earlier documentation were already absent before cleanup; no missing files were recreated. Field descriptions follow the exported names; no authoritative collection protocol or Vectionary scoring specification is supplied in the repository.

## Final datasets and recommended joins

Use [bot_scores_recovered.csv](../data/bot_scores_recovered.csv) for exact account IDs and recorded handles, and [account_status.csv](../data/account_status.csv) for observed status. Both contain 386,327 unique account IDs. Join on **`user_id` as an exact string**; join tweet `author_id` to that same ID. Do not join current account statuses by handle. The earlier handle-matching process was used to recover rounded source IDs and was checked against the original exported rounding precision.

| Final file | Columns | Meaning |
| --- | --- | --- |
| `data/bot_scores_recovered.csv` | `user_id`, `screen_name`, `botometerlite_score` | Audited exact IDs, original recorded handles and historical scores; no score timestamp in this derived file. |
| `data/account_status.csv` | `user_id`, `account_status`, `botometerlite_score` | ID-attributed status observed on 11 November 2026 in Singapore; scores preserved. |
| `results/supplementary_validation/sampled_accounts.csv` | Account identifiers, score and sampling fields, behavior/network/profile/status measures, source references, and mosaic positions | One row per sampled account: 4,000 bot-like and 4,000 comparison accounts. Full column definitions are in the companion workbook's `Data dictionary` sheet. |

For the sample, use `sampling_weight` to summarize the comparison population. The primary behavior shares use `content_tweets_known`, reconstructing native retweets from embedded original posts and excluding synthetic `RT @author` mentions. Shares are fractions. Missing recent-activity, impersonation or spam judgments were not imputed.

See [methods and provenance](provenance.md) for status definitions, identity limitations, dates and checksums. The original source files remain local under gitignored `data/raw/`; derived datasets and final results remain eligible for version control.
