# The "By the numbers" stats strip

- **Stats are optional. If present, use exactly 3 tiles.** Omit the `stats` field entirely on an article with no numbers worth surfacing; when you include it, ship exactly 3. The renderer slices to 3 (`article.stats.slice(0, 3)`), so a 4th is silently dropped and fewer than 3 looks unbalanced.
- Every stat must map to a number that actually appears in the body. The strip is a scannable index of the article's claims, not new claims.
- **Pick numbers the reader needs for their decision** (what it costs to run, how long to set up, how long to recover), not facts about the alternative the article rejects. Real edit: an "8-participant cap on official-API groups" tile (a fact about the path the article says not to take) got replaced by total monthly running cost.
- `value` is a string, so ranges/units render verbatim: `"$3k–$5k"`, `"2–6 weeks"`, `"~1 / month"`, `"< 1 year"`. Use an en dash `–` in ranges, never a hyphen-minus and never an em dash.
- **Tight labels.** One line. Cut filler. "Per month to run the workflows" not "Per month to run each of the workflows." Put one concrete example in at least one label ("…like drafting routine emails").
- `icon` is a short key mapped in `ARTICLE_STAT_ICONS`. Valid keys only:
  `clock`, `calendar`, `rocket`, `target`, `speed`, `wrench`, `repeat`, `coins`, `money`, `chart`, `team`, `workflow`.
- Optional `sourceUrl` on a stat links the figure to a source pill.
