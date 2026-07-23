Using UI design from html/sample.html but not data from it.
Run the following investment analysis skills.

Inputs
- Holdings: /Users/dev/Downloads/holdings.csv
- Positions: /Users/dev/Downloads/positions.csv

Universe (analyze even if not currently held)
KPIL,M&M,ATUL,BLS,GESHIP,JKTYRE,JSL,APTUS,JSWDULUX,CHENNPETRO,JSWSTEEL,HEROMOTOCO,BPCL,HINDPETRO,ECLERX,PARADEEP,LUPIN,ITC,IDFCFIRSTB,MANAPPURAM,KTKBANK,SOUTHBANK,NATCOPHARM,TMPV,TMCV,DRREDDY,INFY,ZYDUSLIFE,ARE&M,EXIDEIND,TATACHEM,STOVEKRAFT,ICICIBANK,CIPLA,M&M,BAJAJ-AUTO,BIOCON,KALYANKJIL,TECHM,PETRONET,TMB,IRFC,INDUSINDBK,CUPID,ICICIGI,FEDERALBNK,KARURVYSYA,TATASTEEL,JYOTHYLAB,INDHOTEL,ZENSARTECH,WIPRO,CEATLTD,EMMVEE

Tasks

Run all of the following skills for above:

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
2. Add a "Buy / Sell Suggestions" tab for existing holdings and positions, including:
   - Recommended action (Buy / Hold / Sell)
   - Suggested quantity to buy or sell
3. Add a "New Buy Opportunities" tab for stocks that are not currently present in holdings or positions, including:
   - Recommended action
   - Suggested quantity to buy
4. Include a "Forecast" tab with future outlook and projections.
5. End the report with a "Prioritized Action Plan", listing recommendations in order of importance.
6. Use a "sidebar-based UI", with all report tabs accessible from the left sidebar.
7. When a stock is clicked from any tab, open a popup/modal that consolidates all analysis for that stock across every tab in a single view.
8. for non-held universe stocks check balance sheet.
9. Fetch updated news from web.