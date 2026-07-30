---
name: stock-fundamental-analysis
description: "AI Berkshire skill: Simplified Stock Fundamental Analysis Skill. Source: skills/stock-fundamental-analysis.md."
---

## Codex adapter note

This skill is generated from `skills/stock-fundamental-analysis.md` so Claude Code and Codex users share one canonical workflow.

- Treat `$ARGUMENTS` as the user's request in the current Codex thread.
- When the source mentions Claude-only surfaces such as Task, Agent, WebSearch, Bash, Read, or Write, use the closest Codex capability available in this session: subagents when available, web search when needed, shell commands for local tools, and normal file edits for workspace files.
- Use shared project tools from `tools/` in this repository. Prefer running commands from the repository root with paths like `python3 tools/financial_rigor.py ...`; if the current thread starts outside the repo, locate the actual checkout path first instead of assuming a fixed home-directory path.
- Before starting research, run the `date` command to confirm today's date; treat it as the baseline for "latest" data and state the data cutoff date in the report header. Never assume the current date from training data.
- Preserve the research quality rules from `AGENTS.md`: cross-check financial data, use exact arithmetic tools for valuation/math, and clearly label uncertainty and source gaps.

# Simplified Stock Fundamental Analysis Skill

## Role

Act as a professional equity research analyst. Analyse only the metrics
that materially affect the company's industry. Clearly distinguish
facts, estimates, and assumptions, and provide an objective investment
recommendation.

## Materiality Rule

Analyse only the metrics that matter for the company's industry.

-   **Banks:** NIM, CASA, GNPA, NNPA, Capital Adequacy
-   **IT/SaaS:** ARR, NRR, Rule of 40, Margins
-   **Manufacturing:** ROCE, Capacity Utilisation, Working Capital
-   **FMCG:** Brand Strength, Distribution, Pricing Power
-   **Pharma:** Pipeline, R&D, Regulatory Approvals

Skip irrelevant sections instead of completing every checklist.

## 1. Executive Summary

-   Company
-   Sector
-   Market Cap
-   Current Price
-   Fair Value
-   Recommendation
-   Conviction (1--5 ⭐)
-   Risk Level

## 2. Business Quality (15%)

-   Business model
-   Revenue sources
-   Competitive moat
-   Industry position
-   Key competitors
-   **Score:** /15

## 3. Financial Strength (20%)

-   Revenue CAGR (3Y & 5Y)
-   EPS CAGR
-   ROE
-   ROCE
-   ROIC
-   Debt/Equity
-   Interest Coverage
-   Current Ratio
-   **Score:** /20

## 4. Cash Flow & Earnings Quality (15%)

-   Operating Cash Flow
-   Free Cash Flow
-   OCF/PAT
-   FCF Trend
-   One-time items
-   Earnings quality
-   **Score:** /15

## 5. Valuation (15%)

-   PE
-   PEG
-   EV/EBITDA
-   Price/Book
-   Optional DCF
-   Margin of Safety
-   Verdict: Cheap / Fair / Expensive
-   **Score:** /15

## 6. Growth Drivers (10%)

-   Capacity expansion
-   New products
-   Market expansion
-   Government support
-   Technology advantage
-   **Score:** /10

## 7. Management & Governance (10%)

-   Promoter quality
-   Capital allocation
-   Corporate governance
-   Auditor observations
-   Shareholding trend
-   **Score:** /10

## 8. Risk Analysis (10%)

-   Top five risks
-   Risk Level: Low / Medium / High
-   **Score:** /10

## 9. Red Flags

-   Auditor resignation
-   Promoter pledge
-   Negative FCF
-   Equity dilution
-   Related-party transactions
-   Falling margins
-   High receivables
-   Overall: None / Minor / Major

## 10. Peer Comparison

  Metric           Company   Peer Average
  ---------------- --------- --------------
  ROE                        
  ROCE                       
  Revenue Growth             
  PE                         
  Market Share               

## 11. Investment Thesis

### Reasons to Buy

-   Top 5 points

### Reasons to Avoid

-   Top 5 points

### Key Catalysts

-   Next 12 months

## 12. Final Recommendation

### Overall Score (/100)

  Category       Weight
  ------------ --------
  Business           15
  Financials         20
  Cash Flow          15
  Valuation          15
  Growth             10
  Management         10
  Risk               10
  Red Flags           5

### Recommendation

-   Strong Buy
-   Buy
-   Accumulate
-   Hold
-   Reduce
-   Sell

## Advanced (Optional)

-   Piotroski F-Score
-   Altman Z-Score
-   Beneish M-Score
-   DuPont Analysis
-   DCF Sensitivity Analysis
-   Segment Analysis
-   Geographic Analysis
-   ESG Review
-   Industry-specific modules
