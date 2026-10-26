# Pattern: improvement folder

**Fits when:** while using the brain, the person keeps having ideas about the brain itself ("the summary should show deadlines first", "add a flow for X") and wants them captured without stopping what they're doing.

---

## The structure

A folder, e.g., `_system/improve/` (or a project folder named "Improve my second brain", if they prefer working in a dedicated chat), with:

| File | What goes in it |
|---|---|
| `notes.md` | Ideas and annoyances, one line each, with the date. Anyone (the person, a flow, a chat) can append |
| `done.md` | Ideas applied or dropped, with the date and what was done or why it was dropped |
| `AGENTS.md` / `CLAUDE.md` *(optional)* | "When opened, read `notes.md`, group the ideas, propose the 3 most valuable, and apply only what the owner approves. Move handled ideas to `done.md`." |

Register it in `_system/places.md` (e.g., `improve`, kind `folder`).

## How it's used

- **Capture:** "note for the brain: …" in any session, or a line from the voice bot, goes to `notes.md`.
- **Review:** every week or two, or when the list grows, the person opens the folder (or its chat) and goes through it. Changes to flows use the build cycle; changes to folders use `restructure.md`.
- It's the human counterpart of the health check: the health check finds what's broken, this folder collects what could be better.
