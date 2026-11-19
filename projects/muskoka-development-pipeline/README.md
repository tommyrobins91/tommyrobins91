# Muskoka Development Pipeline

Code: [tommyrobins91/Muskoka-Dev-Pipeline](https://github.com/tommyrobins91/Muskoka-Dev-Pipeline)

## The problem

One of the largest landowners in Muskoka told me the hardest part of tracking development in the region is that the information is scattered. Planning notices, building permits, zoning and assessment data sit across six area municipalities and the District of Muskoka, each with its own format. Paid pipeline trackers like Altus cover Toronto and Vancouver, not cottage country. I checked for an existing product before building and didn't find one.

## What I built

A single-page tool that pulls everything onto one map:

- Planning applications (severances, rezonings, minor variances, plans of subdivision and condominium) from the five towns that publish notices. Georgian Bay does not publish them.
- Building permits, with teardown and rebuild flags
- Lot size, zoning and assessed value for each property
- Property-level planning and permit history back to 1999
- A 500-metre "nearby activity" view around any address
- Property search and a "filed in the last 30 days" panel
- One-click Excel export

## How it works

The data comes from the District's ArcGIS REST services. Those endpoints only answer requests that come from the District's own map pages, so the refresh job runs inside a browser session on those pages, pulls the layers, and rebuilds the dataset. A scheduled task reruns it and flags new filings.

## What it shows

Twenty-five years of history makes the trend data useful on its own. Minor variances in Muskoka Lakes have held between about 45 and 95 a year, so a jump outside that band is worth noticing. The open subdivision and condo files give a rough count of the supply that's actually in the approvals process.

## Next

The same engine can be pointed at other fragmented Ontario markets (Simcoe, Kawartha Lakes) under one codebase.
