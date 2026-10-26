# AI assistants: plans, capabilities and costs

Prices and features as checked on 2026-10-24. They change often: verify current details at runtime (web search) before recommending.

How to use this file: consult it when the person asks "which AI should I use?", when you plan who runs a flow, or when you explain cost direction. Do not read it to the person. Labels: **[V]** = vendor's own page; **[S]** = secondary source only (comparison site, blog); **[U]** = unconfirmed or conflicting. Treat [S] and [U] as "check before relying on it".

---

## 1. Plans and prices (USD, US region)

No official EUR prices could be captured for any vendor. EU prices are often the same number in EUR including VAT, but this is **not verified**: check the vendor page in the person's country.

| Assistant | Free | Cheap tier | Standard (~$20) | Power tier | Business / team | Status |
|---|---|---|---|---|---|---|
| **Claude** | $0 | — | Pro $20/mo ($17/mo billed annually) | Max from $100/mo (5x usage); $200 for 20x [S for the $200 figure] | Team Standard $25/seat monthly or $20 annual; Team Premium $125/$100; Enterprise $20/seat annual + usage | [V] |
| **ChatGPT** | $0 | Go: **$5.50 or $8** (sources conflict); "may show ads" | Plus $20 | Pro $100 and/or $200 (and $500 per one source); $200 tier reportedly paused for new sign-ups | Business $25/user monthly or $20 annual, 2-seat minimum | **[U]** official page showed no prices; two third parties disagree |
| **Google AI (Gemini)** | $0 (15 GB) | AI Plus $4.99 (400 GB) | AI Pro $19.99 (5 TB, 1M-token context) | AI Ultra $99.99 or $199.99 | Via Workspace plans | [V]; availability varies by country |
| **Microsoft Copilot / 365** | Copilot free, "subject to available capacity" | M365 Personal $9.99/mo ($99.99/yr); Family $12.99 ($129.99/yr, AI for owner only) | M365 Premium $19.99 ($199.99/yr) | M365 Pro $99.99/mo | M365 Copilot Business add-on $18/user annual (promo to 31 Dec 2026, normally $21) or $25.20 monthly; Business Standard with Copilot $23.50 annual | [V] |
| **Perplexity** | $0 (~5 Pro searches/day) | Education Pro $10 | Pro $20/mo ($200/yr) | Max $200/mo | Enterprise Pro $40/seat; Enterprise Max $325 | **[U]** April 2026 third-party figures, not confirmed for October |
| **Mistral (Le Chat, plans now branded "Mistral Vibe")** | $0 | Students $5.99 | Pro $14.99 (excl. tax) | — | Team $24.99/user | [V]; EUR toggle exists but amounts did not render |

Pattern that is stable even when prices move: free → cheap (~$5–15) → standard (~$20) → power ($100–200) → per-seat business (~$20–25).

---

## 2. Capabilities that matter for a second brain

### 2a. Basics (available on most free tiers, with tighter limits)

| Capability | Claude | ChatGPT | Gemini | Copilot (consumer) | Perplexity | Mistral |
|---|---|---|---|---|---|---|
| **Image input** (e.g., reading a photo of a hand-drawn map) | Yes, all plans | Free "limited"; Go+ yes | Yes [U for per-plan limits] | "Visual assistance" on paid M365 plans | Photo uploads on Pro | Yes [U] |
| **Web search** | All plans | All plans | All plans | Yes | Core feature | Free limited; Pro 5x |
| **File creation / code execution** | All plans (incl. Free) | "Data analysis": Free limited, Go+ yes | [U] | Copilot in Word/Excel on paid plans | [U] | [U] |
| **Projects** | Free up to 5; paid unlimited | All plans | "Gemini Notebook" on every plan | — | Spaces (50 files, 50 MB each, Pro) | Pro up to 1,000 project folders |
| **Memory** | All plans | Free limited; Plus/Pro expanded | [U] | [U] | [U] | Yes (Sep 2025 page) |
| **Deep research** | Pro and up | Free/Go limited; Plus+ yes | All plans | Researcher agent (business) | Pro 20/day | [U] |

Takeaway: a **chat-only person on any free tier** can photograph their map, search the web, upload files and keep a project. Paid tiers mainly add higher limits, unattended runs and agents.

### 2b. Local folder access (the second brain lives in a folder)

| Tool | Reads/writes a local folder? | Plan |
|---|---|---|
| Claude desktop app / Cowork | Yes, without a terminal | Cowork on paid plans (desktop macOS, Windows, Linux beta); also web/mobile on Pro/Max/Team |
| Claude Code (terminal/IDE) | Yes | Pro and up, or API key |
| ChatGPT desktop ("ChatGPT Work") / Codex app | Likely, **not verified** | Work: limited on Free/Go (desktop only), full on Plus/Pro; Codex limited on Free/Go |
| Gemini CLI / Antigravity, Jules | Yes (CLI) / repo-based | See section 3 |
| Copilot, Perplexity, Le Chat web | No local folder; upload files instead | — |

### 2c. Scheduled / recurring tasks

| Assistant | Plans | Limits | Can it reach local folders? |
|---|---|---|---|
| **Claude** (Cowork scheduled tasks) | All paid plans; not on Free [V] | Hourly, daily, weekly, weekdays, manual | **Since 6 Oct 2026, new tasks on Pro/Max run in the cloud** with no device online. A cloud task **cannot read a laptop folder**. Tasks that need local files, local MCP or browser use need the **desktop app open and the computer on**. Tasks created locally before 6 Oct stay local. [V] (two help pages phrase this slightly differently; recheck) |
| **ChatGPT** Tasks | Go 3 active, Plus 5, Business/Edu 10, Pro/Enterprise 15 | Managed on web and mobile, not the desktop app | No local folder access (cloud). Help page is inconsistent on whether Go is eligible [V/U] |
| **Gemini** scheduled actions | AI Pro, Ultra, qualifying Workspace | Up to 10 active | Cloud only. **2025 source, not re-confirmed** [U] |
| **Mistral** | Free 5 tasks; Pro/Team unlimited | — | Cloud only [V] |
| Copilot, Perplexity | Not documented | — | — |

Design consequence: a flow that runs at 07:00 while the person sleeps should read cloud sources (Gmail, Calendar, Drive) and write to a cloud-synced place, or the person accepts that the computer must be on.

### 2d. Native connectors: read vs write

| Assistant | Email / calendar / files | Read or write | Other connectors | Notes |
|---|---|---|---|---|
| **Claude** | Gmail, Google Calendar, Google Drive, "available to all users" [V] | **Write.** Gmail drafts, sends, replies, forwards (asks before each send by default). Calendar creates/updates/deletes events. Drive uploads and saves files; share/move/trash need approval [V] | Directory: Slack, Notion, Linear, Canva, Stripe, PayPal, Plaid… [S] | Gmail reads attachment **metadata, not content**. Team/Enterprise owners must enable connectors |
| **ChatGPT** | Gmail, Drive, Calendar as "apps" (renamed from connectors, Dec 2025) [V] | Reads by default, asks before "important actions" [V]. Gmail send after approving a draft (paid, web), Drive read/write, Calendar create [S, unconfirmed] | App directory | Some apps not available in **EEA, UK, Switzerland**, depending on the partner [V] |
| **Gemini** | Gmail, Calendar, Drive, Docs, Keep, Tasks, Photos, Maps [V/S] | Creating events, sending messages "with permission"; per-app actions vary [V] | Spotify, WhatsApp (Android), Dropbox, GitHub, Canva…; no Slack/Notion [S] | Requires **Keep Activity on**. Availability "varies by location, language, device" [V] |
| **Copilot (consumer)** | OneDrive, Outlook.com mail/calendar/contacts, Gmail, Google Calendar/Drive/Contacts [V] | **Read and search only** documented [V] | — | M365 Personal/Family/Premium/Pro; Copilot.com and mobile only |
| **Perplexity** | Gmail + Calendar, Outlook.com, OneDrive, SharePoint, Drive, Dropbox, Box [V] | Gmail/Calendar "search and perform actions"; Outlook/OneDrive mostly read [V] | Notion, Slack, Asana, Jira, HubSpot | Per-plan tiers unconfirmed |
| **Mistral** | Outlook, Box via MCP directory [V] | Per connector | 20+ MCP connectors (Notion, Asana, Linear, Zapier…); pricing page says "100+ connectors" | All available on Free (Sep 2025 page) |

**Observed in a real build (October 2026), Claude:** the Google Drive connector could **create** files but **could not modify the content of existing files**, and didn't read plain-text/Markdown content reliably; Google Calendar create/update/delete worked as documented. Consequence: cloud scheduled tasks suit flows that *create* outputs; flows that *modify* files need the desktop app (computer on) or a script (e.g., Google Apps Script). Connectors change: **test the exact action** before designing a flow on it. Details: `field-notes-2026-10.md`, section 7.

### 2e. Custom MCP connectors (connect anything else)

| Assistant | Custom MCP | Plan |
|---|---|---|
| Claude | Remote MCP connectors (OAuth or API key; server must be reachable from the internet) | **All plans; Free limited to one** [V]. Local MCP servers only via the desktop app, not in Cowork or the web [V] |
| ChatGPT | Developer Mode | Full MCP **with write** in beta for Business/Enterprise/Edu; **Pro read/fetch only**; web only; agent mode doesn't use custom apps [V]. Free/Go unclear [U] |
| Gemini | Via Gemini Spark (since 30 Jun 2026) | **Personal accounts only, English, Keep Activity on**; not work or school accounts [S]; plan tiers unconfirmed |
| Mistral | Any remote MCP | Free plan [V] (Sep 2025 announcement) |
| Copilot, Perplexity | Not documented | — |

Tip: on Claude Free (one custom slot) an MCP hub (Zapier MCP, Composio) can stand in for many apps. See `tools-and-costs-2026-10.md`.

### 2f. Region and account limits

- **EEA / UK / Switzerland:** some ChatGPT apps are not offered, depending on the partner [V]. Gemini Connected Apps vary by location [V]. Native health-record connectors (ChatGPT, Claude) are **US-only** [V]. No EU connector restriction found for Claude, Copilot or Perplexity (gap, not a guarantee).
- **School and work accounts:** the organization decides. On Claude Team/Enterprise an owner must enable connectors and Cowork, and decides whether send/share may run without asking [V]. Gemini custom MCP is not supported on work/school accounts [S]. University Microsoft 365 / Google Workspace accounts often block third-party apps ("Approval required" / admin consent) [V]. Advice: if a school or work account blocks a connector, suggest forwarding to a personal mailbox only if the institution's rules allow it.
- **Privacy defaults:** consumer plans usually train on data unless the person opts out (ChatGPT "Opt-out available"; Mistral opt-out on Pro+) [V]. Claude, Gemini and Copilot consumer defaults were not verified. Suggest checking the training toggle before uploading personal notes.

---

## 3. Agentic tools that work on a folder

| Tool | Free option | Paid direction | Ease |
|---|---|---|---|
| **Claude Cowork** (desktop) | — | Included in paid Claude plans | No terminal; easiest for non-technical people |
| **Claude Code** | None | Included from Pro ($20); or API key per token | Terminal/IDE |
| **OpenAI Codex** | Free plan "light tasks" in the desktop app [S]; "Limited" on Free/Go [V] | Included in Plus; "Expanded" on Pro | Desktop app lowers the barrier |
| **Gemini CLI / Antigravity CLI** | Google login 1,000 requests/day; unpaid API key 250/day (Flash only) | AI Pro 1,500/day; Ultra 2,000/day | **[U]** the same official page says Gemini CLI "was replaced by Antigravity CLI" for unpaid users in June 2026; it is internally inconsistent |
| **Cursor** | Limited agent/chat | New plans from Oct 2026: Plus $8, Premium $30, Super $100, Ultra $200; frontier models billed at API price from credit | [S] single aggregator |
| **GitHub Copilot** | 2,000 completions/mo + limited chat/agent | Pro $10, Pro+ $39, Max $100; extra usage metered per credit | [S] |
| **Windsurf** (renamed "Devin Desktop") | Light quota | Pro $20, Max $200 | [S] |
| **Aider, Cline** (open source) | Free software; you pay the model API | Typical solo use $5–50/mo in API [S] | Need your own API key; Aider can use local models via Ollama (fully free) |
| **OpenCode** | Open source, own key [U] | — | — |

Everything except Cowork and the Codex desktop app assumes comfort with a terminal or code editor.

---

## 4. API (pay-per-use) prices

**Claude** [V as read on the official pricing page on 2026-10-24; these are much lower than earlier model generations' list prices, so **re-check before quoting**: https://claude.com/pricing], USD per million tokens, input / output:

| Model tier | Standard | Batch (−50%) |
|---|---|---|
| Opus (most capable) | $4 / $20 | $2 / $10 |
| Sonnet (balanced) | $2 / $10 | $1 / $5 |
| Haiku (fast, cheap), prompts ≤100K tokens | $0.10 / $0.50 | $0.05 / $0.25 |
| Haiku, prompts >100K tokens | $0.50 / $2.50 | $0.25 / $1.25 |

Prompt-cache hits cost 5–10% of the input price. **OpenAI and Gemini per-token prices were not fetched**: look them up at runtime.

**Transcription APIs** (per audio hour, approx.): Groq Whisper Turbo ~$0.04 [S]; OpenAI gpt-4o-mini-transcribe ~$0.18; AssemblyAI $0.15–0.21; Mistral Voxtral ~$0.21; ElevenLabs Scribe ~$0.22; Deepgram ~$0.26–0.31. Details in `tools-and-costs-2026-10.md`.

---

## 5. Subscription vs pay-per-use vs automation-platform tasks

| Model | How the cost behaves | Grows with | Good for |
|---|---|---|---|
| **Subscription** (~$20/mo) | Flat; usage caps instead of surprise bills | Only if you move to a power tier | Most people; predictable; includes chat, projects, scheduled tasks, agents |
| **Pay-per-use API** | Pennies per light run; unbounded at the top | Number of flows × frequency × size of context × model tier | Technical users, scripts, open-source agents |
| **Automation platform** | Monthly plan with a quota of tasks/credits/executions, plus the AI model's own bill if you bring a key | Steps per run (per-step billing) or runs; polling frequency | App-to-app moves with retries and approvals |

Reference points:
- **Light personal use:** a practitioner reported ~$10–15/month in API for daily briefs, weekly consolidation and occasional commands [S]. A few on-demand flows on a cheap model: likely a few dollars a month (estimate).
- **Heavy use:** a founder running dozens of heavy daily automations reported a month of about **€1,000** in AI usage (anecdote). Costs scale with frequency and context size, not with the number of ideas.
- **Hidden multipliers:** a 5-minute schedule around the clock is ~2,000 runs/week vs 20 for a weekday 30-minute check; per-step platforms charge a 6-step flow ~6 units per run; large always-loaded context files are paid on every run.

Advice for the guide: start on the subscription the person already has; move a flow to API or a platform only when it needs to run unattended or at volume; show the cost direction before building.

---

## 6. Which assistant for which person (advice, not rules)

| Person | Suggested starting point (simplest first) | Why |
|---|---|---|
| Chat-only, wants $0 | Any free tier they already use (Claude, ChatGPT, Gemini, Le Chat) | Vision, search, projects work for design steps; files are copied by hand (chat mode) |
| Chat-only, wants automation cheaply | Mistral Free (5 scheduled tasks, free custom MCP) or ChatGPT Go (3 tasks) | Cheapest unattended runs; verify current limits |
| Non-technical, wants the brain in a folder | Claude Pro with Cowork | Local folder without terminal, scheduled tasks, write-capable Google connectors |
| Lives in Google (Gmail, Keep, Android) | Google AI Pro, or Claude for write-capable Gmail/Calendar | Gemini is strongest on Google's own apps; check scheduled actions status |
| Lives in Microsoft 365 | Their M365 plan's Copilot for reading; Power Automate for writing | Consumer Copilot connectors are read-only |
| Research-heavy | Perplexity Pro, or Deep Research on any standard tier | Search-first |
| Wants EU vendor / privacy focus | Mistral, or local models via open-source agents | EU vendor; opt-out on paid tiers |
| Technical | Claude Code or Codex on an existing plan; Aider/Cline + API key or local models | Full control of the folder, git, scripts |
| School or work account only | Whatever the institution enables; suggest a personal account for the personal brain | Admins control connectors |

Always: ask what they already pay for before suggesting anything new.

---

## Sources

- Claude pricing: https://claude.com/pricing
- Claude scheduled tasks: https://support.claude.com/en/articles/13854387-schedule-recurring-tasks-in-claude-cowork
- Claude Cowork on web/desktop/mobile: https://support.claude.com/en/articles/15520349-use-claude-cowork-on-web-desktop-and-mobile
- Claude custom connectors (remote MCP): https://support.claude.com/en/articles/11175166-getting-started-with-custom-connectors-using-remote-mcp
- Claude Google Workspace connectors: https://support.claude.com/en/articles/10166901-use-google-workspace-connectors
- Claude API pricing: https://platform.claude.com/docs/en/about-claude/pricing
- ChatGPT pricing: https://chatgpt.com/pricing
- ChatGPT Tasks: https://help.openai.com/en/articles/10291617-tasks-in-chatgpt
- ChatGPT apps: https://help-lb.openai.com/en/articles/11487775 ; developer mode: https://help-lb.openai.com/en/articles/12584461
- Introducing apps in ChatGPT: https://openai.com/index/introducing-apps-in-chatgpt/
- ChatGPT Google write features [S]: https://www.usecarly.com/blog/chatgpt-work-google-workspace-integration/
- ChatGPT prices [S]: https://krater.ai/blog/chatgpt-pricing ; https://agentdeals.dev/ai-coding-pricing-2026
- Gemini subscriptions: https://gemini.google/subscriptions/
- Gemini Connected Apps: https://support.google.com/gemini/answer/13695044
- Gemini scheduled actions [S, 2025]: https://www.androidauthority.com/gemini-scheduled-actions-rollout-3565152
- Gemini Spark MCP [S]: https://www.techrepublic.com/article/news-gemini-spark-app-integrations/
- Gemini CLI quotas: https://geminicli.com/docs/resources/quota-and-pricing
- Microsoft Copilot individuals: https://www.microsoft.com/en-us/copilot/pricing/individuals ; business: https://www.microsoft.com/en-us/microsoft-365/copilot/pricing
- Copilot connectors: https://support.microsoft.com/en-us/Microsoft-Copilot/connecting-microsoft-copilot-to-other-services
- Perplexity prices [S]: https://www.finout.io/blog/perplexity-pricing-in-2026 ; connectors: https://intercom.help/perplexity-ai/en/collections/18799295-connectors-integrations
- Mistral pricing: https://mistral.ai/pricing ; MCP connectors: https://mistral.ai/fr/news/le-chat-mcp-connectors-memories
- Coding tool prices [S]: https://agentdeals.dev/ai-coding-pricing-2026
- Practitioner API spend [S]: https://dev.to/huy_tieu/i-finally-built-a-second-brain-that-i-actually-use-6th-attempt-4075
