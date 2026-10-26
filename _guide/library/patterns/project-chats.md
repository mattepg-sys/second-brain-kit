# Pattern: project chats + a horizontal layer

**Fits when:** the person already has one AI chat (or Project) per topic, each with its own folder connected, and the chats work well. What's missing is the overview: deadlines, next actions and people across all projects.
**Doesn't fit when:** the person doesn't use chats this way. Don't create this structure for them.

---

## The idea

- **Vertical:** each project keeps its own chat and folder. Nothing about how they work there changes.
- **Horizontal:** the second brain sits above them. It doesn't redo the projects' work; it reads one short, standard file from each project and builds the overview.

```
            Control-tower session (reads every README)
     ┌──────────────┬──────────────┬──────────────┐
  Project A      Project B      Project C      Study
  chat + folder  chat + folder  chat + folder  chat + folder
  README.md      README.md      README.md      README.md
```

## 1. A README with a fixed structure in every project

Use `_guide/templates/project-readme.md`. The fixed sections (What it is, Goal, Next actions with due dates, Deadlines, Key people, Where things are, Updates) make the READMEs easy to read across projects, by people and by flows. **Updates is append-only**: new lines go at the bottom, old lines are never rewritten.

## 2. Each project chat writes its own README

The chat that knows the project best writes the README. Give the person the prompt in `_guide/templates/prompt-readme-per-chat.md` to paste into each project chat. Do it one chat at a time; check the first result together.

Optionally, add a per-folder instruction file so the project chat keeps the README current: `_guide/templates/project-agents.md` (save it as `CLAUDE.md` or `AGENTS.md` inside the project folder, depending on the tool).

## 3. The control tower

A session (or a scheduled flow) that reads all the READMEs and produces the overview: deadlines in the next 14 days, overdue next actions, people to follow up, projects with no update for a while. It's a normal flow: design it with the build cycle.

## 4. "Where everything goes"

Agree on one short convention and write it in `AGENTS.md` section 2 (or a small `_system/where-things-go.md`), for example:

| Kind of thing | Goes to |
|---|---|
| Something about one project | That project's folder (its chat updates the README) |
| A to-do with no project | `_system/BACKLOG.md` |
| A fact about a person | `People/` |
| Anything unsorted | `Inbox/` |
| Code | Outside the synced brain (disk or GitHub); the project README links to it |

## 5. Moving project folders into the brain (if they want)

- **No need to restructure everything first.** A working overview matters more than tidy folders; projects can move one at a time, or stay where they are and just be registered in `_system/places.md`.
- **Copy, don't move.** Check the copy, then archive the originals.
- **Reconnect every chat to the new path** before deleting or archiving the originals. A chat still pointing at the old path may recreate empty folders there.
- Code projects stay outside the synced drive.
