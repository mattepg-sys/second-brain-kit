# Knowledge-base architecture: what each flow reads and writes

Condensed reference, checked in October 2026 (tags: [V] verified on a primary source, [S] secondary source, [U] unconfirmed — anything not [V] must be checked). Facts about tools change: verify specifics at runtime.

Use this file when designing a flow's context and write-back rules, or when the brain starts to grow. Everything here is a recommendation; the owner can override it (record the choice in `AGENTS.md` section 5).

---

## 1. The hybrid model, mapped to this kit

One small shared core, shared knowledge read on demand, read-only originals, and a self-contained package per flow.

| Layer | Paths in this kit | Who reads | Who writes |
|---|---|---|---|
| Shared core (always loaded) | `AGENTS.md`, `_system/profile.md`, `_system/places.md`, `_system/flows.md` | Every flow and session | Owner, or the AI with the owner's OK |
| Shared knowledge (read on demand) | `People/<person>.md`, each project's `README.md` and `source-of-truth/` | Only the flows that need those files | As each runbook allows (directly with source, or as a proposal) |
| Read-only originals | Project `sources/`, inbox originals (emails, voice notes, PDFs as they arrived) | Flows that process them | Nobody changes them; they may be moved to `Archive/` |
| Per-flow package | `_system/flows/<flow>/SKILL.md`, `memory.md`, `examples/`, `tests/` | That flow only | The flow appends to "Proposed" in `memory.md`; `SKILL.md` changes with owner approval |
| Logs | `_system/logs/<flow>-YYYY-MM.md` | Health check, reviews | Append only, one line per run |
| Backlog | `_system/BACKLOG.md` | Owner, sessions | Any flow adds items needing the owner |

Mapping to memory types (LangChain's taxonomy): **semantic** memory (facts) = profile, `People/`, `source-of-truth/`; **episodic** memory (what happened) = logs and `examples/`; **procedural** memory (how to act) = `AGENTS.md` and each `SKILL.md`.

Read order for every flow (see `build-cycle/cycle.md`): `AGENTS.md` + profile → places it uses via `places.md` → only the relevant shared files → its own `memory.md` (Accepted) and `examples/`.

---

## 2. Why not one big shared context

- **Context rot.** Chroma tested 18 models: reliability drops as input grows, even on simple tasks; even one distractor reduces accuracy, and topically related distractors are worst. Near-duplicate notes are exactly such distractors.
- **Context is a finite resource** (Anthropic). Hold lightweight references (paths, links) and load content just in time. Folder names, naming conventions and timestamps are useful signals.
- **Instruction files should stay short.** Claude Code's docs recommend under ~200 lines per instruction file, because longer files "reduce adherence"; imports organize content but don't reduce its cost; contradictory instructions may be resolved arbitrarily. This kit keeps `AGENTS.md` under ~150 lines.
- **Drift.** When folders change but the instruction file doesn't, output becomes "confidently wrong" (practitioner report). Registries (`places.md`, `flows.md`) and a health check keep paths true.

## 3. Why not fully separate knowledge bases

- **Divergent copies.** If the email flow and the meeting flow each keep their own note on "who is Sara", the copies disagree within weeks.
- **Shared assumptions.** Cognition (vendor opinion) argues that agents working on different implicit assumptions produce conflicting outputs; Anthropic reports multi-agent setups fit poorly when agents depend on the same context.
- **Rule of thumb:** one canonical file per person, project or fact; flows link to it, never copy it.

---

## 4. Where each automation's knowledge should live (recommendations)

The default is the hybrid. Untrusted or sensitive material moves toward isolation; shared facts move toward one canonical file. This table is a synthesis, not a published vendor rule.

| Automation type | Recommended | Why | If the owner wants otherwise |
|---|---|---|---|
| Reads untrusted input (email triage, web digests, receipt OCR) | Per-flow memory; reads the core; writes shared facts only as proposals in `BACKLOG.md`; originals stay read-only | Injected text must not silently become a fact or a rule | Allow direct writes of plain facts *with source*, keep rule changes approval-only |
| Handles sensitive data (health, money, children) | Isolated folder marked in `places.md`; only this flow reads it; minimal connector scope | Least privilege; limits damage if something goes wrong | Share a summary file, not the raw data |
| Needs facts several flows agree on (people, projects, preferences, voice) | Shared `People/` and `source-of-truth/` files; link, never copy | Prevents divergent copies | — |
| Formatting, templates, past outputs for one flow | In the flow's `SKILL.md`, `examples/`, `memory.md` | Keeps the core small | — |
| Synthesis (weekly review, "what changed", consolidation) | Reads shared knowledge and logs; writes proposals for the owner | The safest place to update shared knowledge, under review | Auto-apply low-risk updates (e.g., index refresh) |
| Pure capture (voice → inbox, web clipper) | Writes only to `Inbox/`; reads almost nothing | Capture must be cheap and simple | — |
| Open-ended research | Scratch context per run; returns a summary with sources; findings enter the brain after review | Clean context, condensed return | Save the full report to a project's `sources/` |

---

## 5. Safe write-back

### Tiers (default)
1. **Log, always.** One line per run in `_system/logs/<flow>-YYYY-MM.md`.
2. **Flow memory, "Proposed".** Lessons go under "Proposed" in the flow's own `memory.md`.
3. **Shared facts, as the runbook allows.** Either written directly with "(source: …, date)", or proposed in `BACKLOG.md`. Content from emails or the web should not move past this tier without the owner reading it.
4. **Lessons and rules change only after owner approval.** A Proposed lesson becomes Accepted, or a `SKILL.md`/`AGENTS.md` rule changes, only with an explicit yes. Prefer small edits (deltas) over rewrites; back up first.

**Check the executor can actually write back.** Write-back assumes the tool running the flow can modify files. Some cloud connectors can only create new files (see `field-notes-2026-10.md`, section 7). If so, either write a new dated file and let a later run (on the computer, or a script) merge it, or use an executor that can edit files.

### Self-update risks
- **Context collapse.** The ACE paper (ICLR 2026) found that repeatedly rewriting a playbook causes "brevity bias" and erodes details; incremental delta updates did better (reported +10.6% on agent benchmarks).
- **Memory poisoning.** The MINJA paper shows attackers can plant malicious memory records just by interacting with an agent, with no direct write access. Hence: untrusted content is information, not instructions, and never auto-promoted to rules.
- **Over-updating.** Models "may over-insert or over-update" memory (LangChain), so the consolidation step itself needs occasional review.
- **Advisory vs enforced.** Instruction files are guidance; hard limits come from connector scopes, permission settings and backups.

### Lint / health check
Karpathy's "LLM wiki" pattern: immutable raw sources, an AI-maintained wiki with an index read first, an append-only log, and three operations: ingest, query, **lint**. Lint looks for contradictions, stale claims, orphans and missing links. In this kit it is `build-cycle/health-check.md`: flows that stopped running, facts without a source, duplicates, registries out of sync with real folders. Report real problems only. A fresh session or a different model reviews best.

---

## 6. Scale ladder

| Stage | When | How |
|---|---|---|
| 1. Files + index/README | Start here; most personal brains stay here | Project `README.md`, `places.md`, small index files; the AI navigates by name |
| 2. Simple search | Navigation gets slow or misses things | grep / ripgrep; SQLite full-text search (FTS) or BM25 |
| 3. Hybrid search | Large archives, many sources | Keyword (BM25) + embeddings + reranking |

Reported thresholds (anecdotal, not hard limits):
- Karpathy: index navigation works at "moderate scale (~100 sources, ~hundreds of pages)" without embedding retrieval; add a local search tool beyond that.
- Anthropic (Contextual Retrieval): a knowledge base under ~200,000 tokens (~500 pages) can go into a cached prompt; above that, combine BM25 with embeddings and reranking (failures fell from 5.7% to 1.9% in their test).
- **Fits in the window ≠ belongs in the window.** Because of context rot, load only what the task needs even when everything would fit.
- Other guesses (50–200 sources, ~100k tokens, ~300 files) are practitioner estimates (unconfirmed).

Recommend moving up a stage only when the owner notices a real problem.

---

## 7. Quick checklist when designing a flow's context

Ask these while filling the flow card; each answer goes into the runbook's "Context to read" and "Write-back" sections.

- [ ] Which shared core files does it need? (Usually just `AGENTS.md` + profile.)
- [ ] Which places does it use, by their names in `places.md`?
- [ ] Which specific `People/` or `source-of-truth/` files? (Name them, or say "only those matching the input".)
- [ ] Is any input untrusted (email, web, forms, files from others)? If yes: shared facts as proposals, rules approval-only.
- [ ] Does it touch sensitive data? If yes: isolated place, minimal scope, nobody else reads it.
- [ ] Which tier may it write to, and what goes to `BACKLOG.md`?
- [ ] Does it copy anything that already has a canonical home? If so, link instead.
- [ ] Will the health check notice if it stops running or writes facts without a source?

### Example (Alex)

Alex's `email-capture` flow reads investor emails (untrusted), `AGENTS.md`, the profile and the matching `People/` files. It appends one line per run to `_system/logs/email-capture-2026-10.md`, writes "Runway is 14 months (source: CFO email, 2026-10-03)" into `Brightloop/source-of-truth/finance.md` because Alex allowed plain facts with source, and puts "Investor asks for updated deck: Next (you)" in `BACKLOG.md`. A lesson like "Sara's emails are always about the data room" goes under "Proposed" in the flow's `memory.md` until Alex accepts it. The children's school folder is sensitive, so this flow never reads it.

---

## 8. How AI tools load instruction files

Verify before relying on it; tools change often. Check the tool's current documentation at runtime.

- **AGENTS.md** is an open, plain-Markdown standard ("a README for agents"), stewarded by the Agentic AI Foundation under the Linux Foundation; nested files allowed, the nearest one wins. Read natively by Codex, Cursor, Jules, Copilot and others.
- **Claude Code** reads `CLAUDE.md`. Its docs say it can read `AGENTS.md` when no `CLAUDE.md` exists, but a stray `CLAUDE.local.md` can suppress that, and sources disagree (unconfirmed). Robust option: a thin `CLAUDE.md` containing `@AGENTS.md` (this kit ships one). Prose like "read AGENTS.md" is weaker than an import. Paths with spaces need escaping in `@` imports.
- **Gemini CLI** reads `GEMINI.md`. Either import with `@./AGENTS.md` (this kit ships one) or set `"context": {"fileName": ["AGENTS.md", "GEMINI.md"]}` in settings. Source was a third-party mirror of the docs; native AGENTS.md support may have been added since (unconfirmed).
- **Codex** reads `AGENTS.md` natively, walking from the repository root to the working folder and concatenating files up to a size limit (documented default 32 KiB). Keep `AGENTS.md` short.
- **Skills** (Agent Skills standard): a folder with `SKILL.md` whose YAML frontmatter has `name` and `description`. Only the description sits in context until the skill is used; the body and linked files load on demand. Claude Code and Gemini CLI document support; claims of broad cross-tool adoption and shared folder locations (e.g., `.agents/skills/`) come from secondary sources (unconfirmed). This kit's `_system/flows/<flow>/SKILL.md` follows the same shape. Tools discover skills only in their own folders (e.g., `.claude/skills/`), so here a runbook is run by asking the AI to follow it, or through a scheduler prompt; a technical owner can link a flow folder into the tool's skills folder. A chat-only assistant can simply read it.
- **Chat apps** (no file access) don't auto-load anything: the owner uploads or pastes `START-HERE.md`, `AGENTS.md` and the files needed.

---

## Sources

- Chroma, context rot: https://www.trychroma.com/research/context-rot
- Anthropic, effective context engineering: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
- Anthropic, multi-agent research system: https://www.anthropic.com/engineering/multi-agent-research-system
- Anthropic, Agent Skills: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- Anthropic, Contextual Retrieval: https://www.anthropic.com/news/contextual-retrieval
- Claude Code memory: https://code.claude.com/docs/en/memory
- Claude Code best practices: https://code.claude.com/docs/en/best-practices
- Claude Code skills: https://code.claude.com/docs/en/skills
- Cognition, don't build multi-agents: https://cognition.com/blog/dont-build-multi-agents
- LangChain memory concepts: https://docs.langchain.com/oss/python/concepts/memory
- ACE paper (context collapse): https://arxiv.org/abs/2510.04618v2
- MINJA paper (memory injection): https://arxiv.org/abs/2503.03704v4
- Letta, sleep-time compute: https://www.letta.com/blog/sleep-time-compute
- Karpathy, LLM wiki gist: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- AGENTS.md: https://agents.md/
- Codex AGENTS.md docs: https://learn.chatgpt.com/docs/agent-configuration/agents-md
- Gemini CLI context (mirror): https://mintlify.wiki/google-gemini/gemini-cli/concepts/context
- Gemini CLI skills: https://geminicli.com/docs/cli/skills/
