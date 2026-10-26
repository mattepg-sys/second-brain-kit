# Tools and costs: automation, MCP, storage, note apps, capture

Prices and features as checked on 2026-10-24. They change often: verify current details at runtime (web search) before recommending.

How to use this file: consult it when choosing the "Who" of a flow or explaining cost direction. Do not read it to the person. Prices are USD unless marked. Labels: **[V]** = vendor's own page; **[S]** = secondary source only; **[U]** = unconfirmed or conflicting. AI assistant plans are in `ai-assistants-2026-10.md`.

---

## 1. Automation platforms

The **billing unit** drives cost more than the sticker price: per-step platforms charge a 6-step flow ~6 units per run; per-run or per-execution platforms charge 1.

| Platform | Free tier | Entry paid | Billing unit | Human approval step | Difficulty |
|---|---|---|---|---|---|
| **Zapier** | 100 tasks/mo, **2-step Zaps only**, 15-min polling | Professional from $19.99/mo (multi-step); Team from $69 | Per action (task); triggers, filters, formatter, Tables don't count | Request Approval / Collect Data: **paid only**, self-only on Professional; can edit before send [V] | Easy |
| **Make** | 1,000 credits/mo, 2 active scenarios, 15-min schedule [S for scenarios] | Core ~$9/mo annual ($10.59 monthly) [S] | Per module action (credit) | No first-party module documented; use "draft, then wait" [U] | Medium |
| **n8n cloud** | Trial: 1,000 executions, no card | Starter €20/mo annual (2.5K executions); Pro €50 (10K) | Per execution (any number of steps) | Human review per AI tool call, via Slack, Telegram, Gmail, Teams… [V] | Medium–technical |
| **n8n self-hosted** | Community Edition, no execution caps | Your server cost (~$5–10/mo VPS, unsourced) | — | Same as cloud | Technical. License terms unconfirmed |
| **Activepieces** | **1,000 credits per day**, unlimited flows | Plus $20/mo (10K credits) | **Per run** + AI step cost (2 fast / 10 smart / 20 frontier; 1 with own key on Plus+) | Not stated in sources | Easy–medium; self-hostable |
| **Power Automate** (in Microsoft 365) | Included with M365 licenses: standard connectors only, 6,000 actions/user/day | Premium (price unconfirmed; historically ~$15/user) | Per action | "Approvals" is a standard M365 feature [U, not verified] | Medium. HTTP and most LLM connectors are premium [U] |
| **Power Automate desktop** | Included with Windows: local desktop flows, no cloud connectors | — | — | — | Medium |
| **Google Apps Script** | Free with quotas: consumer accounts 100 email recipients/day, 90 min trigger runtime/day, 6 min per run | — | Quota | Build your own (e.g., create Gmail drafts) | Technical (JavaScript); AI can write it |
| **IFTTT** | 2 Applets, unlimited runs | Pro $2.99/mo; Pro+ $8.99 (AI services) | Per Applet | No | Very easy, limited |
| **Relay.app** | Free, "all features", quota not stated | Professional $9/mo (10K steps) | Per step; polling free | **Approval steps on all plans**; each approver needs a seat [V] | Easy |
| **Lindy** (AI agent builder) | $50 credits for 7 days, one-time | Team $49.99/mo (page also says "from $29.99" [U]) | Credits per task (2–250 everyday) | **Outside-impact actions wait for approval by default** [V] | Easy |
| **Pipedream** | **Development only** (no production) | Startup $99/mo annual | 1 credit per 30 s compute | — | Developer tool |

Also free on Apple devices: **Shortcuts** (incl. Apple Intelligence actions) [U, not verified].

Advice: simplest first. For many people the assistant's own scheduled tasks (see the other file) replace a platform entirely. Add a platform when a flow needs an event trigger ("when an email arrives"), retries, or app-to-app moves. Default pattern for anything outbound: **create a draft, the person presses send**.

---

## 2. MCP in practice

- **What it is:** Model Context Protocol, an open standard ("USB-C for AI apps") that lets an AI app use tools and data (calendar, Notion, files). Supported by Claude, ChatGPT, Mistral, Gemini Spark, VS Code, Cursor and others.
- **Official vs community:** the official reference repo now keeps only a few servers (Filesystem, Fetch, Git, Memory, Time, …). Google Drive, Slack, SQLite, PostgreSQL, GitHub reference servers were **archived**. Vendors now host their own: Notion MCP (remote, OAuth, read/write), GitHub MCP (remote or local, `--read-only` flag). Google's own Workspace MCP servers (Gmail, Drive, Calendar…) are in Developer Preview, need a Cloud project; consumer @gmail.com support unclear [V/U]. Browse published servers at the MCP Registry (registry.modelcontextprotocol.io). Obsidian MCP servers are community-only [U].
- **Remote/OAuth vs local:** remote servers (a URL + sign-in) are easiest and work in web apps and cloud scheduled tasks. Local (stdio) servers run code on your computer with your permissions, work only in desktop apps, and carry the biggest risk.
- **Universal bridges** (one connector → thousands of apps):

| Bridge | Free | Paid | Note |
|---|---|---|---|
| Zapier MCP | Uses plan tasks: **2 tasks per tool call** (Free 100 tasks ≈ 50 calls/mo) | Professional, Team | Auth built in; failed calls free [S for details] |
| Composio | Hobby: 100K tool calls + 50K triggers/mo | Pro $29/mo | [V] |
| Pipedream Connect | Development only | From $99/mo | Developer-oriented |
| Activepieces MCP | All plans incl. Free | — | [V] |

- **Security advice** (suggest, explain why):
  - Prefer the assistant's built-in connector directory or the vendor's own hosted server; avoid random community local servers.
  - Grant the minimum: read-only where offered; a Filesystem server only on the brain's folder, never the home folder.
  - Text inside emails and web pages can contain instructions (prompt injection). Keep write tools (send, share, delete) behind a human approval step. A hub widens what one token can do.
  - Claude notes that Advanced Research can call connector tools without asking: disable write tools for it [V].
  - Revoke tokens when a flow is retired.

---

## 3. Databases and structured stores

Advice: use the store the person's tools already speak; keep knowledge in Markdown and only records (tasks, contacts, expenses) in a table.

| Store | Free limits | Paid entry | Lock-in / export | AI-friendliness |
|---|---|---|---|---|
| **Plain CSV / Markdown files** | Free, unlimited | — | None; most portable | Any agent with folder access reads them directly |
| **Google Sheets** | Free (limits not fetched [U]) | Workspace | CSV/XLSX export | Native in every automation platform and most assistants |
| **Excel / Microsoft Lists** | With M365 | — | CSV/XLSX | Power Automate standard connectors |
| **Notion** | Free, unlimited blocks for individuals; 5 MB uploads | Plus $10/member; Business $20 (needed for Notion Agent) | Pages → Markdown, databases → CSV; **exports can't be re-imported**; relations lost [U] | Hosted Notion MCP (read/write); native in all platforms. Notion AI only a trial on Free/Plus |
| **Airtable** | 1,000 records/base, **100 automation runs and 1,000 API calls/mo** | Team $20/collaborator annual | CSV | Good API; one polling automation can exhaust Free |
| **Baserow** | 3,000 rows, 2 GB | Premium $10/user annual | Self-hostable | Lists an MCP server |
| **NocoDB** | Cloud: 1,000 records, 100 runs, 1,000 API calls/mo | Plus $12/seat | Self-hosted Community: unlimited records (2 workflows/base) | REST API |
| **Supabase** (Postgres) | 500 MB DB, 2 projects; **pauses after 1 week of inactivity** | Pro from $25/mo | Standard Postgres | SQL; technical users |
| **Zapier Tables** | 2,500 records; doesn't use tasks | Professional 100K records | Zapier-bound | Easy inside Zapier |
| **Make data stores** | 1 store, 1 MB | — | Make-bound | Only inside Make |

---

## 4. Note apps over plain files, and sync gotchas

| App | Status / price | Plain files? |
|---|---|---|
| **Obsidian** | App free, including work use (commercial license optional, $50/user/yr). **Sync** $4/mo annual ($5 monthly), E2E encrypted, version history. **Publish** $8/site/mo annual ($10 monthly). Official **CLI** since early 2026 (desktop 1.12 line): needs the Obsidian app running, so poor for headless agents | Yes: the vault is a folder of .md files; agents can edit them without Obsidian |
| **Logseq** | Split in April 2026: **Logseq OG** (Markdown files) gets security fixes only; main app is database-based with a **read-only** Markdown mirror | OG yes; new app no. Not advised for a new file-first brain |
| **Notion** | See section 3 | No; exports lose data, workspace export can take up to 30 h |
| **VS Code / Cursor, Markor (Android, no built-in sync), iA Writer** | Free / various | Yes |
| **Capacities** ($9.99 Pro), **Mem** (Free 25 notes/mo) | Cloud | Markdown export promised |
| **Anytype, AFFiNE** | Local-first | Own formats [U for Markdown export] |
| **Tana, Craft, Heptabase, Reflect** | Cloud, $8–30/mo | Markdown export not stated |
| **Evernote** | Free: 50 notes, 1 device; paid ~$99–250/yr [S] | No; not viable free |

**Sync gotchas** (tell the person before the brain lives in a synced folder):
- **Online-only placeholders:** OneDrive Files On-Demand, Google Drive "streaming" and possibly iCloud optimized storage keep files in the cloud; agents may see them as missing, and search finds names, not content. Fix: OneDrive "**Always keep on this device**" on the brain folder; Google Drive **Mirror** mode; iCloud keep downloaded. OneDrive Storage Sense can revert files to online-only.
- **One sync engine per vault.** Avoid syncing the same folder with two services (e.g., Obsidian Sync + iCloud): conflicts and corruption.
- **Git inside OneDrive/Dropbox** can break the `.git` folder (user reports). Keep the repo outside the synced folder, or use git itself as the sync.
- **Android:** OneDrive and Google Drive apps don't reliably sync a folder two-way. Options: Obsidian Sync (official), Syncthing-Fork (official Syncthing app discontinued), FolderSync or Dropsync.
- **iOS:** Obsidian Sync or iCloud (vault inside iCloud Drive's Obsidian folder). Others unsupported; Git via Working Copy works for some.
- Watch for conflict files ("conflicted copy", device-name suffixes) after agent runs; keep paths short (Windows 260-character limit).
- `.gdoc` files in a local Drive folder are pointers, not content: convert to Markdown first [U, widely known].

---

## 5. Capture and voice

### Dictation apps
| App | Free | Paid | Platforms / notes |
|---|---|---|---|
| **Superwhisper** | **Unlimited local Whisper dictation** (nothing leaves the device) | Pro $8.49/mo, $84.99/yr, **$249.99 lifetime** | Mac, Windows, iPhone, Android |
| **Wispr Flow** | 2,000 words/week desktop; limited mobile | Pro $15/mo ($12 annual); 50% education | Mac, Win, iOS, Android; "100+ languages"; Notetaker for meetings (Mac) with MCP |
| **Aqua Voice** | 1,000 words; MCP/CLI included | Pro $12/mo ($10 annual); 70% students | Mac, Win, iOS, Android |
| **Willow** | 2,000 words/week | $15/mo or $144/yr | [U] competitor source |
| **MacWhisper** | Local small models, TXT export | Pro ~€59–64 one-time | macOS; [U] prices from competitor page |

### Phone built-in transcription (free)
- **Pixel Recorder:** Italian and Spanish transcription on Pixel 6+; summaries (incl. Italian) on Pixel 8+; some processing on Google servers.
- **Samsung Transcript Assist** (Galaxy AI): supports Italian and Spanish.
- **iPhone call recording / Notes** (iOS 18.1+): transcription languages did **not include Italian** per a secondary source; may have changed with iOS 26 [U]. Italian iPhone users: suggest a dictation app or local Whisper.

### Meeting recorders
| Tool | Free | Paid | Markdown / API / MCP | Language note |
|---|---|---|---|---|
| **Granola** | 30-day history, MCP for last 30 days | Business $14/user (API, Notion, Zapier) | MCP; community Obsidian plugin | "Multi-language" [U] |
| **Otter** | 300 min/mo, 30-min cap | Pro $16.99 ($8.33 annual) | MCP all tiers; export txt/pdf/docx, **no Markdown**; API Enterprise | **6 languages, no Italian** |
| **Fireflies** | 400 min storage | Pro ~$10 annual | API on all plans | 100+ languages |
| **Fathom** | Unlimited recordings | Premium $20 ($16 annual) | API, MCP, Zapier (tier unclear) | Not stated |
| **Read.ai** | ~5 transcripts/mo (page conflicts) | Pro $15 annual | API, MCP, Claude connector | 16+ incl. Italian |
| **Tactiq** | 10 transcripts/mo, no bot | Pro $8 annual | MCP Business only (beta) | — |
| **Teams + Copilot** | — | Teams Premium $10/user; Copilot business add-on | Intelligent recap | Work accounts |

Markdown export is rare: the practical route to files is MCP/API or copy-paste.

### Transcription APIs (approx. per audio hour) and local
| Option | Price | Note |
|---|---|---|
| Groq Whisper Large v3 Turbo | ~$0.04 [S] | Official page redirects |
| OpenAI gpt-4o-mini-transcribe | ~$0.18 | gpt-4o-transcribe ~$0.36 |
| AssemblyAI | $0.15 (Universal-2) – $0.21 | Up to 185 free hours |
| Mistral Voxtral Mini | ~$0.21 | EU vendor |
| ElevenLabs Scribe | ~$0.22 | — |
| Deepgram Nova-3 | ~$0.26–0.31 | $200 free credit |
| **Local Whisper** (whisper.cpp, faster-whisper) | Free (MIT) | Runs on ordinary laptops; use multilingual models (not `.en`); `turbo` can't translate |

One hour a day costs under ~$11/month on any API. In a real build (October 2026), **Groq's free tier** with `whisper-large-v3` was enough for personal voice notes; its `prompt` parameter accepts a list of names to improve spelling. Groq's file-size limit per request (about 25 MB on the free tier when checked; verify) matters for long lectures: split or compress the audio.

**Phone capture with the computer off (worked example):** Telegram bot (free) → Google Apps Script (free) → Groq Whisper (free tier) → Claude API small model (~$0.001–0.002 per note) → Drive and Calendar. Recipe: `_guide/library/recipes/telegram-voice-bot.md`. Vendor benchmarks put Italian error rates at ~4–7% on clean audio; real meetings are worse.

### Read-later and clipping
- **Pocket** (closed July 2025) and **Omnivore** (shut down late 2024) are gone.
- **Obsidian Web Clipper:** free, open source, saves Markdown into the vault; most browsers.
- **Readwise** (Reader + Highlights) $9.99/mo annual; Obsidian export, MCP, API.
- **Raindrop.io:** Free unlimited bookmarks; Pro ~$28/yr (AI, MCP, full-text) [S for price].
- **wallabag:** open source, or hosted €11/yr.
- Telegram Sync plugin: phone → vault, but desktop Obsidian must be running.

### Document conversion to Markdown
- **Google Docs:** File → Download → Markdown (all accounts, free).
- **MarkItDown** (Microsoft, `pip`): PDF, Office, HTML, images, audio → Markdown; MCP package.
- **Docling** (MIT, `pip`): PDF, Office, images, audio → Markdown with OCR; MCP server.
- **Mistral OCR:** $2–4 per 1,000 pages for scanned documents.
- pandoc, pdftotext: free CLI alternatives (not re-verified).

---

## 6. Realistic stacks by level and budget (suggestions)

| Level | Assistant | Automation | Store | Capture | Approx. monthly |
|---|---|---|---|---|---|
| **Beginner, €0** | Any free tier (chat mode; files copied by hand) | None; flows run "when I ask" | A folder of Markdown (or Google Docs/Sheets) | Phone recorder, Web Clipper, Google Docs → .md | €0 |
| **~€20/month** | One standard plan, e.g., Claude Pro (Cowork, folder, scheduled tasks) or ChatGPT Plus/Go or Google AI Pro | The assistant's own scheduled tasks | Markdown folder + one Sheet | Superwhisper Free / Wispr Free; Pixel/Samsung recorder | ~€20 |
| **Intermediate** | Same | Zapier Professional or Relay (approvals), or Activepieces Free | Notion Plus or Sheets + Markdown | Granola/Fathom free; Obsidian Sync if mobile | ~€30–45 |
| **Technical / advanced** | Claude Code or Codex on the existing plan; Aider/Cline + API key | Scripts + git; self-hosted n8n with human review | Markdown + git; SQLite or Supabase | Local Whisper or a transcription API | €20 + a few € API; up to ~€60–100 with hosting (estimate) |

Cost bands are estimates built from component prices; no survey of real spend was found. Costs grow with the number of flows and how often they run.

---

## Sources

- Zapier pricing: https://zapier.com/pricing ; Human in the Loop: https://help.zapier.com/hc/en-us/articles/38731463206029
- Make pricing: https://www.make.com/en/pricing ; [S] https://www.jetadmin.io/blog/make-pricing/
- n8n pricing: https://n8n.io/pricing/ ; human review: https://docs.n8n.io/advanced-ai/human-in-the-loop-tools/
- Activepieces: https://www.activepieces.com/pricing
- Power Automate licensing: https://learn.microsoft.com/en-us/power-platform/admin/power-automate-licensing/deep-dive-on-specific-license ; https://learn.microsoft.com/en-us/power-platform/admin/power-automate-licensing/types
- Apps Script quotas: https://developers.google.com/apps-script/guides/services/quotas
- IFTTT: https://ifttt.com/plans ; Relay: https://www.relay.app/pricing ; Lindy: https://www.lindy.ai/pricing ; Pipedream: https://pipedream.com/pricing
- MCP intro: https://modelcontextprotocol.io/docs/getting-started/intro ; servers: https://github.com/modelcontextprotocol/servers ; security: https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/security_best_practices.md
- Notion MCP: https://developers.notion.com/docs/mcp ; GitHub MCP: https://github.com/github/github-mcp-server ; Google Workspace MCP: https://developers.google.com/workspace/guides/configure-mcp-servers
- Composio: https://composio.dev/pricing.md ; Zapier MCP [S]: https://latenode.com/blog/zapier-mcp-pricing
- Notion pricing: https://www.notion.com/pricing ; export: https://www.notion.com/help/export-your-content
- Airtable: https://support.airtable.com/docs/airtable-plans ; Baserow: https://baserow.io/pricing ; NocoDB: https://nocodb.com/pricing ; Supabase: https://supabase.com/pricing
- Obsidian pricing: https://obsidian.md/pricing.html ; CLI: https://obsidian.md/help/cli ; sync: https://obsidian.md/help/sync-notes ; Web Clipper: https://obsidian.md/clipper
- Logseq: https://logseq.io/p/e3YDyX5AYr ; https://discuss.logseq.com/t/whats-new-with-logseq-db-may-16th-2026/35020
- OneDrive Files On-Demand: https://support.microsoft.com/en-us/office/save-disk-space-with-onedrive-files-on-demand-for-windows-0e6860d3-d9f3-4971-b321-7092438fb38e ; Google Drive stream vs mirror: https://support.google.com/drive/answer/13401938 ; git in OneDrive [practitioner]: https://techcommunity.microsoft.com/discussions/onedriveforbusiness/onedrive-is-corrupting-my-git-repositories/3898283
- Markor: https://github.com/gsantner/markor ; Capacities: https://capacities.io/pricing ; Mem: https://get.mem.ai/pricing ; Evernote: https://evernote.com/compare-plans
- Wispr Flow: https://wisprflow.ai/pricing ; Superwhisper: https://superwhisper.com/docs/billing/plans.md ; Aqua: https://aquavoice.com/pricing ; [S] MacWhisper: https://www.getvoibe.com/resources/macwhisper-pricing/ ; [S] Willow: https://www.getvoibe.com/resources/willow-voice-pricing/
- Pixel Recorder: https://support.google.com/pixelphone/answer/16267698?hl=en ; Samsung: https://www.samsung.com/uk/support/mobile-devices/how-to-use-transcribe-assist-on-the-galaxy-s24/ ; [S] iPhone: https://www.macworld.com/article/2536876/how-to-record-and-transcribe-voice-calls-on-your-iphone.html
- Granola: https://www.granola.ai/pricing ; Otter: https://otter.ai/pricing ; Fireflies: https://fireflies.ai/pricing ; Fathom: https://www.fathom.ai/pricing ; Read.ai: https://www.read.ai/plans-pricing ; Tactiq: https://tactiq.io/pricing ; [S] Teams: https://eesel.ai/blog/microsoft-teams-pricing
- OpenAI API: https://developers.openai.com/api/docs/pricing ; [S] Groq: https://www.morphllm.com/groq-pricing ; Deepgram: https://deepgram.com/pricing ; AssemblyAI: https://www.assemblyai.com/pricing ; ElevenLabs: https://elevenlabs.io/pricing/api ; Mistral: https://docs.mistral.ai/models/pricing ; benchmarks: https://www.assemblyai.com/benchmarks
- whisper.cpp: https://github.com/ggml-org/whisper.cpp ; faster-whisper: https://github.com/SYSTRAN/faster-whisper ; Whisper: https://github.com/openai/whisper
- Pocket: https://support.mozilla.org/en-US/kb/future-of-pocket ; wallabag: https://wallabag.it/en/alternatives/omnivore/ ; Readwise: https://readwise.io/pricing ; Raindrop: https://raindrop.io/pro/buy
- Google Docs Markdown: https://workspaceupdates.googleblog.com/2024/07/import-and-export-markdown-in-google-docs.html ; MarkItDown: https://github.com/microsoft/markitdown ; Docling: https://github.com/docling-project/docling
