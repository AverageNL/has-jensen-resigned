# Has Jensen Huang resigned?

A one-page site built by Jekyll on GitHub Pages. You never edit HTML to update it:
everything that changes lives in the `_data` folder.

## Files

| File | What it controls |
| --- | --- |
| `_data/timeline.yml` | The timeline entries |
| `_data/watch.yml` | The "What to watch" tiles |
| `_data/background.yml` | The collapsed "How it got here" list |
| `_data/sources.yml` | The source list and its numbering |
| `_data/status.yml` | The hand-set verdict (the live check does the rest) |
| `index.html` | Layout, styling, the three summary cards and the script |
| `_includes/refs.html` | Turns source ids into the small numbered links |

## Add a timeline entry

Open `_data/timeline.yml` on GitHub, click the pencil, and paste a block at the top:

```yaml
- date: 2026-11-12
  headline: "Huang agrees to brief Congress"
  points:
    - tag: record
      text: "He accepts the 18 November closed-door session."
      sources: [house-request]
```

- `tag` is `record` (on the record), `reported` (unnamed sources, not proven) or `denied`.
- `sources` are ids from `_data/sources.yml`. For a new source, add it at the bottom of
  that file first, so the existing numbers stay the same.
- Keep text inside double quotes, and keep the indentation exactly as shown (spaces, not tabs).
- For a date range, add a line such as `label: "5–6 November 2026"` under `date`.

Commit, and the site rebuilds in about a minute.

## If he resigns

The page checks Wikidata on every visit and flips to "Yes." by itself once Wikidata
records an end date. To flip it by hand straight away, set `resigned: true` in
`_data/status.yml` and edit `resigned_summary`.

## If a change does not show up

A typo in a `.yml` file stops the build, and the site keeps showing the last good
version. The repository's **Actions** tab shows the failed build and the line it tripped on.
