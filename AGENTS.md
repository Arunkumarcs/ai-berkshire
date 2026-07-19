# AI Berkshire Codex Guide

This repository contains investment research workflows, reports, and shared
validation tools. Keep compatibility with both Claude Code and Codex users.

## Project Overview

Value investing research skill collection based on the Four Masters framework:
Buffett, Munger, Duan Yongping, Li Lu.
GitHub: xbtlin/ai-berkshire

## Project Layout

- `skills/*.md`: Claude Code slash-command source files.
- `codex-skills/*/SKILL.md`: Codex skill packages. Most are generated from
  `skills/*.md`; Codex-only hand-written packages are allowed when clearly
  marked and no same-named `skills/*.md` source exists.
- `codex-prompts/*.md`: generated Codex custom prompts for slash-command
  style entry points. These are a compatibility layer; skills remain preferred.
- `tools/*.py`: shared financial validation and data tools used by both systems.
- `reports/`: research outputs. Do not rewrite unrelated reports while changing
  tooling or skills.
- `html/`: standalone HTML reports (portfolio dashboards, visualizations, etc.). All HTML reports must include a dark/light mode toggle (JS button or `prefers-color-scheme` media query).
- `assets/`: static resources like images.
- `scripts/sync-codex-skills.py`: regenerates Codex skills from `skills/*.md`.
- `scripts/install-codex-skills.sh` / `scripts/install-codex-skills.bat`:
  installs Codex skills locally.
- `scripts/install-codex-prompts.sh` / `scripts/install-codex-prompts.bat`:
  installs generated Codex slash prompts locally.
- `scripts/install-claude-commands.sh` / `scripts/install-claude-commands.bat`:
  installs Claude Code commands locally.

## Report Directory Structure

All reports are organized by **company name** folder, with all company-related
reports inside:

```
reports/
├── AI-Industry-Research/       — AI industry chain panorama (pinned)
│   ├── AI-5-layer-cake-industry-panorama-20260605.md
│   └── AI-5-layer-cake-wechat-20260605.md
├── Tencent/                    — All Tencent research reports
│   ├── Tencent-research-20260408.md
│   ├── Tencent-earnings-2025Q4.md
│   ├── Tencent-management-20260409.md
│   └── Tencent-thesis.md
├── PDD/                        — All PDD research reports
├── Pop Mart/                   — All Pop Mart research reports
├── nuclear-industry-20260409.md  — Industry reports at root
├── AI-compute-funnel-20260509.md — Funnel screening at root
└── portfolio-latest.md           — Portfolio report at root
```

## Report Naming Convention

| Skill | File Naming Format | Example |
|-------|-------------------|---------|
| /investment-team | `{company}/` directory with 4 perspectives + final report | `reports/PDD/final-report.md` |
| /investment-research | `{company}-research-{YYYYMMDD}.md` | `reports/Tencent/Tencent-research-20260408.md` |
| /investment-checklist | `{company}-checklist-{YYYYMMDD}.md` | `reports/Tencent/Tencent-checklist-20260408.md` |
| /industry-research | `{industry}-industry-{YYYYMMDD}.md` (root) | `reports/nuclear-industry-20260409.md` |
| /industry-funnel | `{industry}-funnel-{YYYYMMDD}.md` (root) | `reports/AI-compute-funnel-20260509.md` |
| /private-company-research | `{company}-private-{YYYYMMDD}.md` | `reports/ByteDance/ByteDance-private-20260408.md` |
| /earnings-review | `{company}-earnings-{period}.md` | `reports/Tencent/Tencent-earnings-2025Q4.md` |
| /earnings-team | `{company}/` directory with 4 master perspectives + research working files + wechat article + reader review | `reports/Tencent/Tencent-earnings-2025Q4.md` (final wechat draft) |
| /thesis-tracker | `{company}-thesis.md` (long-term maintenance) | `reports/Tencent/Tencent-thesis.md` |
| /portfolio-review | `portfolio-latest.md` (root, continuously updated) | `reports/portfolio-latest.md` |
| /management-deep-dive | `{company}-management-{YYYYMMDD}.md` | `reports/Tencent/Tencent-management-20260409.md` |

## /investment-team File Structure

```
reports/{company}/
├── README.md                         — Research framework overview + key conclusions
├── 01-business-model-DYP-perspective.md
├── 02-financial-valuation-Buffett-perspective.md
├── 03-industry-competition-Munger-perspective.md
├── 04-risk-management-Li-Lu-perspective.md
└── final-report.md                   — Team Lead consolidated report
```

## Compatibility Rules

- Treat `skills/*.md` as the canonical workflow source.
- After changing any file in `skills/`, run:
  `python3 scripts/sync-codex-skills.py`
- If slash prompt compatibility is needed, also run:
  `python3 scripts/sync-codex-prompts.py`
- Do not manually edit generated `codex-skills/*/SKILL.md` unless also updating
  the corresponding source in `skills/`.
- For Codex-only hand-written packages under `codex-skills/`, keep them clearly
  marked as Codex-only and do not create a same-named `skills/*.md` file unless
  intentionally adopting the workflow for Claude Code too.
- Keep tool paths compatible with the documented checkout path:
  `~/ai-berkshire/tools/...`
- Keep `CLAUDE.md` for Claude Code behavior and this `AGENTS.md` for Codex
  behavior.

## Research Analysis Core Principles (Highest Priority)

- **Objective, objective, objective** — all research must be based on facts and data. No subjective conjecture.
- Strictly distinguish "facts" from "opinions": facts must be supported by data. Opinions must be explicitly labeled as "opinion" or "speculation."
- **No pre-set bias**: do not preset a bullish or bearish stance. Present data first, then logic, then conclusion. Conclusions must follow naturally from the data.
- Do not use "I think," "I feel," "obviously" and other subjective expressions. Use "data shows," "evidence indicates," "according to [source]."
- **Present both sides**: every core judgment must include counterarguments ("on the other hand...") so readers can weigh for themselves.
- When uncertain, honestly say "uncertain" or "insufficient data." Do not use speculation to fill gaps.
- All skills (investment-team, investment-research, earnings-review, etc.) must follow these principles.

## Report Language & Style

- **All reports use English**
- Style: direct, sharp, no filler
- Data must cite sources. Key data needs at least 2 cross-verified sources.
- Estimates must be labeled "estimate."
- Use clear ratings or scores where appropriate.
- Interleave quotes from Buffett/Munger/Duan Yongping/Li Lu where relevant.

## Research Quality Rules

- Before starting any research, run the `date` command to confirm today's
  date. Treat that date as the baseline for "latest" data (prices, market cap,
  most recent filings), and state the data cutoff date in the report header.
  Never assume the current date from training data.
- Financial data must come from at least two independent sources when the skill
  requires verification.
- Use exact arithmetic tools for market cap, valuation, cross-source checks, and
  scenario analysis:
  `python3 tools/financial_rigor.py ...`
- Use report audit tooling before treating generated research as publishable:
  `python3 tools/report_audit.py ...`
- Clearly label low-confidence conclusions, incomplete data, and source gaps.
- This project is for learning and research, not investment advice.

## GitHub Operations

- Local checkout path: `~/ai-berkshire/`
- Remote: `https://github.com/xbtlin/ai-berkshire.git`
- Before pushing, always `git pull --rebase origin main` (remote often has new commits)
- Commit messages in English, clearly describing what changed
- Do not push intermediate files (e.g., data_collection.md), only final reports

## Dashboard UI Template

The canonical dashboard format is `html/sample.html`: sidebar navigation, tab-based content sections for each analysis skill, stock click-to-modal showing consolidated cross-skill data. Use this as the template for all future dashboard work.

## Common Commands

```bash
# Push report to GitHub
cd ~/ai-berkshire
git add reports/xxx.md
git commit -m "Add research report for X"
git pull --rebase origin main
git push origin main
```

## Notes

- Market cap must be manually verified: share price x total shares, cross-check with reported market cap.
- Be explicit about currency units (HKD/USD/RMB) to avoid confusion.
- Use `tools/financial_rigor.py` for precise PE/ROE calculations.
- After writing a report, proactively ask if the user wants to push to GitHub.

## Editing Rules

- Preserve existing report files unless the task specifically asks to change
  them.
- Keep changes scoped to the requested skill, tool, script, or documentation.
- Before finishing a skill/tool change, run the relevant syntax or generation
  check. For compatibility changes, run:
  `python3 scripts/sync-codex-skills.py`
- To verify generated Codex artifacts are current without rewriting files, run:
  `python3 scripts/sync-codex-skills.py --check`
  and, when slash prompts are relevant:
  `python3 scripts/sync-codex-prompts.py --check`
