Using UI design from html/sample.html but not data from it.
Run the following investment analysis skills.

Inputs

- Holdings: /Users/dev/Downloads/holdings.csv
- Positions: /Users/dev/Downloads/positions.csv

Universe (analyze even if not currently held)
BLS,CHENNPETRO,JSWDULUX,ENGINERSIN,JSWSTEEL,LUPIN,NATIONALUM,ITC,INFY,
JKTYRE,GESHIP,APTUS,
M&M

Tasks

top priority run all of the following skills for above:

- /portfolio-review
- /thesis-tracker
- /thesis-drift
- /news-pulse
- /quality-screen
- /bottleneck-hunter
- /investment-checklist
- /investment-research

Output

Generate a consolidated dashboard at:

html/dashboard.html

Requirements

note: In all table add sorting in heading but heading should not sort.

1. Create a separate tab for each analysis skill/report, clearly showing the skill used.
   - Run deep analysis: web search + financial tools for holdings
   - Run deep analysis for non-held stocks in universe
2. Add Valuation Tab
3. Add Risk Tab
4. Add Bonds Tab
5. Add a "Buy / Sell Suggestions" tab for existing holdings and positions, including:
   - Recommended action (Buy / Hold / Sell)
   - Suggested quantity to buy or sell
6. Add a "New Buy Opportunities" tab for stocks that are not currently present in holdings or positions, including:
   - Recommended action
   - Suggested quantity to buy
7. Include a "Forecast" tab with future outlook and projections.
8. End the report with a "Prioritized Action Plan", listing recommendations in order of importance.
9. Use a "sidebar-based UI", with all report tabs accessible from the left sidebar.
10. When a stock is clicked from any tab, open a popup/modal that consolidates all analysis for that stock across every tab in a single view.
11. for non-held universe stocks check balance sheet.
12. Fetch updated news from web.
13. Sector Leaders — Top 2 per Sector
