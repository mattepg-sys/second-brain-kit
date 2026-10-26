# Field notes: what a real build taught (October 2026)

> Lessons from the first full test of this kit: one person (a university student and founder with about a dozen projects, Windows laptop, Android phone, Claude Max) building their own second brain over three sittings.
> **These are experiences, not rules.** Use them to anticipate problems and to suggest options. Every person's setup is different: don't push a pattern because it worked here.

---

## 1. Time, honestly

- Real time was about **9–10 hours over 3 sittings**, not 3–4.
- Steps 01–06 (imagining, challenging, drawing, reviewing) took roughly the time the guide estimates.
- **Infrastructure took most of the time:** choosing and setting up storage, moving existing folders, and making a flow run with the computer off (a phone bot, a cloud script, API keys).
- Rule of thumb to share up front: **3–4 hours** to a first flow that runs when you ask; **8–10 hours** if flows must run on their own while the computer is off.

## 2. Ask early: the questions that changed the architecture

Each of these, answered late, caused rework. Ask them in step 03 (they are in that step's file):

| Question | Why it matters |
|---|---|
| Should flows work while your computer is off? | Decides local vs cloud storage, and whether scripts or cloud tasks are needed |
| Will you dictate a lot (voice)? | Changes the capture design; proper names will be misheard |
| How much free space do you have in your cloud storage, and on your disk? | Mirroring a cloud drive downloads all of it |
| Do you already work in AI chats or projects with folders connected? | Moving folders breaks those chats; it may suggest the "horizontal layer" pattern |
| Are there code projects among the folders you want to bring in? | Code (`node_modules`, `.git`) doesn't belong in a synced drive |

## 3. Voice dictation and names

- Dictating answers made the interview much faster and richer. Suggest it at the start (the AI app's microphone, or the phone or computer's built-in dictation).
- Long voice answers covering several questions at once worked well: the AI should accept them and sort them.
- **Proper names get mangled** (a company called "Build It Up" became "BeItUp"). What helped:
  - the AI confirming unusual names back once;
  - a short **"Names and spellings"** list in `_system/profile.md` (heard as → correct), read by every flow;
  - passing the same name list to the transcription service, when it accepts a vocabulary or prompt (Whisper-style APIs accept a `prompt`).

## 4. Storage on Windows with Google Drive for desktop

- **Streaming mode** (a virtual `G:` drive) was **not readable** by Claude's folder tools, even with folders marked "available offline". **Mirror mode** worked (files live in a normal folder on disk).
- Mirroring downloads the whole "My Drive": check free disk space first, or mirror only what's needed.
- During setup, Google Drive offers to back up Desktop and Documents: **untick** it unless wanted, or it duplicates folders.
- On Windows 11, Drive's "offline access" option is under **Show more options** (or Shift + right-click).
- A **university or employer account** (OneDrive, Google Workspace) was a poor home: it may close after graduation, and admins may block third-party apps. A personal account was chosen instead. Check, don't assume.

## 5. Moving existing folders

- **Copy, don't move**, then check the copy, then archive the originals.
- **Code projects stay outside the synced drive** (on disk or in GitHub); the brain keeps a short note with the path or repository link.
- **Existing AI chats with a connected folder** kept writing to the old path, and recreated empty folders after the move. Before deleting or moving originals, **reconnect every chat or project to the new path** (or disconnect the old one).
- There was **no need to restructure everything first**: a working first flow mattered more than tidy folders.

## 6. Working in many project chats ("vertical") plus a brain ("horizontal")

The person already had one AI chat per project, each with its own folder. Rather than replacing them, the brain became a **horizontal layer** above them:
- each project folder got a `README.md` with a fixed structure, **written by that project's own chat** using a standard prompt;
- one "control tower" session reads all the READMEs for the overview (deadlines, next actions, people).

Full pattern: `_guide/library/patterns/project-chats.md`. It fits only people who already work this way.

## 7. Connectors: what they really did (October 2026, Claude)

- **Google Drive connector:** could **create** new files, but **could not modify the content of existing ones** (and couldn't read plain text/Markdown content reliably). So:
  - flows that **create** an output (a daily summary file) can run as cloud scheduled tasks;
  - flows that **modify** existing files (append to a project README, update a person) need a different executor: the desktop app with the computer on, or a script (e.g., Google Apps Script, which can rewrite a file with `setContent`).
- **Google Calendar connector:** full create / update / delete, as documented.
- **Lesson:** before designing a flow around a connector, **run a 2-minute real test** of exactly what the flow needs (read this file, change this line, create this event). Documentation and reality differed.

## 8. What worked for capture with the computer off

A personal **Telegram bot → Google Apps Script → Groq Whisper (transcription) → Claude API (decides and acts) → Drive and Calendar**. Notes cost about $0.001–0.002 each. Full recipe, with the pitfalls that took hours to find: `_guide/library/recipes/telegram-voice-bot.md`.

## 9. Calendars from several organizations

- An Outlook calendar shared by email: the "Add calendar" button didn't work in Google; the **ICS link** ("this URL") at the bottom of the email, added in Google Calendar as **From URL**, did.
- A Google Workspace calendar from another organization showed only **free/busy**: the admin decides.
- The choice that worked: **read all calendars, write only to the personal one.**

## 10. Decisions this person made (examples of owner's choices, not defaults)

- The bot may create, edit and delete calendar events, and always reports what it did; when several events could match, it asks. (Deleted events stay in Google's trash for 30 days.)
- Emails are never sent without an explicit "send".
- Event durations are estimated with common sense when not said.
- Data must not be used for model training: privacy settings checked in each tool.
- Personal API keys only (never an employer's).
- Secret values are never shown in chat or saved in files.

## 11. Mistakes the guiding AI made (avoid them)

- Recommending Drive **streaming + "offline"** instead of mirroring.
- Writing a duplicate-message guard that only lasted a few minutes (see the recipe: it must be permanent).
- Suggesting "use Claude on your phone while the computer is on" first, when the person had said the computer would be off.
- Assuming a connector could modify files without testing it.

## 12. Patterns that emerged (optional)

- **An improvement folder and chat** for ideas about the brain itself: `_guide/library/patterns/improvement-folder.md`.
- **Contacts as a table plus a few cards**, for people with many contacts: `_guide/library/patterns/contacts-table.md`.
- A health check made sense only after 2–3 flows were running.
