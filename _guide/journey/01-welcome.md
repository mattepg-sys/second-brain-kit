# Step 01 — Welcome

**Goal:** make the person feel welcome, agree on languages, learn what you (the AI) can do in this session, and choose between the full journey and a quick start.
**Time:** about 5–10 minutes.
**Output:** `_system/PROGRESS.md` started; languages and choices noted.

---

## 1. Greet and set expectations (one short message)

Use the language the person wrote in. If their only message was the trigger sentence in English, open with one short line in English and the same line in two or three other likely languages, and ask which they prefer.

Say, in your own words:
- what a second brain is, in one sentence ("a set of folders and small automations that collect information where it arrives and deliver it where you need it");
- how it works: first we imagine and design together, then we build **one flow at a time**;
- they can stop at any time and continue later, in any chat;
- you give advice, but **they decide** everything;
- **what to expect** (adapt from `README.md`, "Is it for you?"): what they'll end up with (a map of their second brain, a base folder, a first flow that saves real time, a way to add more), roughly how long it takes (3–4 hours to a first flow; 8–10 hours if flows must run with the computer off; or a quick start under an hour), and what's needed (an AI assistant, ideally a cloud folder; costs shown before any decision);
- **tips:** they can **dictate** instead of typing (the AI app's microphone, Windows Win + H, Mac dictation, the phone keyboard's microphone; if the AI app has no microphone, dictate in another app such as Word, Google Docs, Gemini or ChatGPT and paste); they can answer several questions in one long message; they can skip anything.

Keep it to a short message. Then ask how they'd like to be called. Don't list all the steps.

## 2. Languages (one question, with a default)

"Shall we do everything in <their language>: our conversation, the documents of your second brain, and what your automations write?" *(default: yes)*

If they want different languages, ask the three separately (conversation · documents · automation outputs) and offer: "If you prefer, inside each folder I can use the language that folder is already written in." *(default: no)*

From now on, speak only in the chosen conversation language.

## 3. Capability check

Work out what you can do (see `_guide/00-for-the-ai.md`, section 3). Detect what you can yourself; ask only what you can't, briefly:
- **File mode:** try to read `_system/PROGRESS.md`. If it works, you're in file mode; say nothing more about it.
- **Chat mode:** if you can't read files, explain in one sentence how it will work (you'll ask them to upload files, and you'll give them files to save), and suggest a Project if their assistant has one.
- Ask which AI tool and plan they're using now, and whether it's the one they normally use. *(default: "this is my usual one")*

Don't ask about connectors or scheduled tasks yet; you'll need that only when building automations.

## 4. Technical comfort (one question)

"How comfortable are you with technology?"
- **Beginner** — "I use apps, I don't install or configure much"
- **Some experience** — "I've set up a few tools or automations"
- **Technical** — "I'm fine with code, terminals, APIs"

*(default: some experience)*

Adapt everything that follows: fewer terms and more step-by-step for beginners; more options and shortcuts for technical people. They can change level at any time.

## 5. Full journey or quick start

If the person already said which they want, confirm it in one line and move on. Otherwise offer the choice, with honest pros and cons. Recommend the full journey, but let them choose.

| | **Full journey** (recommended) | **Quick start** |
|---|---|---|
| What happens | Discover → your story → challenge → draw your map → design review → foundations → first flow | Minimal setup → one simple, proven first flow → design later |
| Time to first working flow | About 3–4 hours, best over 2–3 sittings (8–10 hours in total if flows must run with the computer off) | About 30–45 minutes with an AI that opens folders; 60–90 minutes in a chat-only app |
| **Pros** | You build what *you* need most, in the right order; the structure fits your life from day one; fewer things to redo later; you see the whole map before building | You see real value today; good if you're short on time or unsure a second brain is for you; motivation from a quick win |
| **Cons** | Takes longer before anything works; needs a calm moment (especially for the drawing) | The first flow is a generic one, not necessarily your biggest need; the structure is minimal and may need reorganizing later; without the map it's easier to add flows randomly and overbuild |
| Best for | People who want a second brain that lasts | People who want to try first and design later |

Say: "You can switch at any time. If you start quickly, I'll suggest doing the design steps afterwards."

### If they choose the quick start
1. Ask only:
   - which of these they'd like first:
     - **Inbox triage** (`_guide/library/recipes/inbox-triage.md`) — files and notes dropped in one place get sorted;
     - **Voice capture** (`_guide/library/recipes/voice-capture.md`) — spoken ideas become text in the inbox (usually together with inbox triage);
     - **Course deadlines** (`_guide/library/recipes/course-deadlines.md`) — for students: deadlines into a calendar and a weekly plan;
   - the folder or app where they work every day;
   - their devices (computer and phone).
2. Fill a **minimal** `_system/profile.md` (name, languages, technical comfort, devices, AI tool, and any preference the recipe needs).
3. Do the short version of step 07 (`_guide/journey/07-foundations.md`, "Quick start" box): where the brain lives, backup advice, `AGENTS.md` basics, only the folders the recipe needs.
4. Build the chosen recipe with the path it recommends.
5. When it works, offer: "Now that you've seen it work, want to design the rest of your second brain? It starts with step 02." Note in `PROGRESS.md`: "Steps 02–06 to do; step 07 partial (complete AGENTS.md and register new places later; don't recreate existing folders)."

## 6. Save and move on

Update `_system/PROGRESS.md` (in chat mode, you can wait for a natural pause):
- journey started: yes, with today's date; journey type: full or quick start;
- step 01 ticked; session capabilities and mode;
- key answers: name, languages, per-folder option, technical comfort, AI tool and plan;
- next step: `_guide/journey/02-discover.md` (full) or the chosen recipe (quick start).

Transition (full journey): "Great. Now let me show you what a second brain can do, so you can start imagining yours."
