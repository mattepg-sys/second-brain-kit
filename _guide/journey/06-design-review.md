# Step 06 — Design review

**Goal:** turn the hand-drawn map into a clear design, give honest feedback, show the tool options and their cost direction, and agree on the first arrow to build.
**Time:** 20–30 minutes.
**Output:** draft entries in `_system/places.md` and `_system/flows.md` (status `planned`), and the first arrow chosen.

---

## 1. Read the map back

Transcribe what you see into two short lists and ask the person to confirm or correct:

- **Places:** name, kind (source / folder / destination), what it holds.
- **Flows:** from → to, what, when, who, check, and which are starred ★ or circled ◯.

If something is unreadable, ask. Don't guess silently.

## 2. Give feedback (critical about why, positive about how)

Look for these, and mention only what is relevant:

| Look for | Why it matters |
|---|---|
| Arrows without a "when" | Decide: on a schedule, on an event, or on demand |
| Places that receive a lot but give nothing out | Collecting without using |
| Many arrows into the same file | Who "owns" it? Two flows writing the same file can overwrite each other |
| Flows that depend on another flow | Order matters (e.g., transcription before triage) |
| Missing basics | An inbox, a place for people, an archive, a place for decisions that need them |
| Sensitive data (health, money, family) | Advise where it lives and which services see it; they decide |
| External actions (sending, posting, paying) | Advise a checkpoint; explain the risk once (see `_guide/knowledge/safety-advice.md`); they decide |
| Too many arrows for now | Remind: the map is the destination; we build one at a time |

End with what is strong about their design. Be specific.

## 3. Tools and costs, place by place and arrow by arrow

For each source and for the most important arrows, give 2–3 options, from simplest to most powerful, each with its cost direction (free / included in a plan / paid, and how cost grows with usage).

- Start from what they already use (step 03).
- Use `_guide/knowledge/` as your starting point, opening only the section you need: `connecting-platforms.md` (the platform matrix) for a specific platform, `ai-assistants-2026-10.md` for scheduled tasks and connectors, `tools-and-costs-2026-10.md` for automation platforms and capture tools. They were checked in October 2026; anything not tagged as verified must be checked.
- When they name a specific bank, school, app or platform, **research it specifically** if you can search the web. If you can't, say what you know may be outdated and how they can check.
- Be positive: if the obvious way is blocked, look for another (export file, calendar link, email forwarding, an automation platform, a small script).

### Where flows run (explain once, when relevant)
- **On their computer** (the AI desktop app or a script): can use local folders, but the computer must be on when the flow runs.
- **In the cloud** (scheduled tasks of AI assistants, Zapier, Make, n8n cloud, a cloud script such as Google Apps Script): runs even with the computer off, but usually only reaches cloud services and connected apps, not local folders.
- **Connectors differ in what they can do:** some can create files but not change existing ones (see `_guide/knowledge/field-notes-2026-10.md`, section 7). A flow that only **creates** outputs fits a cloud task more easily than one that **modifies** files. Test the exact action before relying on it.

## 3b. Where the brain lives (decide now: it shapes the tools)

Storage decides which tools can reach the brain, so settle the direction here, before choosing the first arrow's tools. Use the architecture answers from step 03 (in `profile.md`). A simple decision tree, as advice:

```
Must flows run with the computer off, or the phone drop notes into the brain?
├─ No  → a local folder, or a synced folder they already use (simplest)
└─ Yes → a synced cloud folder, kept fully on the computer
         ├─ Google Drive → "Mirror files" mode (streaming isn't readable by AI folder tools; check disk space)
         ├─ OneDrive     → "Always keep on this device" on the brain folder
         └─ Dropbox / iCloud → keep the folder downloaded (not online-only)
Is the account a university or employer one?
└─ Check it stays after graduation/leaving and that the admin allows AI apps; a personal account is usually safer
Code projects?            → keep them outside the synced folder (disk or GitHub); the brain links to them
Existing project chats?   → see the pattern `_guide/library/patterns/project-chats.md` (only if it fits)
```

Give a hint of the base structure they'll get (rules, `_system/`, Inbox, People, Archive, plus only the folders the first flows need). The details and the move itself happen in step 07.

**No need to reorganize everything first.** Existing folders can stay where they are and be registered, or move in one at a time later. A working first flow matters more than tidy folders.

## 4. Choose the first arrow

Recommend one, with reasons. A good first arrow is:
- frequent (daily or weekly);
- valuable (removes a real pain from step 03);
- simple (few places, tools they already have);
- low risk (reads more than it sends; mistakes are easy to fix).

If their circled ◯ arrow is risky or complex, say so honestly and suggest either a simpler version of it or a different first arrow. They decide.

If the chosen arrow only gives value together with the next one (e.g., voice capture is useful only once the inbox is sorted), plan to build both in the same cycle.

## 5. Write the design down

1. Add the places to `_system/places.md` (status `planned`, except the base folders already active). Give each a short stable name (lowercase, hyphens). Register a parent folder with a pattern (e.g., `Clients/<client>/`) when its subfolders are alike; register a subfolder separately only if a flow treats it differently or it is protected.
2. Add the flows to `_system/flows.md` with status `planned`, including the four labels and a rough monthly cost estimate where possible. Fill in "Dependencies and order".
3. Mark the first arrow as the next to build.

In chat mode, give the updated files to save.

## 6. Save and move on

Update `_system/PROGRESS.md`: step 06 ticked; key answers: first arrow chosen, main tool choices. Next step: `07-foundations.md`.

Tell them they can ask to see their map (generated from the registries) at any time.

Transition: "Now let's prepare the foundations: where your second brain lives and the basic structure. Then we build the first flow."
