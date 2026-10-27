# Step 07 — Foundations

**Goal:** put the second brain in the right place, protect it with a backup, complete its rules, and create only the folders the first flows need.
**Time:** 20–40 minutes for a simple setup; 1–3 hours if a sync app must be installed, existing folders are brought in, or flows must later run with the computer off. Say so up front.
**Output:** a working base structure; `AGENTS.md` completed.

> **Quick start box.** In a quick start, do only: section 1 (short), section 2 (advice in one line), section 3 (name, languages, location, backup choice), and from section 4 only the folders the chosen recipe needs. Don't re-ask anything already in `PROGRESS.md` or `profile.md`.

---

## 1. Where the brain lives

Recommend: **the place they already use every day**. A second brain kept in a separate place nobody opens stays empty. Use what they said in step 03 about where they keep files, the architecture answers in `profile.md`, and the direction agreed in step 06.

| Option | Good for | Watch out |
|---|---|---|
| Local folder only | Trying things out, privacy | No backup, no phone access, automations only when the computer is on |
| Synced folder (OneDrive, Google Drive for desktop, Dropbox, iCloud Drive) | Most people; **needed if the phone should drop notes into the brain** | Set it to keep files on the device ("Always keep on this device" in OneDrive; "Mirror files" in Google Drive) so the AI never meets empty placeholder files; avoid editing the same file from two devices at once |
| Git repository (technical users) | Full history and undo of every change; the same brain on several machines (laptop, home server, VPS) via a private remote such as GitHub | Use Git **instead of** cloud sync for this folder, never inside a synced folder; pull before working, push after. Needed for an always-on agent (`_guide/library/recipes/always-on-agent.md`) |
| They live in Notion, Google Docs or another app | — | Those aren't plain files an AI can open as a folder. Suggest a small synced folder as the brain's "home" (rules, registries, inbox), with the app registered as a place the brain reads from or writes to |

Add: "For flows that should run while your computer is off, the brain (or part of it) needs to be in a cloud folder that cloud tools can reach."

### Google Drive for desktop on Windows (lessons from a real setup)
- Use **Mirror files**, not streaming: the streamed drive (`G:`) was not readable by AI folder tools, even with folders set to "available offline". Mirroring keeps real files in a normal folder.
- Mirroring downloads the whole "My Drive": **check free disk space** first.
- During setup, Drive offers to back up Desktop and Documents: **untick** it unless they want it (it creates duplicate copies).
- On Windows 11, Drive's right-click options are under **Show more options** (or Shift + right-click).
- After setup, **test**: ask the AI to read and write a small file in the new folder before moving anything.

### University or employer accounts
Check before choosing one as the brain's home: does the account stay after graduation or after leaving the job? Does the admin block third-party AI apps or connectors? A personal account is usually safer; the person decides.

### Installing into a folder or vault they already have
If they want the brain *inside* an existing folder (e.g., Documents, a Drive folder) or an Obsidian vault:
- copy `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `START-HERE.md`, `_guide/` and `_system/` into its root (and the base folders if they don't exist);
- if `AGENTS.md`, `CLAUDE.md` or `GEMINI.md` already exist there, **merge, never overwrite**: show the merged version and wait for a yes;
- if folders named like the base places already exist with another meaning, register different paths for `inbox`, `people`, `archive` in `places.md`;
- register existing top-level folders gradually: only those a flow uses; the rest can be one place (`existing-files`, kind `folder`);
- in Obsidian, the person can hide `_guide/` from search and graph (Settings → Files & links → Excluded files).

### Bringing existing folders in (only if they want)
- **No need to restructure everything first.** Folders can stay where they are and just be registered in `places.md`, or come in one at a time.
- **Copy, don't move.** Copy into the brain, check the copy (the AI can compare file counts), then archive the originals with the person's OK.
- **Code projects stay outside the synced folder** (`node_modules`, `.git` and build files sync badly). The project's README links to the code's path or repository.
- **AI chats or projects connected to the old folders** keep using the old path and may recreate empty folders there. Before archiving or deleting the originals, **reconnect each chat or project to the new path**, or disconnect the old one. Make a checklist of those chats with the person.

### Moving the folder
If the kit folder needs to move, give click-by-click steps for their system. Moving it usually disconnects the AI tool from the folder, so **do it at the end of the session**: write in `PROGRESS.md` "Next: reconnect the folder from its new location, then say *Let's continue*". If a sync app must be installed first, guide them step by step and offer to continue after.

### More than one device
If they use more than one computer, recommend that each scheduled flow runs on **one** device only (noted in the "Who runs it" column of `flows.md`), to avoid duplicates. Phones are usually for capture only.

## 2. Backup (strongly recommended)

Before creating folders or moving their own files, recommend a backup:
- **Beginner:** a dated zip copy of the folder (e.g., `second-brain-backup-2026-10-24.zip`) kept outside the synced folder, repeated weekly or before big changes.
- **Technical:** git, committing at the start and end of each working session. If the brain lives in a synced folder, either use git **instead of** that sync (with a private remote), keep the repository outside the synced folder, or use dated zips.

If they say "later", add it to `_system/BACKLOG.md` with the exact steps. If they decline, record it in `AGENTS.md` section 5 and continue.

## 3. Complete `AGENTS.md`

Fill in the placeholders:
- owner name; the languages (copy from `PROGRESS.md`) and the per-folder option;
- where the brain lives, the devices, and the backup choice;
- any owner's choices made so far (e.g., "health data stays in the brain; the owner accepts that the AI assistant can read it"), and remove the example row in section 5.

Keep the default rules unless the person wants to change them. In chat mode, give the completed file to save.

## 4. Create only what is needed now

1. Check the base places exist (`Inbox/`, `People/`, `Archive/` by default). Offer **once** to rename them into the document language now, before any flow exists; if they accept, rename and update their paths in `_system/places.md`.
2. Add a `backlog` place if it's missing (`_system/BACKLOG.md`, kind `destination`).
3. Create the folders the **first flow** needs, plus any project or area folders the person wants to start using right away. For each:
   - give it a clear name in their document language;
   - add a `README.md` from `_guide/templates/project-readme.md` (what it is, status, next action);
   - for projects that will hold many files, offer (don't impose) the common inner structure: `source-of-truth/` (canonical facts, each with its source), `deliverables/` (what goes out), `sources/` (originals the AI only reads), and optionally a protected subfolder the AI never touches (e.g., `DO-NOT-TOUCH/`). Create only the subfolders they want;
   - register it in `_system/places.md` with status `active` (add `protected` where needed). Similar subfolders (e.g., one per client) can be registered as one place with a pattern (`Clients/<client>/`).
4. Don't create folders for "Later" ideas. They stay on the map as `planned`.

If they already have folders to bring in (e.g., a project folder on the Desktop), offer to copy them in and register them, following "Bringing existing folders in" above. Confirm before overwriting anything.

For people with many contacts, offer (don't impose) the pattern `_guide/library/patterns/contacts-table.md` instead of one file per person.

## 5. Show the result

List the structure (a short tree), and say in one sentence what each top-level folder is for. Ask if anything feels wrong.

## 6. Save and move on

Update `_system/PROGRESS.md`: step 07 ticked (or "partial" in a quick start); next step: build the first flow with `_guide/build-cycle/cycle.md` (or the chosen recipe). Log the session in `_system/logs/sessions-YYYY-MM.md`.

Transition: "The foundations are ready. Let's build your first flow, carefully and step by step."
