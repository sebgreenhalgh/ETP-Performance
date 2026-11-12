# Data instructions

This directory is a *location for locally downloaded/generated data*, **not** a place to commit licensed datasets or binary dumps.

Data sources, units, as-of timestamps, availability lags and downloading/reproduction steps will be selected in issue #6 and documented in `docs/source_inventory.md` and `docs/data_dictionary.md`.

Important:
- The project brief warns that EIA free futures data terminate in **April 2024**; verify source coverage directly.
- Keep F1/F2 contract definitions and roll conventions; no guessed or silently forward-filled quotes.
- Avoid including API keys and credentials in repo files or notebooks.
- Only include data you have permission to redistribute; synthetic test fixtures should be clearly labeled and small.
