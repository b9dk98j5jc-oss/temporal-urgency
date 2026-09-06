# Retrieval notes

## X / Twitter — the weak link

X posts are not reliably retrievable through web search. Search engines index
individual posts inconsistently and with heavy lag; third-party mirrors are
largely defunct; and scraping the site is both brittle and against its terms.
A weekly scheduled run that relies on search alone will produce systematically
incomplete X coverage — and, worse, coverage biased toward posts that got
picked up by news outlets, which correlates with exactly the inflammatory
framing the paper is measuring.

Three defensible options:

1. **X API (paid tier).** Reliable user-timeline pulls and stable IDs. Best
   data, real recurring cost, requires a local script rather than a chat-side
   scheduled task.
2. **Periodic manual export.** The user requests their own archive or pulls
   timelines quarterly by hand; the skill ingests the dump and codes it. Zero
   cost, coarse cadence, fine for a corpus measured in months.
3. **Declare X out of frame for the primary analysis** and treat it as a
   secondary sample with stated limitations. Defensible, and avoids a
   sampling-bias problem that a referee would otherwise find.

Whichever is chosen, record it in `frame_changes.md` with a date. Do not let a
scheduled run quietly substitute news coverage of a post for the post itself —
that is a paraphrase, and belongs in `unverified.csv`.

## What the weekly run reliably gets

Transcripts, testimony, blog posts, and keynotes index well and carry stable
URLs. This substrate is also better evidence for the paper's construct: a
prepared statement to a legislature and an off-hand post are different speech
acts, and `venue_type` lets that difference be tested rather than assumed.

## Query construction

Per speaker, per venue type, one query. Useful patterns:

- `{speaker} interview transcript {month year}`
- `{speaker} testimony {year}`
- `{speaker} blog post {topic}`
- `{company} earnings call transcript {quarter}`

Avoid urgency vocabulary in the query itself. Searching for "Altman AGI
inevitable" retrieves the passages that confirm the hypothesis and misses the
speaker's neutral or decelerationist statements — which the `80` code exists
to capture. Search by speaker and venue; let the coding find the framing.
