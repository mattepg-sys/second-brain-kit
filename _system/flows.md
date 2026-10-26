# Flows registry

Every flow (arrow) in this second brain. A flow moves something **from** one or more places **to** one or more places. Places are referenced by their stable names from `places.md`. Each active flow has a folder `_system/flows/<flow-name>/` with its design (`card.md`), runbook (`SKILL.md`), memory and tests.

The map of the second brain is generated from this file and `places.md`.

**Status:** `planned` · `building` · `testing` · `active` · `paused` · `retired`
**Path:** `light` · `standard` · `full` (see `_guide/build-cycle/`)
**Controlled values** (headers, statuses, paths) stay in English; descriptions use the document language.

| Flow | From | To | What moves | When | Who runs it (and device) | Checkpoint | Status | Path | Est. cost / month |
|---|---|---|---|---|---|---|---|---|---|
| | | | | | | | | | |

<!-- Example row (remove when real rows exist):
| inbox-daily-triage | inbox | company-facts, people, archive | files and dictated facts, sorted to the right place | daily 05:30 | Claude scheduled task | owner reviews the daily summary | active | standard | included in plan |
-->

## Dependencies and order
Flows that depend on another flow's output, and the order they must run in.

- (e.g., `voice-capture` must run before `inbox-daily-triage`)

## Shared files and owners
Files written by more than one flow, and which flow "owns" each one.

- (e.g., `People/*.md` — owner: `people-update`; other flows only propose changes)
