# Light path

For simple, low-risk flows that stay inside the brain (e.g., voice note → text in the inbox, a weekly summary for yourself, sorting files on request). Usually one session.

Phases are numbered as in `path-full.md` so you can always switch to a heavier path.

---

### 1. Define "done"
Agree in one sentence what a good result looks like. Fill in the short version of the flow card: name, one sentence, the four labels, from/to places.

### 3. Do it by hand once
Run the task manually in the conversation with 2–3 real examples from the person's material. Show the result. Ask: "Is this what you want? What would you change?" Adjust until they say yes. This is the most valuable phase: it reveals what the person really wants.

### 4. Write the runbook
Save the short flow card as `_system/flows/<flow-name>/card.md`. Create `_system/flows/<flow-name>/SKILL.md` from `_guide/templates/flow-skill.md`, with the rules and the example you just agreed on. Keep it short. Create `memory.md` from `_guide/templates/flow-memory.md`.

### 5. Choose how it runs
Recommend the simplest option that works, and explain the alternatives in one line each:
1. **On demand:** the person says "run <flow-name>" to their AI (free, nothing to set up);
2. **Scheduled by their AI assistant**, if it supports scheduled or recurring tasks;
3. **An automation tool** (Zapier, Make, n8n, Power Automate…) or a small script, if needed.
Set it up together. Explain where it runs (computer on, or cloud) if it's scheduled. For a scheduled run, paste the **scheduler prompt** from the runbook (section "Scheduler prompt" of `_guide/templates/flow-skill.md`) into the scheduled task: every scheduled run starts with no memory of this conversation.

### 7. First real run
Run it once for real. Check the output with the person. Fix the runbook if needed.

### 13. Log
Each run appends one line to `_system/logs/<flow-name>-YYYY-MM.md`.

### Register
Follow `cycle.md`, section 5.

### 15. Keep, simplify or stop (after 1–2 weeks)
Add a reminder in `_system/BACKLOG.md`: "Review <flow-name>: is it used? Is it useful?" When reviewed, the person decides: keep, simplify, change, pause or retire it.
