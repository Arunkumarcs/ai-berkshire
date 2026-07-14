Run the following investment analysis skills.

Inputs
- Holdings: /Users/dev/Downloads/holdings.csv
- Positions: /Users/dev/Downloads/positions.csv

Universe (analyze even if not currently held)
KPIL,M&M,ATUL,BLS,GESHIP,JKTYRE,JSL,APTUS,JSWDULUX,CHENNPETRO,JSWSTEEL,HEROMOTOCO,BPCL,HINDPETRO,ECLERX,PARADEEP,LUPIN,ITC,IDFCFIRSTB,MANAPPURAM,KTKBANK,SOUTHBANK,NATCOPHARM,TMPV,TMCV,DRREDDY,INFY,ZYDUSLIFE,ARE&M,EXIDEIND,TATACHEM,STOVEKRAFT,ICICIBANK,CIPLA,M&M,BAJAJ-AUTO,BIOCON,KALYANKJIL,TECHM,PETRONET,TMB,IRFC,INDUSINDBK,CUPID,ICICIGI,FEDERALBNK,KARURVYSYA,TATASTEEL,JYOTHYLAB,INDHOTEL,ZENSARTECH

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

1. Create one tab for each skill/report.
2. Add a "Buy / Sell Suggestions" tab for existing holdings and positions containing:
   - Symbol
   - Current Qty
   - Suggested Action (Buy / Hold / Reduce / Exit)
   - Suggested Qty
   - Target Allocation
   - Confidence Score
   - Reasoning
3. Add a "New Buy Opportunities" tab for stocks that are NOT currently present in holdings or positions containing:
   - Symbol
   - Suggested Buy Qty
   - Suggested Allocation %
   - Entry Zone
   - Stop Loss
   - Target
   - Conviction Score
   - Investment Thesis
4. Use sortable tables and charts wherever appropriate.
5. Include timestamps indicating when the data and news were fetched.
6. Highlight any conflicting signals between:
   - valuation
   - momentum
   - quality
   - news
   - thesis
7. Produce an overall portfolio score (0–100).
8. End with a prioritized action list:
    - Buy immediately
    - Accumulate on dips
    - Hold
    - Trim
    - Exit
    with clear reasoning for each recommendation.

If any ticker is invalid or delisted, report it separately instead of failing the run.
