# Places registry

Every place in this second brain: folders, files, external apps and inboxes. Flows refer to places by their **stable name** (first column), never by path. To move or rename a folder, change only its path here (and tell the AI, so it can check the flows that use it).

**Kinds:** `source` (where information comes from) · `folder` (where it lands) · `destination` (where it goes out) · if a place is more than one, write its main kind first.
**Controlled values** (table headers, kinds, statuses) stay in English; descriptions use the document language.
**Similar subfolders** (e.g., one per client) can be one place with a pattern: `Clients/<client>/`.
**Status:** `active` · `planned` · `paused` · `archived` · add `protected` to any place an AI must never modify (e.g., `active, protected`)

| Name | Kind | Location (path or app) | What it holds | Language | Status |
|---|---|---|---|---|---|
| inbox | folder | `Inbox/` | Everything that arrives before being sorted | {{doc language}} | active |
| people | folder | `People/` | One file per person: who, when you met, what connects you | {{doc language}} | active |
| archive | folder | `Archive/` | Anything no longer active; nothing is deleted | — | active |
| backlog | destination | `_system/BACKLOG.md` | Decisions and to-dos waiting for the owner | {{doc language}} | active |

<!-- Example rows (remove when real rows exist):
| company-facts | folder | `MyCompany/source-of-truth/` | Canonical facts and figures, each with its source | English | active |
| gmail | source | Gmail (read-only connector) | Email threads | — | active |
| reading-queue | destination | e-reader / phone | PDFs to read | — | planned |
-->
