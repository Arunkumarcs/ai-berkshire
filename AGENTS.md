# AI Berkshire Agent Guide

Investment research workflows, reports, and shared validation tools built on
the Four Masters framework (Buffett, Munger, Duan Yongping, Li Lu).
Canonical upstream: https://github.com/xbtlin/ai-berkshire (this checkout may
be a fork; current branch is `dev`).

## Project Layout

- `skills/*.md`: canonical workflow sources (Claude Code slash commands).
- `codex-skills/*/SKILL.md`: generated from `skills/*.md`. Codex-only
  hand-written packages are allowed when clearly marked and no same-named
  `skills/*.md` source exists (e.g. `investment-memo-craft`).
- `codex-prompts/*.md`: generated slash-prompt compatibility layer; skills remain preferred.
- `tools/*.py`: stdlib-only financial validation tools (see below).
- `scripts/`: sync scripts (`sync-codex-skills.py`, `sync-codex-prompts.py`),
  dashboard build (`build_dashboard.py`), install scripts (`.sh`/`.bat`).
- `reports/`: research outputs, organized by company folder.
- `html/`: `sample.html` (canonical dashboard template), `dashboard.html`
  (generated), `serve.py` (local server). All HTML must include a dark/light
  mode toggle (JS button or `prefers-color-scheme`).
- `tests/`: self-executing unittest regression tests.
- `CLAUDE.md`: Chinese instructions for Claude Code behavior (overlaps this
  file; treat this `AGENTS.md` as authoritative for OpenCode/Codex).

## Reports: Language, Structure, Naming

- Reports are written in **Chinese** (English is acceptable for global
  companies — e.g. `GESHIP-research-20260713.md`, `nasdaq-100-investment-research.md`).
- Reports live in company folders with **Chinese names**: `reports/腾讯/`,
  `reports/拼多多/`, `reports/泡泡玛特/`, `reports/AI产业研究/`.
- Naming: `{公司名}-research-{YYYYMMDD}.md`, `-earnings-{period}.md`,
  `-checklist-{YYYYMMDD}.md`, `-management-{YYYYMMDD}.md`, `-thesis.md`
  (long-term, maintained), `{公司名}-investment-team-{YYYYMMDD}.md`.
  Industry/funnel reports at root: `{行业}-industry-{YYYYMMDD}.md`,
  `{行业}-funnel-{YYYYMMDD}.md`.
- `/investment-team` folder layout: `01-商业模式分析-段永平视角.md`,
  `02-财务估值分析-巴菲特视角.md`, `03-行业竞争分析-芒格视角.md`,
  `04-风险管理层评估-李录视角.md`, plus `最终报告.md` / dated finals.
- Do not rewrite unrelated reports while changing tooling or skills.
- `reports/portfolio-latest.md` is **gitignored (local only)**; `/local/`
  holds private data and API tokens — never commit it.

## Compatibility Rules

- `skills/*.md` is canonical. After changing any file there, run:
  `python3 scripts/sync-codex-skills.py`
- Verify generated artifacts are current without rewriting:
  `python3 scripts/sync-codex-skills.py --check` and
  `python3 scripts/sync-codex-prompts.py --check` (when prompts matter).
- Do not manually edit generated `codex-skills/*/SKILL.md` without updating
  the source in `skills/`.

## Research Analysis Core Principles (Highest Priority)

- Objective, fact- and data-based research only; strictly distinguish facts
  (data-supported) from opinions (must be labeled "opinion"/"speculation").
- No pre-set bullish/bearish stance: data first, logic second, conclusion
  last. Every core judgment includes counterarguments ("on the other hand...").
- Never use "I think"/"obviously"; use "data shows"/"according to [source]".
  When uncertain, say "uncertain" / "insufficient data".
- These rules bind every skill (investment-team, investment-research,
  earnings-review, etc.).

## Research Quality Rules

- Before research, run `date`; treat it as the data cutoff and state it in
  the report header. Never assume the current date from training data.
- Key data needs at least 2 independent cross-verified sources; estimates
  must be labeled "estimate". Currency units explicit (HKD/USD/RMB).
- Market cap must be manually verified: share price × total shares,
  cross-checked against reported market cap.
- This project is for learning and research, not investment advice.

## Tools, Tests, and Their Quirks

- `python3 tools/financial_rigor.py` — exact Decimal math (no float drift).
  Subcommands: `verify-market-cap`, `verify-valuation`, `cross-validate`,
  `calc`, `benford`.
- `python3 tools/report_audit.py` — 3-step audit: `extract --report X.md`
  (samples ~15% of data points) → fetch values from reliable sources →
  `verdict --results '[...]'` (pass/reject). `--dry-run` skips fetching.
- `python3 tools/terminal_value.py` — terminal value / DCF checks; wired into
  `skills/investment-research.md` as a hard validation constraint.
- `python3 tools/twstock_data.py` (FinMind) — Taiwan stock data; cross-verify
  per `skills/financial-data.md`. `tools/ashare_data.py` for A-shares.
- Tests: **pytest is NOT installed**. Run directly:
  `python3 tests/test_financial_rigor.py`, `python3 tests/test_report_audit.py`
  (unittest, zero deps).

## Dashboard Work

- `html/sample.html` is the canonical template (layout only — **don't reuse
  its data**). `html/dashboard.html` is generated, not hand-edited: rebuild
  via `python3 scripts/build_dashboard.py`, which reads
  `data/dashboard_data.json` plus a **machine-specific holdings CSV path
  hardcoded in the script** (`/Users/dev/Downloads/holdings.csv`).
- Every dashboard table must be sortable: include `makeSortable()` verbatim
  from sample.html AND call it at the end of `init()`. Verify with
  `node scripts/check-dashboard-sort.mjs`.
- Serve locally with `python3 html/serve.py [port]` (avoids file:// CORS).

## GitHub Operations

- Before pushing, always `git pull --rebase origin main` (remote often has
  new commits). Commit messages in **Chinese**, clearly describing the change
  (matches repo history).
- Do not push intermediate files (e.g. data_collection.md) or anything under
  `/local/` — only final reports. After writing a report, proactively ask if
  the user wants to push.

## Editing Rules

- Keep changes scoped to the requested skill/tool/script/docs. Preserve
  existing reports unless the task explicitly asks to change them.
- Before finishing a skill/tool change, run the relevant check:
  `python3 scripts/sync-codex-skills.py --check` (see Compatibility Rules);
  tests via `python3 tests/test_*.py`.