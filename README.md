# Instagram Reels Practice Project

A small exploratory analysis of Instagram Reels performance data, done to find
patterns that could inform strategy for a new, zero-follower AI-content account.

## Data

- **`instagram_reels_clean.csv`** — 828 Instagram Reels with post metadata
  (creator, caption, timestamp, duration) and performance metrics (views,
  likes, comments, hashtag count, engagement rate, and a derived virality
  score/tier).
- **`data_dictionary.csv`** — column-by-column description of the dataset.
  Note: it documents a `video_play_count` column that isn't actually present
  in the CSV (15 columns exist, the dictionary describes 16) — a minor
  mismatch to be aware of if you extend this dataset.

The dataset covers only **9 creators**, and nearly all of them are
established, verified accounts with large existing followings (e.g.
techburner, BeerBiceps, Kabita's Kitchen). That matters a lot for how the
findings below should be read — see [Limitations](#limitations).

## What we did

1. Moved the raw CSVs into this project folder and reviewed the data
   dictionary to understand each column.
2. Built two charts (saved as PNGs in this repo):
   - **`avg_virality_by_niche.png`** — average virality score per content
     niche, sorted highest to lowest.
   - **`avg_views_by_hashtag_count.png`** — average views per hashtag count,
     sorted highest to lowest.
3. Ran deeper analysis to sanity-check what actually drives performance:
   correlations between views/engagement and hashtag count, video duration,
   caption length, and posting time/day — and checked whether any of those
   patterns were really just a stand-in for "which creator posted it."

## Findings

1. **Virality by niche.**

   | Niche | Avg. virality score |
   |---|---|
   | Fitness & Lifestyle | 89.0 |
   | Technology & Gadgets | 78.3 |
   | Entertainment | 69.9 |
   | Food & Cooking | 66.5 |
   | Personal Finance | 63.8 |

2. **Hashtag count barely matters.** Correlation between hashtag count and
   views was ~0 (r = 0.01), and even within a single creator's own posts
   (techburner), using 1 vs. 4 vs. 5 hashtags showed no consistent difference
   in engagement rate. Using 5 hashtags (a common default) is not a
   meaningful lever — don't over-invest effort here.

3. **Shorter videos had better engagement.** Reels in the 30–60 second range
   averaged ~6.8% engagement rate vs. ~5.9–6.3% for reels over 90 seconds.
   Shorter, tighter content is easier to finish and rewatch, which Reels'
   algorithm rewards.

4. **Mid-length captions outperformed both extremes.** Captions of 16–60
   words averaged ~9% engagement vs. ~6.6–7.5% for bare captions or long,
   essay-style ones. A caption with a real hook or bit of context does
   better than either hashtag-only captions or walls of text.

5. **Posting time had a real spread in this sample.** Friday, Wednesday, and
   Sunday, and the ~14:00–15:00 UTC window, averaged the highest views. This
   reflects *these specific creators'* audiences, so treat it as a hypothesis
   to test against your own account's data, not a rule.

## Key takeaways (for a new, zero-follower account)

At zero followers, growth is driven almost entirely by Instagram's
discovery/Explore/Reels algorithm — not by follower count or hashtags. The
levers that matter most, informed by both the data above and how Reels
distribution generally works:

1. **Nail the hook in the first 1–2 seconds.** If viewers don't stop
   scrolling immediately, the algorithm stops distributing the video.
2. **Keep it short and loopable.** The duration finding above supports
   this directly — favor 30–60 second reels over long-form.
3. **Post consistently**, ideally daily or near-daily in one niche, so
   Instagram can learn who to show your content to.
4. **Use trending audio.** It's one of the strongest discovery signals
   available to small accounts.
5. **Write a real caption with a CTA that invites comments** (e.g. "comment
   X if..."). Comments are weighted heavily by the algorithm, and even a
   handful of comments is a meaningful signal at this stage.
6. **Don't over-optimize hashtags.** 3–5 relevant tags is enough; the data
   shows no payoff from tuning this further.

## Limitations

- Small sample: 828 rows across only 9 creators, most already established
  and verified. Their raw view/engagement numbers reflect existing
  audience size and algorithmic trust, not tactics a new account can copy
  directly.
- Several patterns (e.g. hashtag count) are confounded with creator
  identity — each creator tends to use a consistent hashtag style, so
  apparent "hashtag effects" can really be creator effects. Where
  possible, findings above were checked within a single creator to reduce
  this bias, but sample sizes per creator are small.
- Posting-time and day-of-week patterns are specific to this sample's
  audiences and time zones, not a universal rule.

## Files

- `instagram_reels_clean.csv` — raw dataset
- `data_dictionary.csv` — column definitions
- `avg_virality_by_niche.png` — chart: average virality score by niche
- `avg_views_by_hashtag_count.png` — chart: average views by hashtag count
