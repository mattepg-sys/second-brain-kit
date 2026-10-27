# Ideas catalog

A menu of flows people build into their second brains, grouped by life area. Use it to inspire (step 02), to fill gaps in a design (step 06), and when the person asks "what else could it do?".

**How to use it (for the AI):** don't read it out. Pick the 3–5 ideas closest to what the person said. For each idea you propose, adapt the example to their life, check current tools and prices if you can search, and build it with the build cycle. Ideas marked ⭐ have a complete recipe in `recipes/`.

**Each idea shows:** what it does · Alex's version (Alex is the example persona: a founder, part-time master's student and parent of two) · tool options from simplest to most powerful · cost direction · suggested build path.
**Costs** are directions as of October 2026, not quotes. "Included" means covered by a typical ~$20/month AI assistant plan or a free tier.

---

## 1. Capture

### ⭐ Voice capture
- **What:** ideas spoken while walking or driving become text in the inbox.
- **Alex:** dictates three ideas on the way to the office; they're in `Inbox/recordings/` before he sits down.
- **Tools:** phone's built-in recorder transcription → dictation apps (Wispr Flow, Superwhisper, Aqua Voice) → a Telegram bot or automation with a transcription API (worked example with the computer off: `recipes/telegram-voice-bot.md`) → local Whisper.
- **Cost:** free to ~$15/month; transcription APIs cost cents per hour of audio.
- **Path:** light

### ⭐ Inbox triage
- **What:** everything dropped in `Inbox/` is sorted into the right folders, with a short summary of what went where.
- **Alex:** every day at 05:30, signed documents go to their project, dictated facts to the right file, people to `People/`.
- **Tools:** on demand with any AI that can open the folder → a scheduled task in the AI assistant → a scheduled script running an AI command-line tool.
- **Cost:** included; scheduled runs need a plan that supports them.
- **Path:** light (on demand) → standard (scheduled)

### Web and reading clipper
- **What:** articles and pages you save land as clean Markdown notes in the inbox.
- **Alex:** clips market reports from the browser while researching competitors.
- **Tools:** Obsidian Web Clipper (free) → Readwise Reader (paid) exporting to the folder.
- **Cost:** free to ~$10/month.
- **Path:** light

### Email to inbox
- **What:** forward any email to a special address and it becomes a note in the inbox.
- **Alex:** forwards receipts and interesting threads from his phone.
- **Tools:** an email filter + automation (Zapier, Make, Power Automate, Apps Script) saving to a cloud folder.
- **Cost:** free tiers usually enough.
- **Path:** light

### Photos of paper
- **What:** a photo of a whiteboard, letter or receipt becomes searchable text.
- **Alex:** photographs the whiteboard after strategy meetings.
- **Tools:** phone scanner apps → upload to the inbox → AI extracts text and key points.
- **Cost:** free or included.
- **Path:** light

---

## 2. Work and projects

### Facts with their source
- **What:** important facts, figures and decisions from meetings, emails and documents are added to the project's source-of-truth file, each with where and when it came from.
- **Alex:** "Runway is 14 months (CFO email, 2026-10-03)" lands in `Brightloop/source-of-truth/finance.md`.
- **Tools:** part of inbox triage or meeting capture; AI with file access.
- **Cost:** included.
- **Path:** standard

### Project status at a glance
- **What:** every project folder's README is kept current: status, next action, last change.
- **Alex:** each Friday, all project READMEs are refreshed from the week's notes.
- **Tools:** on-demand or scheduled AI task.
- **Cost:** included.
- **Path:** light

### Overview across project chats
- **What:** for people who work in one AI chat per project: each chat keeps a standard README; one session reads them all for deadlines, next actions and people.
- **Alex:** (not Alex's setup; a real user's) a Monday overview of 12 projects in one page.
- **Tools:** the pattern `patterns/project-chats.md` and its templates.
- **Cost:** included.
- **Path:** light

### Decision log
- **What:** decisions are recorded with date, reasons and who decided, so they're not re-discussed.
- **Alex:** after each board call, decisions go to `Brightloop/decisions.md`.
- **Tools:** part of meeting capture; or dictated.
- **Cost:** included.
- **Path:** light

### Drafts you send yourself
- **What:** replies, updates and reports are drafted with full context; the owner reviews and sends.
- **Alex:** the monthly investor update is drafted from the month's facts; he edits and sends it.
- **Tools:** AI with the project's files; an email connector that creates drafts.
- **Cost:** included.
- **Path:** standard (full if it sends automatically)

### Cold review of important documents
- **What:** before something important goes out, a fresh AI session (or a different model) checks it against a checklist.
- **Alex:** the board pack and the grant application are reviewed for wrong numbers and unclear claims.
- **Tools:** a second AI chat or model with a checklist file.
- **Cost:** included.
- **Path:** light

### Reading queue
- **What:** documents to read or review are collected and sent to the device where you read best.
- **Alex:** contracts to review become PDFs on his tablet each evening.
- **Tools:** a folder + sync to the tablet or e-reader; or email to the e-reader's address.
- **Cost:** free.
- **Path:** light

---

## 3. People

### Meeting capture
- **What:** recorded or dictated meetings become a summary, facts in the right projects, and notes on the people involved.
- **Alex:** after each call, the summary goes to the project and each person's file gets "what we discussed, what I promised".
- **Tools:** meeting recorders that export text (Granola, Fathom, Otter, Read.ai…), or a dictated recap → AI.
- **Cost:** free tiers to ~$15–20/month.
- **Path:** standard

### Personal CRM
- **What:** one file per person, updated from meetings, emails and events: who they are, how you met, what connects you, open promises.
- **Alex:** investors, customers, classmates and the kids' teachers are all people in `People/`.
- **Tools:** AI with file access; email and calendar connectors for automatic updates.
- **Cost:** included.
- **Path:** standard

### Contact list import
- **What:** a one-off import of contacts from an event list, a class roster or a group export into the people table, with duplicates merged.
- **Alex:** imports the 80 attendees of a founders' dinner; only 6 get a full card.
- **Tools:** AI with file access, on demand (pattern: `patterns/contacts-table.md`). No flow needed.
- **Cost:** included.
- **Path:** light

### Follow-up reminders
- **What:** promises made in meetings and emails resurface before they become late.
- **Alex:** "send the deck to Maria" appears in his morning list two days later.
- **Tools:** part of the health check or the morning briefing.
- **Cost:** included.
- **Path:** light

### Before-meeting brief
- **What:** before a meeting, a one-page brief: who they are, history, open topics, what they care about.
- **Alex:** gets a brief 15 minutes before each investor call.
- **Tools:** calendar connector + People files; on demand or scheduled.
- **Cost:** included.
- **Path:** standard

---

## 4. Email and calendar

### What needs you from email
- **What:** each morning, only the emails that need your attention, with why and a suggested reply.
- **Alex:** at 06:00 he gets a list of 5 emails out of 80, with drafts ready for 3.
- **Tools:** AI assistant with an email connector (read-only works); automation platforms for more control.
- **Cost:** included; automation platforms may need a paid tier for daily runs.
- **Path:** standard (reads untrusted content: keep it read-only or add a checkpoint before sending)

### Morning briefing
- **What:** one short page: today's calendar, deadlines, what needs you, follow-ups due.
- **Alex:** reads it with breakfast.
- **Tools:** a scheduled AI task reading calendar, backlog and inbox summary; or a cloud script that sends it as a Telegram message at 07:00 (extends `recipes/telegram-voice-bot.md`).
- **Cost:** included, or a few cents a month via an API.
- **Path:** standard

### Email to calendar and to-dos
- **What:** dates and tasks inside emails become calendar events and to-dos.
- **Alex:** "parents' meeting Thursday 18:00" from the school email lands in the family calendar.
- **Tools:** AI with email + calendar connectors (with confirmation), or an automation platform.
- **Cost:** included or free tier.
- **Path:** standard

### Weekly review
- **What:** once a week, a guided 15-minute review: what happened, what's stuck, what matters next week.
- **Alex:** Sunday evening, the AI prepares the review; he decides the week's three priorities.
- **Tools:** any AI on demand; optionally scheduled preparation.
- **Cost:** included.
- **Path:** light

---

## 5. Study

### ⭐ Course deadlines and weekly study plan
- **What:** all course deadlines in one calendar, and a weekly plan of what to study when.
- **Alex:** his master's Moodle calendar feeds his calendar; every Monday he gets a study plan around his work and family.
- **Tools:** the platform's calendar link (Moodle, Canvas, Brightspace, Blackboard) → calendar subscription → AI weekly plan.
- **Cost:** free; the plan is included.
- **Path:** light (standard if it writes calendar events)

### Course materials to study notes
- **What:** new slides and readings become summaries, key concepts and flashcards.
- **Alex:** each week's readings become a two-page summary and 20 flashcards.
- **Tools:** download materials to the course folder → AI; NotebookLM for audio overviews. For Moodle, technical users can sync all course files automatically with the open-source `moodle-dl` (if the university allows it).
- **Cost:** free or included.
- **Path:** light

### Lecture recordings to notes
- **What:** a recorded lecture becomes a transcript, a summary and the key points, filed in the course folder.
- **Alex:** records the guest lecture on his phone; next morning the summary is in `Study/`.
- **Tools:** the phone's recorder with transcription → a transcription API (Groq, OpenAI; long files may exceed per-request size limits: split or compress) → local Whisper for long or private recordings. Ask the lecturer before recording.
- **Cost:** free to cents per hour.
- **Path:** light

### Exam preparation
- **What:** practice questions and mock exams from your own course material, with weak spots tracked.
- **Alex:** two weeks before exams, daily practice sets from his notes.
- **Tools:** AI with the course folder; study modes of AI assistants.
- **Cost:** included.
- **Path:** light

### Grades and feedback tracker
- **What:** grades and professor feedback in one place, with patterns ("my structure is always criticized").
- **Alex:** after each assignment, the feedback is added to `Study/feedback.md`.
- **Tools:** manual paste or email notifications → AI.
- **Cost:** included.
- **Path:** light

### Class connections
- **What:** classmates, professors and guest speakers become people in the CRM, linked to courses and projects.
- **Alex:** a guest speaker becomes a potential advisor for his startup.
- **Tools:** part of the personal CRM.
- **Cost:** included.
- **Path:** light

---

## 6. Content and newsletter

### Content pipeline
- **What:** interesting items from your work and reading are collected as candidates; you pick; the AI drafts.
- **Alex:** every two weeks, 15 candidates for his newsletter; he picks 5; a draft is ready for editing.
- **Tools:** clipper + notes → AI; newsletter platform for publishing (beehiiv, Substack…).
- **Cost:** free to platform plans.
- **Path:** standard

### Idea bank
- **What:** every idea for posts, talks or products gets a note, linked to related ideas.
- **Alex:** startup ideas, post ideas and talk ideas each have their list.
- **Tools:** voice capture + inbox triage.
- **Cost:** included.
- **Path:** light

### Repurposing
- **What:** one piece of content becomes several (a post, a thread, slides).
- **Alex:** each newsletter becomes a LinkedIn post draft.
- **Tools:** AI with the content folder.
- **Cost:** included.
- **Path:** light (standard if it publishes)

### Events digest
- **What:** local events and opportunities collected from newsletters and sites into a weekly list.
- **Alex:** startup events in his city, filtered by relevance, every Monday.
- **Tools:** email forwarding / RSS → AI.
- **Cost:** free or included.
- **Path:** standard

---

## 7. Money

### ⭐ Monthly spending summary
- **What:** bank transactions become a one-page monthly summary: where money went, subscriptions, unusual items.
- **Alex:** on the 2nd of each month, a summary compares family spending with last month.
- **Tools:** monthly CSV export from the bank → AI; budgeting apps with open-banking sync for automation.
- **Cost:** free (CSV) to a few euros/month (open-banking tools).
- **Path:** standard (sensitive data: decide which services see it)

### Receipts and invoices
- **What:** receipts and invoices from email and photos are collected in one folder with date, amount and category.
- **Alex:** startup expenses for the accountant, household invoices for taxes.
- **Tools:** email forwarding + AI extraction; in Italy, e-invoices downloadable from the tax portal.
- **Cost:** free or included.
- **Path:** standard

### Subscription tracker
- **What:** all recurring payments in one list, with renewal dates and a "do I still use this?" check.
- **Alex:** finds three forgotten subscriptions in the first month.
- **Tools:** part of the monthly summary.
- **Cost:** included.
- **Path:** light

### Bills and deadlines
- **What:** bills, taxes and renewals (insurance, car, ID documents) with due dates in the calendar.
- **Alex:** the car insurance renewal appears a month before.
- **Tools:** email → AI → calendar.
- **Cost:** included.
- **Path:** standard

---

## 8. Health and family

### Health timeline
- **What:** lab results and medical reports (PDFs) become a timeline of key values and visits, per family member.
- **Alex:** cholesterol trend over three years, ready for the doctor.
- **Tools:** download PDFs from the health portal → `Health/<person>/sources/` → AI extracts values.
- **Cost:** included.
- **Path:** standard (sensitive: decide which services see it)

### Kids' health and appointments
- **What:** vaccinations, check-ups and appointments for each child, with reminders.
- **Alex:** Mia's next vaccination appears in the family calendar a week before.
- **Tools:** vaccination booklet photos + appointment emails → AI → calendar.
- **Cost:** included.
- **Path:** standard

### Wearables weekly summary
- **What:** sleep, activity and recovery data become a short weekly note with trends.
- **Alex:** sees that late meetings hurt his sleep.
- **Tools:** export from the phone's health app (Android Health Connect scheduled export; iPhone export apps) → AI.
- **Cost:** free to a few euros.
- **Path:** light

### School to family calendar
- **What:** school emails and announcements become calendar events and to-dos.
- **Alex:** "bring costume Friday" doesn't get missed.
- **Tools:** school emails / platform notifications → AI → calendar (with confirmation).
- **Cost:** included.
- **Path:** standard

### Family logistics
- **What:** a shared weekly view of who does what: pickups, activities, meals.
- **Alex:** Sunday evening, the week's family plan is ready to share with his partner.
- **Tools:** calendar + AI summary; a shared folder or family app.
- **Cost:** included.
- **Path:** light

### Important documents
- **What:** IDs, insurance, contracts and warranties in one place, with expiry dates tracked.
- **Alex:** passport expiry flagged six months before a trip.
- **Tools:** scans in a protected folder + AI index.
- **Cost:** free.
- **Path:** light (mark the folder `protected`)

---

## 9. Job search and career

### Opportunity tracker
- **What:** job or opportunity alerts become a tracked list with status and next step.
- **Alex:** advisory roles and speaking invitations, with follow-ups.
- **Tools:** alert emails → AI → table or files.
- **Cost:** free or included.
- **Path:** standard

### Applications with context
- **What:** each application drafted from your profile, past work and the specific role.
- **Alex:** a grant application draws on the startup's source-of-truth files.
- **Tools:** AI with the brain's files.
- **Cost:** included.
- **Path:** light

### Network warm-up
- **What:** before reaching out, find who in your network connects to a company or person.
- **Alex:** finds two classmates who worked at a target customer.
- **Tools:** People files + AI.
- **Cost:** included.
- **Path:** light

---

## 10. Life admin

### Travel organizer
- **What:** booking emails become one itinerary per trip, with documents and reminders.
- **Alex:** a conference trip with flights, hotel and agenda in one note.
- **Tools:** email forwarding → AI.
- **Cost:** included.
- **Path:** light

### Home and maintenance
- **What:** appliances, repairs, warranties and service contacts, with maintenance reminders.
- **Alex:** the boiler service reminder every autumn.
- **Tools:** a folder + calendar reminders.
- **Cost:** free.
- **Path:** light

### ⭐ Chat with your second brain from your phone
- **What:** ask questions or add notes (voice or text) from a messaging app, even with the computer off.
- **Alex:** sends "add to Brightloop: customer X wants SSO" from his phone.
- **Tools:** the AI assistant's mobile app with access to the brain's cloud folder; a Telegram bot connected to an automation; or a Telegram bot + Google Apps Script + transcription + AI API (recipe: `recipes/telegram-voice-bot.md`).
- **Cost:** free to small API costs.
- **Path:** standard (technical)

---

## 11. Taking care of the system

### ⭐ Always-on agent (technical)
- **What:** an AI agent on a home server or VPS runs the scheduled flows and answers on Telegram, with the brain in a private Git repository shared with the laptop.
- **Example:** (not Alex's setup; community members use Hermes Agent this way) asking "what did I promise Maria?" from the phone at night and getting the answer from `People/`.
- **Tools:** Hermes Agent, or a custom agent (e.g., Mastra); a home machine or a VPS (Hostinger, Hetzner, DigitalOcean…). Recipe: `recipes/always-on-agent.md`.
- **Cost:** server 0–25 €/month plus model usage (from a few € with API keys to 100 €+/month for heavy use).
- **Path:** full

### Health check
- **What:** a daily or weekly report of what the system can't fix by itself.
- **Alex:** "2 inbox items older than a week; meeting-capture didn't run yesterday."
- **Tools:** see `_guide/build-cycle/health-check.md`.
- **Cost:** included.
- **Path:** standard

### Archive with your OK
- **What:** inactive files and projects are proposed for archiving one by one; nothing moves without approval.
- **Alex:** each month, a list of 10 candidates; he approves 8.
- **Tools:** AI with file access.
- **Cost:** included.
- **Path:** light

### Improvement ideas folder
- **What:** ideas and annoyances about the brain itself are collected in one place and reviewed every week or two.
- **Alex:** "note for the brain: the morning summary should start with deadlines" goes to `_system/improve/notes.md`.
- **Tools:** a folder and, optionally, a dedicated chat (pattern: `patterns/improvement-folder.md`).
- **Cost:** included.
- **Path:** light

### Learning promotion
- **What:** lessons that flows learned (in their `memory.md`) are reviewed and, if approved, become rules.
- **Alex:** once a month, 5 proposed lessons; he approves 3.
- **Tools:** AI on demand.
- **Cost:** included.
- **Path:** light
