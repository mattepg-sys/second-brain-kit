# Restructuring the second brain

Needs change. Folders, levels and flows can always be changed. This file explains how to do it without breaking anything.

The registries make this safe: flows refer to places by **stable names** in `_system/places.md`, so most moves only need one line changed.

---

## The procedure (any change)

1. **Describe the change** with the person in one or two sentences ("move the Health folder into a Family folder", "the weekly summary should also feed the newsletter draft").
2. **Find what it affects:**
   - which places change (`places.md`);
   - which flows use those places (`flows.md`, and the runbooks in `_system/flows/*/SKILL.md`);
   - which files link to the moved files (search for the old path or name).
3. **Show the plan:** what will move, what will be updated, what will be checked. Wait for OK.
4. **Backup** (recommended): a dated zip, or a git commit.
5. **Apply:** move or rename; update the path in `places.md`; update any runbook or link that used a path directly.
6. **Verify:** run each affected flow once on demand (or in test mode) and check the result.
7. **Record:** update `flows.md` if needed, log the change in `_system/logs/sessions-YYYY-MM.md`, update `PROGRESS.md`. Offer to show the updated map.

Never delete during a restructure unless the person explicitly asks: move to `Archive/` instead.

## Common changes

**Move or rename a folder**
Change its path in `places.md`. If its stable name still fits, keep it; flows don't need to change.

**Add a new level** (an output starts another flow)
Register the output as a place (if it isn't already), add the new flow to the map with the build cycle. Nothing else moves.

**Split a folder in two** (e.g., `Family/` into `Family/kids/` and `Family/home/`)
Create the new places, decide which flows write where, update those runbooks, move the files, verify.

**Merge two folders**
Choose the surviving place; repoint flows; move files; check for duplicates; keep the old name as an alias line in `places.md` for a while ("old-name → new-name").

**Change what a flow does**
Treat it as a small build cycle: update the flow card, do the new behavior by hand once, update the runbook, re-run its tests, note the change in `memory.md`.

**Pause a flow**
Set status `paused` in `flows.md` and stop its schedule. Nothing else changes; it stays on the map, dashed.

**Retire a flow**
Set status `retired`, stop its schedule, move its folder from `_system/flows/` to `Archive/flows/`. Check whether other flows depended on its output.

**Change who runs a flow** (e.g., from on-demand to scheduled, or to another tool)
Update the "Who" and "When" in `flows.md`, set up the new runner, run once, check, then turn off the old one.
