# Recipe: Voice capture

> Ideas, facts and to-dos spoken out loud become text in the inbox, ready to be sorted.
> Inspired by a founder's real setup: a dictation app for quick notes and a script that turns voice recordings into text in the inbox every morning.

**Good first flow because:** capture is where most second brains fail. If saving a thought takes more than a few seconds, people stop doing it. Voice is the fastest way.
**Suggested path:** light.

---

## 1. Pre-filled flow card (adapt it)

| Label | Default |
|---|---|
| **What** | Spoken notes, as text (one daily file, or one file per note) |
| **When** | Whenever the owner speaks; text lands in the inbox within minutes or by next morning |
| **Who** | Depends on the version (phone, dictation app, automation, or local script) |
| **Checkpoint** | None needed for capture; the inbox triage sorts it later |

- **From:** the owner's voice (phone or computer)
- **To:** `inbox` (e.g., `Inbox/recordings/YYYY-MM-DD.md`, one file per day with timestamps)
- **Done means:** a note spoken on the phone appears as readable text in the inbox, without the owner copying anything by hand.

## 2. Choose your version

Recommend based on their devices and technical comfort. Prices as of October 2026; check current ones if you can search.

| Version | How it works | Good for | Cost direction |
|---|---|---|---|
| **A. Phone's built-in transcription** | Record with the phone's voice recorder; it transcribes; share the text to the brain's cloud folder (or email it to yourself if email-to-inbox exists) | Everyone; zero setup | Free. Check language support: some built-in recorders transcribe many languages (including Italian and Spanish), others only a few |
| **A2. Keyboard dictation (any phone)** | Dictate with the keyboard's microphone into a notes app; then Share → your cloud app (Google Drive, OneDrive…) → the brain's `Inbox/recordings/` | Any phone, including brands without built-in transcription | Free; most phone keyboards support many languages (check yours saves a text file) |
| **B. Dictation app** | Dictate directly into a note or document saved in the brain's synced folder | People who dictate a lot, on computer and phone | Free tiers with word limits; paid plans around $8–15/month. Examples: Wispr Flow, Superwhisper (has a free local mode), Aqua Voice |
| **C. Messaging bot** | Send a voice message to a personal Telegram bot; an automation (n8n, Make, Zapier) transcribes it and saves a Markdown file in the brain's cloud folder | Phone-first people; semi-technical; **works with the computer off** | Telegram bots are free; transcription APIs cost cents per hour of audio; automation free tiers often enough. A complete, tested version with Google Apps Script + Groq + Claude API (it also creates calendar events): `telegram-voice-bot.md` |
| **D. Local transcription** | Voice files dropped in `Inbox/recordings/` are transcribed on the computer with Whisper (free, open source), on demand or on a schedule | Technical users; privacy | Free; needs a reasonably capable computer |

**Phone sync (important for A, A2 and B):** many cloud storage apps on phones (especially Android) don't keep a folder synced both ways like on a computer. Sharing or uploading a file to the cloud app works; editing a synced folder directly may not. Options: upload/share each note, use a note app with its own sync, or use version C.

## 3. Setup

**Prerequisite for phone capture:** the brain's folder must be inside a cloud folder that the computer syncs (e.g., Google Drive for desktop in "Mirror files" mode — not streaming, which AI folder tools couldn't read in a real Windows test — or OneDrive with "Always keep on this device"). If it isn't, do that first (step 07, section 1).

1. Ask the owner how they'd naturally capture ideas: phone or computer, talking or typing, which languages, which phone brand, and **whether capture must work with the computer off** (if yes, don't recommend options that need it on). If you can search, check what their phone's recorder and keyboard can do.
2. Pick a version together (start simple; it can be upgraded later).
3. Create `Inbox/recordings/` and register it as a place (`recordings`).
4. Set up the chosen version, step by step, adapted to their devices. If you can search, check the current setup steps for the specific app.
5. Test: the owner records two notes (one short, one long, in their language). Check that both arrive as readable text.
6. Write a short runbook (`_system/flows/voice-capture/SKILL.md`) describing where notes arrive and how they're formatted, so the inbox triage knows how to read them.
7. Register the flow in `_system/flows.md`.

## 4. Format of captured notes

One file per day keeps things simple for the triage:

```markdown
# Recordings — 2026-10-24

## 08:42
Idea for the onboarding email: send the checklist on day 2, not day 1.

## 13:15
Call Marta about the school trip form, due Friday.
```

If the version creates one file per note, use names like `2026-10-24-0842.md` (phones often name shared notes differently, e.g., without the year; inbox triage will take the date from the file's modified time and rename it when archiving).

## 5. Tests

| Test | Expected |
|---|---|
| A 10-second note in the owner's main language | Text arrives in the inbox, accurate enough to understand |
| A 2-minute note with names and numbers | Names and numbers mostly right; the owner knows to check them |
| A note in their second language (if any) | Works, or the limitation is known |
| Phone offline when recording | Arrives once back online (or the limitation is known) |

## 6. Pitfalls and tips
- **Names and numbers** are where transcription fails most. Keep the "Names and spellings" list in `_system/profile.md`; pass it to the transcription service when it accepts a vocabulary or prompt, and let the triage correct names from it.
- **Don't over-process at capture.** Capture is dumb on purpose; cleaning, sorting and extracting happen in the inbox triage.
- **Privacy:** cloud transcription sends audio to a provider. For sensitive notes, local options (version D, or apps with on-device modes) keep audio on the device.

## 7. Grow it next
- Inbox triage turns each dictated fact into a fact with its source, each promise into a person's open promise with a due date, each other to-do into the backlog.
- Meeting capture: the same idea for whole meetings (recorders that export text).
- "Chat with your brain": the same bot can answer questions, not just capture (technical).
