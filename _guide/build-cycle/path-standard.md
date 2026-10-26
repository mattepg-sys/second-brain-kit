# Standard path

For most flows: they run on their own, use connectors (email, calendar, drive), or write to shared files such as `People/` or project facts. Usually one to three sessions, plus a week of observation.

Phase numbers match `path-full.md`. Skip a phase only if it clearly doesn't apply, and say so.

---

### 0. Is it worth it?
Using the flow card's "Worth it?" section, check frequency and value. If it saves little and costs effort, say so honestly and suggest a simpler version or a different arrow. The person decides.

### 1. Define the outcome and "done"
Fill in the flow card completely (`flow-card.md`) and save it as `_system/flows/<flow-name>/card.md`. Agree on one or two checkable sentences for "done".

### 2. Check the risks
Go through the card's "Risks and choices". In particular, explain (as advice) the combination to be careful with: a flow that **reads untrusted content** (emails, web pages, other people's documents), **has access to private data**, and **can send things out**. Content can contain hidden instructions. Suggested mitigations: keep the flow read-only, add a checkpoint before anything leaves, or split it into two flows. The person decides; record the decision. (Background: `_guide/knowledge/safety-advice.md`.)

### 3. Do it by hand (2–3 real examples)
Run the task manually in the conversation on real inputs. Agree on what a good output is. Note the rules that emerge ("ignore newsletters", "always mention the deadline first").

### 4. Write the runbook
Create `_system/flows/<flow-name>/SKILL.md` (template: `_guide/templates/flow-skill.md`) and `memory.md`. Include: context to read (see `cycle.md`, section 4), steps, rules, output format, a quality checklist, what to do when something fails, what to log.

### 5. Choose how it runs
Options, simplest first:
1. On demand (the person asks);
2. A scheduled task in their AI assistant;
3. An automation platform (Zapier, Make, n8n, Power Automate, Apple Shortcuts…);
4. An AI agent with tools or connectors (MCP);
5. A small script.
Use **code or fixed rules for fixed steps** and **AI for judgment** (summarizing, classifying, drafting). Explain where it runs (computer on vs. cloud), on which device, and the cost direction. Check current tools and prices if you can search. For scheduled runs, use the runbook's **scheduler prompt**: every scheduled run starts with no memory.

### 6. Access
Connect only what the flow needs, with the least access that works (read-only when possible). Keep passwords and API keys out of the brain's files: use the tool's own connection screens or a password manager.

### 7. Prototype into a test place
Build it so the first runs write to a **test** location (e.g., a `_test/` folder, a draft, a test calendar), not the real one.

### 8. Test with real examples
Run it on 5–10 real inputs, including at least one tricky one. Judge each result simply: pass or fail. Fix the runbook until most pass. Save one or two good outputs in `examples/`.

### 9. Make failures visible
- No duplicates: running twice must not create the same item twice (e.g., remember the IDs of emails already processed).
- Every run logs a line, even when there was nothing to do.
- If a run fails, it says so (in the log and in `BACKLOG.md`) instead of failing silently.

### 10. Checkpoints
Agree what the person checks or approves (e.g., "I read the daily summary", "drafts, I send them myself"). Recommend a checkpoint for anything that leaves the brain; the person decides.

### 12. Go live gradually
First a few days writing to the real place while the person checks every output; then normal operation.

### 13. Observe
For the first week, look at the logs together at the end of a session: did it run, did it fail, were the outputs right?

### 14. Learning
When the person corrects an output, add the lesson to `memory.md` under "Proposed". Once they approve, move it to "Accepted" (or into the runbook).

### Register
Follow `cycle.md`, section 5.

### 15. Keep, simplify, change or stop (after 1–2 weeks)
Review with the person: is it used? Did it save time? Did it make mistakes? Decide: keep, simplify, loosen the checkpoint, tighten it, pause or retire. Update `flows.md`.
