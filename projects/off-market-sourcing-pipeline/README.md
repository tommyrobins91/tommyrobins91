# Off-market sourcing pipeline

## The problem

A Reonomy export for one Florida submarket can run past 1,300 properties. Most of them are owned by institutions, professional investors, or are too small to be worth a call. Sorting them by hand took days per market.

## What I built

A repeatable Python pipeline that turns a raw export into an Airtable-ready call list of mom-and-pop owners of multi-tenant industrial buildings.

1. Reads all four tabs of the export (properties, contacts, occupants, occupant contacts) and joins them on the property ID. The tabs use different key names, and a bad join fails silently, so the join is checked.
2. Filters out institutional owners by entity name and professional owners by contact title.
3. Drops owners with more than three listed contacts, which usually signals a professional operation.
4. Measures multi-tenancy with occupant count instead of the unit field, which badly undercounted tenants.
5. Treats $0 sale prices as ownership restructurings, not real trades, so they don't reset the hold period.
6. Sorts survivors by size: a pass list, a review list over 17,000 SF, a separate 12,000 to 17,000 SF band, and drops anything under 12,000 SF.
7. Outputs an import file mapped to the Airtable CRM schema, with views for uncalled owners, owners that still need contact verification, and callbacks due.

## Results

Run on Plant City, Lakeland, Orlando, Tampa and Jacksonville exports. It cut a 1,359-property Tampa export down to a short list that one person can work in a week, and it showed that Lakeland retail had too little viable inventory to pursue, so the focus stayed on industrial.

## Note on data

No exported data, owner names or contact details are included here. Phone numbers are scrubbed against Do Not Call lists before any outreach.
