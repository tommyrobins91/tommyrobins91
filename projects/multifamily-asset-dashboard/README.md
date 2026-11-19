# Multifamily asset management dashboard

## The problem

Asset managers get rent roll, collections and work order data as separate spreadsheet tabs. Answering simple questions (which property is dragging occupancy, how much rent is below market, when the lease cliff hits) means rebuilding pivots every month.

## What I built

An interactive dashboard on a 5-property, 240-unit sample portfolio:

- Property switcher that filters every view
- KPI strip: physical and economic occupancy, in-place vs. market rent, loss-to-lease, vacancy loss, upcoming expirations
- Property comparison table
- Charts for occupancy by property, rent by unit type, and an 18-month lease expiration schedule
- Unit mix table and a sortable, filterable full rent roll
- Light and dark mode, readable on a phone

## What it found

- Physical occupancy of 92.9% against economic occupancy of 89.8%, so concessions and below-market leases cost about 3 points
- Harbor Point is the weak asset at 86.5% occupancy
- Net loss-to-lease of 2.7%
- 152 leases (68% of occupied units) expire within 12 months, peaking in May 2027. That's the renewal risk to plan for.

## Built with

Python (pandas, openpyxl) to clean the workbook, data embedded as JSON in a single HTML file, plain JavaScript and SVG for the charts, and Playwright screenshots at desktop and mobile widths for QA.
