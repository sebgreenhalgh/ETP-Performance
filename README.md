# Commodity ETP Performance Gap

A student quantitative-research project investigating how much of the performance gap between **UNG** (a futures-based natural-gas fund) and a **Henry Hub spot-price reference** is associated with the shape of the natural-gas futures curve. **GLD** versus a gold benchmark is the physically backed control.

**Important:** A spot-price reference is not an investable strategy. Futures-curve slope is not, by itself, realized roll yield or proof of causality.

## Start here

- [Project issue roadmap](https://github.com/sebgreenhalgh/ETP-Performance/issues/1) — tasks, dependencies and beginner starting points.
- [GitHub working agreement](CONTRIBUTING.md) — issues, branches, PRs and lead-only merges.
- [Using AI responsibly and effectively](docs/AI_GUIDE.md) — try first, author prompt, independent review prompt, understanding/testing checklist.
- [Project proposal and frozen research decisions](docs/decision_log.md) — to be created/confirmed during research.

## Project structure (being built)

```text
src/          Reusable loading, performance, plotting, and analysis code
notebooks/    One polished, top-to-bottom final_analysis.ipynb
data/         Download/reproduction instructions; do not commit restricted raw data
docs/         Definitions, data sources, methods, decisions and writing guidance
reports/      Research note and presentation
```

## Working convention

One focused issue → one branch → one pull request → lead (Seb) reviews → **only Seb merges**. Everyone must be able to reproduce and explain what they submit.

## Reproducing the project

Environment and download instructions will be completed as the data/source choices are approved in [issue #6](https://github.com/sebgreenhalgh/ETP-Performance/issues/6). Proposed Python version: **3.11+**. After the environment file is added, use:

```bash
python -m venv .venv
# macOS/Linux: source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

The final notebook will run from top to bottom with documented source data and no manual spreadsheet edits. This README will be updated to provide the exact run command and input availability.

## Required outputs

Growth of $1 comparisons; monthly/cumulative fund–reference gaps; curve-slope distribution; lagged slope vs next-month gap scatter; regression coefficient with 95% confidence interval; contango/backwardation average gaps; and a clear account of fees, collateral income, implementation and limitations. Deliverables also include a 3–5-page note, data dictionary, decision log, brief AI-usage note and presentation.

**Data note:** The project brief flags that EIA free futures data end in April 2024; confirm actual coverage before analysis. Avoid interpolating a missing futures history.
