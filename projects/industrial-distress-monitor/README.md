# Industrial distress signal monitor

## The problem

At Anchor Capital Group I source off-market industrial deals from small private owners in Plant City, Lakeland, Orlando and Tampa. Finding properties is easy. Finding owners who are ready to sell is the bottleneck, and a flat call list treats every owner the same.

## What I built

A monitor that scores private industrial owners on likelihood to sell, using public records:

- Tax delinquencies and tax certificate sales
- Liens and lis pendens filings
- Code violations
- Hold period (long-held assets with low basis)
- Loan maturities

Owners are ranked by score so outreach starts at the top of the list, and each score shows which signals drove it.

## Design choices

- Signals are layered. Industrial owners rarely let taxes lapse, so tax delinquency alone is a thin signal for this asset class. Combining several weak signals gives a usable ranking.
- The scoring is transparent. A broker or acquisitions lead can see why an owner ranks where they do and argue with the weights.
- Every county publishes records differently, so most of the engineering is in per-county parsers, not the scoring.

## Note on data

Screenshots and sample output in this repo use anonymized records. Real owner names and target lists are not published.
