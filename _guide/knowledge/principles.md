# Principles: what works, what fails, what lasts

Condensed reference, checked in October 2026 (tags: [V] verified on a primary source, [S] secondary source, [U] unconfirmed — anything not [V] must be checked). Facts about tools change: verify specifics at runtime.

Use this file when you need the reasoning behind a recommendation. Translate it into advice for the owner; don't recite it.

---

## 1. What to borrow from the classic methods

The methods solve different problems. PARA, GTD and Johnny.Decimal organize **action and files**; Zettelkasten and evergreen notes develop **ideas**; LYT/ACE tries to cover both. Borrow pieces, don't adopt a whole religion.

**PARA / Building a Second Brain (Tiago Forte)**
- Sort by *actionability*, not subject: Projects (short efforts with a goal), Areas (ongoing responsibilities), Resources (topics of interest), Archives (inactive items).
- CODE pipeline: Capture → Organize → Distill → Express. "Express" is the point: notes exist to make something.
- Progressive summarization: highlight, then bold, then an executive summary, done *only when a note is revisited* ("opportunistic compression").
- Governing rule: "Your system has to give you time, not take time."
- Since 2023 Forte frames PARA as "pre-assembled bundles of context" for AI agents. He prefers filing by hand (AI auto-filing loses the reminder value), which is his opinion, not a study. Practical takeaway: the AI proposes a location, the owner confirms.
- Fits: project-heavy people; project folders as AI context.

**Zettelkasten / evergreen notes (zettelkasten.de, Andy Matuschak)**
- Atomic notes in your own words, each with a unique ID; links say *why* they exist. "Connecting, not collecting."
- Evergreen notes are concept-oriented and densely linked; the goal is "better thinking", not better note-taking.
- Fits: writers, researchers, students building understanding. Optional layer, rarely a first step.

**GTD (David Allen)**
- Pipeline: capture, clarify, organize, reflect, engage.
- Weekly Review in three phases: Get Clear, Get Current, Get Creative.
- Allen: "Any time, any frequency, is better than not at all." A backlog of missed reviews can make people quit.
- Fits: anyone with many open loops. The AI can prepare Clear/Current; the owner does Creative.

**Johnny.Decimal**
- At most 10 areas × 10 categories × 100 IDs, addressed as `AC.ID` (e.g., `15.22`): every item has a short address you can say aloud.
- Fits: admin-heavy lives, shared vocabularies with a partner or team. Rigid; offer it, don't push it.

**LYT / ACE (Nick Milo)**
- Atlas (knowledge), Calendar (time), Efforts (action); Maps of Content as hubs.
- Key line: "structure must be earned". Add structure when a pattern repeats.
- Fits: people who want a journal/daily dimension next to projects.

**Digital gardens (Maggie Appleton)**
- Public, evolving notes, published in an unfinished state. A second brain is private and utilitarian; a garden is a possible *output*.
- Fits: people who want to think in public. Keep it a separate, deliberate flow (it publishes outside).

---

## 2. Why second brains fail

Behaviour, not tools. None of these is measured with rigorous adoption data; they are well-described patterns.

| Failure | What it looks like | What helps |
|---|---|---|
| Collector's fallacy (Tietze, 2014) | "To collect is a reward in itself"; "kept isn't read" | Time-boxed capture, then process what was collected |
| Overbuilding up front | Perfect taxonomy, 25 commands, nothing used | Start with one loop; add structure when a need repeats |
| Costly capture | Every note needs a title, tags, a folder | Capture into one inbox with no required metadata |
| Outsourcing thinking | AI summarizes everything; the owner stops thinking | AI files and drafts; the owner decides meaning and keeps writing |
| Write-only notes | Notes are saved and never reopened | Every review asks "what will you make with this?" |
| Tool-hopping | Rebuilding in a new app every few months | Plain files as the source of truth; apps are viewers |

Practitioner signals (not studies): a writer deleted about 10,000 notes in 2025 because the system "began to replace" her thinking; one builder's sixth attempt survived only after he cut 25 commands to 4 and let AI do the filing he never kept up. The popular "under 20% of notes reopened" heuristic is unsourced (unconfirmed).

---

## 3. What the peer-reviewed evidence says

| Study | Finding | Design implication |
|---|---|---|
| Bergman et al., JASIST 2010 (296 people, 1,131 retrievals) | Active files at median depth 3; 82% within 4 levels. Each extra level ≈2.24 s, each extra item ≈0.11 s; authors suggest up to **≈21 items per folder**. People navigate more than they search. | Shallow folders, ~20 items before splitting |
| Whittaker et al., CHI 2011 (345 users, 85,000+ refinding actions) | Filing email into folders in advance does **not** improve refinding; search and threads work better | Don't make the owner file email; let search do it |
| Epstein et al., CHI 2016 (193 former self-trackers) | **Cost of collecting data** was the top reason for quitting; recommend easy re-entry and "happy abandonment" without guilt | Cheap capture; a guilt-free way back after a break |
| Lally et al., 2009 (UCL) | Automaticity took a **median of 66 days** (with wide variation); missing one opportunity did not significantly derail the habit | Missed reviews are normal; judge the system after ~2 months, not 2 weeks |
| Risko & Gilbert, 2016 | Cognitive offloading is a normal, metacognitively driven behaviour | A second brain is not a crutch by definition |

Limits: Epstein studies self-tracking, an analogue of note-taking, not note apps directly. No peer-reviewed study shows that weekly reviews make a system last, explains why specific note apps are abandoned, or compares atomic notes with long documents for AI retrieval. The "capture in under 5 seconds" threshold is lore (unconfirmed).

---

## 4. What makes a second brain last

- **Shallow structure.** About 3 levels, about 20 items per folder; split when it grows, not before.
- **Cheap capture.** One inbox, any format, no required fields. Metadata is added later, by the AI, during processing.
- **AI files, the human decides meaning.** The AI sorts, links, summarizes and drafts; the owner decides what matters, where it belongs and what to keep. Pattern: propose → owner confirms → write.
- **Review at any frequency.** A 10-minute weekly review is a good default; monthly is fine; a missed one is fine.
- **Easy return after a break.** Offer a "welcome back" pass: what changed, what is stale, reset the inbox, no guilt.
- **"What will you make with this?"** End reviews with this question so notes turn into decisions, drafts and outputs.
- **Plain files as the source of truth.** Markdown in a folder the owner already uses survives tool changes.
- **One flow at a time.** Use each new flow for 1–2 weeks before adding the next.

---

## 5. Lessons from a founder's system

A real, AI-run second brain built by a startup founder over several months. Practitioner evidence: one person's setup, shared to illustrate patterns, not a standard. Most of these ideas are already defaults in this kit.

**Where it lives**
- His everyday working folder (Documents) **is** the brain. No separate vault to remember to open.
- Each project folder is self-contained: `source-of-truth/` (canonical facts), `Deliverables/` (what goes out), a protected do-not-touch folder, and its own git, sync and health check.
- A personal CRM where investors are people: one file per person, not rows in a deal table.

**How it is described**
- Places are boxes, flows are arrows. Every arrow carries four labels: **what** moves, **when**, **who** (which model or tool), and the **checkpoint**.
- Many flows overall, grown over months, one at a time. It did not start big.

**How it runs**
- Routines run before he wakes, e.g., 05:30 inbox triage, 05:45 health check, 06:00 email capture. He starts the day reviewing results, not doing the sorting.
- Sources such as email are **read-only**: flows read and extract; they never change the original.
- Live co-edited spreadsheets stay in their cloud app; flows **read** them, never copy them into the brain (copies go stale).
- Drafts are prepared; **he sends them**.
- A separate "cold reviewer" model, in a fresh context, checks high-stakes documents before they go out.

**Rules that keep it trustworthy**
- Facts carry their source (where and when).
- Nothing gets deleted; no duplicate canonical files.
- Indexes are updated when a session closes.
- Items that need him ("Next (you)") go to a backlog instead of being guessed.
- Archiving happens file by file, with his OK, and each archived file gets a provenance label (where it came from, when, why).
- Paused sources stay on the map, marked paused, so nothing silently disappears.

**The map**
- Live: each place shows file counts, last change and what is new since the last review.
- Hovering a node shows only that node's flows, so a large map stays readable.

**Cost**
- Heavy usage once cost about €1,000 in one month of API usage. Costs grow with the number of flows, how often they run and which models they use. A few light flows can stay close to free. Show the owner the cost direction before building.

**What to take from it:** start where the owner already works; keep originals read-only; draft, don't send; write facts with sources; never delete or duplicate; grow one arrow at a time.

---

## 6. Example (only if it helps)

Alex (founder of Brightloop, part-time master's student on Moodle, father of Leo and Mia) captures a voice note after an investor call. Capture costs nothing: it lands in `Inbox/`. The morning triage files the figures into `Brightloop/source-of-truth/` with "(source: voice note, 2026-10-21)", updates the investor's file in `People/`, and puts "Reply to Sara about the data room: Next (you)" in the backlog with a draft ready. Alex decides and sends.

---

## Sources

- Forte, PARA: https://fortelabs.com/blog/para/
- Forte, Progressive Summarization: https://fortelabs.com/blog/progressive-summarization-a-practical-technique-for-designing-discoverable-notes/
- Forte, Why PARA is the key to the AI era: https://fortelabs.com/blog/why-para-is-the-key-to-the-ai-era/
- Zettelkasten introduction: https://zettelkasten.de/introduction/
- Tietze, Collector's Fallacy: https://zettelkasten.de/posts/collectors-fallacy/
- Matuschak, Evergreen notes: https://notes.andymatuschak.org/Evergreen_notes
- GTD Weekly Review: https://gettingthingsdone.com/2009/05/the-gtd-weekly-review/
- Johnny.Decimal: https://johnnydecimal.com/10-19-concepts/11-core/11.01-introduction/
- LYT ACE: https://blog.linkingyourthinking.com/notes/ace-folder-framework
- Appleton, digital gardens: https://maggieappleton.com/garden-history
- Bergman et al. 2010: https://www.tau.ac.il/education/muse/publications/101.pdf
- Whittaker et al. 2011: https://research.ibm.com/publications/am-i-wasting-my-time-organizing-email-a-study-of-email-refinding
- Epstein et al. 2016: https://pmc.ncbi.nlm.nih.gov/articles/PMC5428074
- Lally et al. (UCL): https://www.ucl.ac.uk/news/2009/aug/how-long-does-it-take-form-habit
- Risko & Gilbert 2016: https://discovery.ucl.ac.uk/id/eprint/1508770/
- Westenberg via Kottke: https://kottke.org/25/07/0047083-i-deleted-my-second-brain
- Sixth-attempt second brain: https://dev.to/huy_tieu/i-finally-built-a-second-brain-that-i-actually-use-6th-attempt-4075
- Founder's system: private practitioner account (not published).
