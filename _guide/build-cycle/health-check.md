# The health check

A flow that keeps the second brain trustworthy. It surfaces **only what the system can't fix by itself**: decisions waiting for the owner, things that stopped working, and things drifting out of date.

**Suggest it when 2–3 flows are active.** Build it with the standard path (`path-standard.md`). Name: `health-check`.

---

## Suggested card (adapt with the owner)

| Label | Default |
|---|---|
| What | A short report of problems and decisions needed |
| When | Daily before the owner starts the day, or weekly (e.g., Sunday evening) |
| Who | The owner's AI assistant (scheduled task) or on demand ("run the health check") |
| Checkpoint | The owner reads the report; nothing is changed without their OK, except trivial fixes they have allowed |

## What it checks (choose what fits)

**Flows**
- Each `active` flow in `_system/flows.md` has run when expected (look at its log). Flag flows that didn't run or that failed.
- Flows with many "Proposed" lessons waiting in their `memory.md`.

**Registries vs. reality**
- Every place in `_system/places.md` exists; every top-level folder is registered (ignore `_guide/`, `_system/`, dot-folders such as `.git/` or `.obsidian/`, and generated files such as `MAP.html`).
- Every project or area folder has a `README.md` with a status and a next action.

**Inbox and backlog**
- Items in `Inbox/` older than N days (default 7).
- Items in `_system/BACKLOG.md` older than N days (default 14).

**Knowledge**
- Possible duplicates (two files about the same person or project).
- Facts without a source in source-of-truth files.
- People with open promises older than N days (default 30).
- Projects whose next action hasn't changed in N days (default 30).

**Changes**
- Files changed since the last check without a matching log line (optional, if the tools allow it).

**Costs** (optional)
- A reminder of the estimated monthly cost from `flows.md`, and anything that looks unusually high.

## Output

Write the report to `_system/health/YYYY-MM-DD.md`, and add to `_system/BACKLOG.md` only the items that need the owner, replacing the previous health-check entry (so the backlog doesn't grow every day). Report shape:

```
## Health check — YYYY-MM-DD
Needs you (3):
- inbox: 5 items older than 7 days (oldest: 2026-10-12, invoice.pdf)
- flow meeting-capture did not run yesterday (last success: 2026-10-22)
- People/maria-lopez.md: promise "send deck" open since 2026-09-20
All good: 4 flows ran, registries match folders.
```

Keep it short. If everything is fine, one line is enough.

## Fixing things
By default the health check only reports. The owner can allow it to fix trivial issues on its own (e.g., add a missing `README.md`, register a new folder). Record that choice in `AGENTS.md` section 5.
