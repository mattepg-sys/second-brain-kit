# Logs

What happened, when. Flows and the AI only append; past lines are not edited.

- One file per flow and month: `<flow-name>-YYYY-MM.md`
- One line per run: `YYYY-MM-DD HH:MM · result (ok / failed / skipped) · what changed · anything for the owner`
- Guide and setup sessions log to `sessions-YYYY-MM.md`.

The health check (if active) reads these logs to spot flows that stopped running or keep failing.
