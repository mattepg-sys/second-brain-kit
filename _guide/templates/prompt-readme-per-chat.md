# Prompt: let a project chat write its own README

> Optional (pattern `_guide/library/patterns/project-chats.md`). The owner pastes the prompt below into each existing project chat, one at a time. Replace `{{…}}` first. Translate it into the owner's language if they prefer; the section headings can stay in the document language.

---

```
I'm building a second brain that keeps an overview of all my projects. Please write (or
update) a README.md for this project, in the folder connected to this chat:
{{project folder path}}

Use exactly this structure and these headings:

# <Project name>
- Type: project / area
- Status: active / paused / done
- Last updated: <today, YYYY-MM-DD>
## What it is            (1–2 sentences)
## Goal                  (the outcome I want, and by when)
## Next actions          (- [ ] step — due: YYYY-MM-DD or none)
## Deadlines             (table: Date | What)
## Key people            (name — role; one line each)
## Where things are      (main files and folders, external links, code repositories)
## Updates               (append-only: - YYYY-MM-DD · what happened · source)

Rules:
- Use only what you know from this chat and this folder. Where you're unsure, write "?"
  and list your questions for me at the end of your reply (not in the file).
- Dates as YYYY-MM-DD. Keep it under about 80 lines.
- If a README.md already exists, keep its useful content, move it into this structure,
  and show me what changed before saving.
- From now on, whenever we decide something or a deadline/next action changes in this
  chat, add a line under "Updates" and adjust "Next actions" or "Deadlines".
```
