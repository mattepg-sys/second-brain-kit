# Connecting platforms to the second brain

Condensed reference, checked in October 2026 (tags: [V] verified on a primary source, [S] secondary source, [U] unconfirmed — anything not [V] must be checked). Platforms and rules change: verify specifics at runtime.

**Tags:** **[V]** confirmed on a primary or directly fetched page around October 2026 · **[S]** secondary source only (blog, press, aggregator) · **[U]** unconfirmed: treat as "to verify". Untagged lines are advice. Prices are examples of the cost *direction*, not commitments.

---

## 1. The principle: there is almost always a route

- If the obvious connection ("connect my bank to the AI") is blocked, **look for another route**. Nearly every platform lets you get data out somehow: an export file, a calendar link, a notification email, an RSS feed, the phone's share sheet.
- In late 2026 the most dependable channel is usually the plainest: **a file, an email or a calendar feed lands in `Inbox/`, then the AI reads it and files it as Markdown.** Live APIs are the exception, and the trend for consumer platforms is toward *less* API access, not more [V].
- Ask first "what does this platform let you **export, email or subscribe to**?", then "is there an integration?".
- **Research the person's specific bank, school, app or portal at runtime.** This file gives patterns; the details per institution change and many were never verified.
- Default to **read-only** access. Almost no valuable flow needs write access beyond creating a draft or a calendar event.

## 2. The connection-methods ladder

From least to most technical. Start at the lowest rung that does the job; climb only if the person wants to.

| # | Method | What it looks like | Skill needed | Cost direction |
|---|---|---|---|---|
| 1 | **Manual export / download** | CSV, PDF, ZIP, "Download your data" into `Inbox/` | None | Free |
| 2 | **Share sheet / copy-paste / photo** | Phone "Share to" a notes app or folder; screenshot; photo of paper | None | Free |
| 3 | **Calendar link (iCal/ICS)** | Subscribe to a platform's feed in a personal calendar | None | Free |
| 4 | **Email forwarding / filters** | Notifications, receipts, alerts sent to one label or address | Low | Free |
| 5 | **Assistant's native connectors** | Gmail, Calendar, Drive, Notion… inside the AI app | Low | Included in plan; write access varies by assistant |
| 6 | **RSS feed** | Blogs, newsletters, YouTube channels, podcasts | Low | Free; automation tools have RSS triggers |
| 7 | **Automation platform** | Zapier, Make, n8n, IFTTT turning emails/feeds/files into notes | Medium | Free tiers are small; billing per task/step grows with volume |
| 8 | **MCP server / hub** | A connector the AI can call (official, community, or a hub like Zapier MCP or Composio) | Medium–high | Often free to start; hubs bill per call (Zapier MCP: 2 tasks per call [V]) |
| 9 | **Official API with a personal token** | Telegram bot, Notion API, Todoist API, Canvas token | High | Usually free; keep tokens secret |
| 10 | **Small script or self-hosted tool** | Python/Apps Script, Actual Budget, Firefly III, moodle-dl | High | Free software; your time and hosting |

Notes:
- Claude Free allows **one** custom remote MCP connector [V]; a hub (one connector, many apps) helps there.
- Claude's Gmail connector reads attachment *metadata*, not content [V]: for receipts or school PDFs, add a step that saves attachments to Drive or a folder.
- Unattended (scheduled) runs in the cloud cannot see a laptop folder: such flows should read cloud sources and write to a cloud-synced place [V for Claude cloud scheduled tasks].
- Unofficial clients and scrapers exist for many platforms; they can break without notice and may breach terms. Mention them as an option, with that caveat; the person decides.

---

## 3. Domain by domain

Each domain: **non-technical path**, **technical path**, **pitfalls**.

### Email and calendar
- **Non-tech:** use the assistant's native connector (Claude reads/writes Gmail, Calendar, Drive on all plans, asking before each send by default [V]; consumer Copilot is read-only for Outlook.com and Google [V]; ChatGPT and Gemini have Google connectors with plan-dependent actions [V/S]). Use filters/labels to isolate what a flow should read. For iCloud or Proton calendars, share a calendar link.
- **Tech:** Gmail API, Apps Script, Microsoft Graph, Google's official Workspace MCP servers (Developer Preview; need a Cloud project and OAuth client; whether consumer @gmail.com works was not stated [V]). iCloud: IMAP/CalDAV with an app-specific password [U]. Proton: paid Bridge running locally [U].
- **Pitfalls:** work/school tenants may block third-party apps (see University). Google OAuth apps left in "testing" mode get refresh tokens that expire after about 7 days [U]. Keep drafts as the default output; sending stays a human step unless the owner chooses otherwise.
- **Calendars from other organizations:** an Outlook calendar shared by email may not add with its button in Google Calendar; use the **ICS link** in the invitation ("this URL") and add it in Google Calendar → Other calendars → **From URL**. A Google Workspace calendar of another organization may show only **free/busy** (the admin decides). A common, safe choice: **read all calendars, write only to the personal one**. Subscribed calendars refresh every few hours, not instantly.
- **Free cloud script for Google:** Google Apps Script can read Gmail, write Drive files (including changing existing ones with `setContent`), manage Calendar, and receive webhooks (e.g., from a Telegram bot), with the computer off. A worked example: `_guide/library/recipes/telegram-voice-bot.md`.

### Messaging
- **WhatsApp (personal):** per-chat "Export chat" to a .txt file via the share sheet; no bulk export, no personal API [U]. Unofficial bridges (web-client libraries) breach WhatsApp's terms and risk a ban on the number [U]. Gemini on Android can *send* WhatsApp messages, but that is not a way to read chats into the brain [V].
- **WhatsApp Business API:** since 15 Jan 2026 Meta's terms ban providers whose core product is a general-purpose AI chatbot; business bots ancillary to a real service (support, bookings) remain allowed [V]. Exceptions: **Italy** (from Jan 2026, after an AGCM order) and **the EU for 12 months from around March 2026**, with fees critics called "vexatious" [S/V]. Too fluid to build on: date-stamp it and check at runtime.
- **Telegram (recommended bot channel):** free official Bot API; create a bot with @BotFather; n8n, Make and Zapier have Telegram nodes; Desktop exports your own chats as JSON/HTML [U]. Bots see only chats they are added to. Good for "send a note/photo to my brain" and family logistics groups.
- **Signal / iMessage:** no official APIs; only unofficial tools (signal-cli; reading the Mac Messages database with Full Disk Access) [U].
- **Slack / Discord:** robust bot APIs; Slack connectors exist in Claude and Perplexity [S]. Slack may rate-limit history reads for non-Marketplace apps [U].

### Social and publishing
- **Read via RSS or export; write by hand**, except on creator-friendly tools.
- **LinkedIn:** download your data archive (non-tech). **EEA members only:** the DMA Member Data Portability API gives a snapshot plus a 28-day changelog of your own activity, from the moment of consent [S]. No general personal API; no personal posting API; scraping breaches terms [V].
- **X:** API moved to **pay-per-use credits** on 6 Feb 2026; free tier effectively ended; status of the old entry plan unclear [S]. Post manually, or budget for credits.
- **Instagram:** API only for **professional** (Business/Creator) accounts; switching is free and reversible; personal accounts have had no API since Dec 2024 [S/V].
- **YouTube:** channel RSS (`youtube.com/feeds/videos.xml?channel_id=…`); Data API free with a default 10,000 units/day quota [U].
- **Substack:** RSS at `/feed` and subscriber CSV export; no publishing or subscriber API; a read-only MCP for Bestseller admins (July 2026) rests on one aggregator [S].
- **beehiiv:** API on all plans including Free; MCP from Lite (~$49/mo yearly); webhooks from Pro (~$95/mo yearly) [V]. Whether the API can create a *draft* post was not checked.
- **Medium:** RSS only; API unmaintained [U].

### Tasks and notes
- **Non-tech:** native connectors (Notion in Claude/Perplexity/Mistral; Google Tasks via Gemini [S]); Zapier/Make recipes; email-to-task addresses (Things "Mail to Things", Todoist) [U]; Apple Shortcuts for Reminders/Things [U].
- **Tech:** official APIs for Todoist (consolidated "API v1" [U]), TickTick (limited Open API), Microsoft To Do (Graph), Google Tasks; Notion API and official hosted MCP (read/write) [V, earlier research].
- **Pitfalls:** Notion export can't rebuild a workspace and may take hours [V] — keep the brain's source of truth in plain files if portability matters. Things and Reminders have no cloud API (local URL scheme/AppleScript only) [U].

### Reading
- **Kindle:** no API. Highlights via the Kindle notebook page, `My Clippings.txt`, or Obsidian importer plugins [V]; or **Readwise**, which syncs Kindle and other sources and has an official Obsidian export (paid, ~$8–10/month yearly [V, earlier research]).
- **Pocket:** **closed**. Shut down July 2025; API off and data deleted from 12 Nov 2025 [V]. Alternatives named in press: Readwise Reader, Instapaper, Raindrop [S].
- **Web clipping:** Obsidian Web Clipper (free) saves pages as Markdown [V]; RSS for blogs and newsletters.

### Banking and finance
- **Non-tech (works with every bank):** once a month, export CSV/XLS/PDF statements into a finance inbox; the AI categorises, compares months, lists subscriptions. Spanish banks commonly also offer Norma 43 files [U]. Revolut and N26 have no official retail API [U] — export works.
- **Tech, EU/UK:** **Enable Banking free "restricted mode"**: create a Production app, keep its private key safe, link only your own accounts [V]. Feed it into **Actual Budget** or the **Firefly III Data Importer**, both supporting Enable Banking [V]. Bank-by-bank coverage in Spain/Italy not verified: check its live bank list.
- **GoCardless (ex-Nordigen) has accepted no new sign-ups since July 2025** [V] — older tutorials using it are obsolete for new users.
- **Tech, US:** **SimpleFIN Bridge** (~$15/year, up to 25 institutions) → Actual Budget or similar [V]. YNAB and Lunch Money have official APIs and community MCP servers [U/S].
- **UK:** Monzo personal API and Starling scoped Personal Access Tokens [U].
- **Wise:** personal API tokens are now documented for **business** accounts; statements via API only for accounts based in a few countries (US, CA, AU, NZ, SG, MY) [V]. Business tokens can create transfers.
- **Italy:** private citizens can download every **B2C e-invoice** (XML) from Agenzia delle Entrate "Fatture e corrispettivi" with SPID/CIE/CNS, no enrolment since 2024; files kept only until **31 December of the second year** after receipt (~2 years), and access can't be delegated [V]. A quarterly download habit avoids losing them.
- **Italy, freelancers (partita IVA):** received and issued e-invoices are in the same AdE "Fatture e corrispettivi" area; the accountant (commercialista) often already has delegated access, so ask them before building an invoices flow [U].
- **Pitfalls:** connect **read (account information) access only, never payment initiation**. Some community finance MCP servers expose write tools such as "create transaction" [S]. Actual stores bank-sync keys without end-to-end encryption [V]. Open-banking consents often need renewing every 90–180 days in the EU [U]; put a reminder in the flow. Keep keys and PEM files in a password manager, never in the brain's notes. Corporate aggregators (Tink, TrueLayer, Plaid production) target companies, not individuals [U].

### Health
- **AI assistants' native health features are US-only:** ChatGPT Health (US hospital portals, Apple Health; Free–Pro; not HIPAA-eligible) [V]; Claude health connectors (HealthEx, Function, Apple Health and Health Connect in beta; Pro/Max) [V]. None confirmed in any EU country. Fitbit's Gemini coach: Premium, English, US/UK/CA/AU/NZ/SG only [S].
- **Android:** Health Connect (Android 14+) has a built-in **scheduled export** (daily/weekly/monthly ZIP to a cloud app); **medical records are excluded** [V].
- **iPhone:** Apple Health has no automatic export of its own; apps such as **Health Auto Export** write JSON/CSV to iCloud Drive, Google Drive or Dropbox (automatic export needs the paid Premium tier, a few euros a year) [V]. Technical: it can also push to your own REST/MQTT endpoint [V].
- **Oura:** data download from the membership hub; OAuth API needs an **active membership** on Gen3 and later [V].
- **Garmin:** developer program **paused for new applicants** in 2026, no reopening date [S]. Route: sync Garmin to Apple Health or Health Connect, then export from there.
- **Clinical documents, EU:** Italy — download referti PDFs from the regional **Fascicolo Sanitario Elettronico** (FSE 2.0 reported fully active in May 2026, with dossier farmaceutico and document hiding) [S]; App IO route [U]. Spain — **Mi Carpeta Ciudadana** shows national health-record documents as PDFs after Cl@ve/certificate/DNIe login [S]. Expect PDFs, not structured data.
- **EHDS timeline:** EU regulation in force since 26 Mar 2025; patient summary and ePrescription exchange due **March 2029**, lab results, images and discharge reports **March 2031** [V].
- **Pitfalls:** sensitive data — see `safety-advice.md`. Values extracted from PDFs can be misread: every number should link to its source PDF and be checked by the person. Summaries, never diagnoses.

### School and family (children)
- **Google Classroom:** ask the teacher/admin to invite you as **guardian**; you get daily or weekly email summaries of missing and upcoming work and announcements, **no grades**; the invite must be accepted within 120 days [V]. Route those emails to a label → AI extracts due items and proposes calendar events.
- **Italian and Spanish registers** (ClasseViva, Argo, Axios; Raíces, PASEN, iEduca, Educamos, Alexia), ClassDojo, Seesaw: **mostly unverified**. No official export or iCal confirmed for ClasseViva [U]; an unofficial client exists [U]. **Research the specific platform at runtime**: ask the person which one the school uses and test what it emails or notifies. Fallbacks: forwarded notifications, screenshots, photos.
- **Paper calendars and notes:** a phone photo → any vision-capable AI → `.ics` file to import; the person spot-checks dates.
- **Family logistics:** a Telegram family group with a bot appending to an inbox file is safer than WhatsApp bridges [U].

### University
- **Calendar feeds work without admin rights** on the major LMSs:
  - **Moodle:** Calendar → Export → **"Get URL address"** → an iCal URL with an embedded token, all enrolled courses, no login needed [V]. The URL is a credential: don't share it.
  - **Brightspace:** Calendar → **Subscribe** (all, tasks only, or one course) [V].
  - **Blackboard:** **Share calendar** to iCal/Google/Outlook (all courses) [V].
  - **Canvas:** personal Calendar Feed [U]. **Google Classroom:** deadlines appear in the class Google Calendar [U].
- **Subscribe the feed from a *personal* calendar.** University Microsoft 365 or Google Workspace accounts may need **admin consent** for third-party apps: the student sees "Approval required" and can only file a request [V]; Gemini's custom MCP doesn't work on school accounts [S]. A personal calendar sidesteps the tenant, and the assistant's personal connector sees the deadlines.
- **Materials:** download manually or via the Moodle app's offline mode, then use NotebookLM, a Claude Project or similar. Check the course's AI policy and teachers' copyright.
- **Tech:** **moodle-dl** downloads files, assignments and events incrementally, only if the institution allows Moodle app access; its token is a secret [V]. **Canvas:** students can create tokens by default, but they **expire after 30 days** and admins can disable them [V]; **canvas-mcp** offers read-only student tools, runs locally [V]. Instructure states that inserting a token into an application "violates Canvas API policy", and universities tell students not to share tokens [V] — explain this; the person decides, ideally after checking their institution's rules.
- University mail: forward to a personal address if the institution allows it.

### Life admin
- **Email is the universal on-ramp:** receipts, bills, travel confirmations, delivery notices → one label or address → an automation saves body and attachments → AI files a note. TripIt-style travel parsing via forwarding [U]; Amazon "Request your data" takes days [U].
- **Google Photos:** since 31 Mar 2025 apps can read only photos the user picks (Picker API) or that the app created; no full-library read [V]. Use Takeout or phone-to-folder sync.
- **Google Maps Timeline:** stored on-device; export per device as JSON; no API [S].
- **Government portals** (Agenzia delle Entrate, INPS, AEAT, Seguridad Social and others): manual PDF/XML downloads behind SPID/CIE/Cl@ve logins [U]. **Research the specific portal at runtime.** Advice: keep those logins manual.
- **Home Assistant:** built-in MCP server for households already running it [U].

### Job search
- **Non-tech:** job alerts from LinkedIn, Indeed and company career pages → one email label → weekly AI shortlist scored against a profile file. Alert emails are the only sanctioned feed: LinkedIn's API is partner-only and scraping breaches terms [V]; Indeed's public jobs API is believed closed [U].
- **Tech:** automation turns each alert into a note; an application tracker (Notion or a Markdown table) plus drafted cover letters and interview prep. Published n8n templates cost a few dollars a month in model use [V, earlier research].
- **Pitfalls:** volume eats small free automation tiers quickly. Applications and messages stay human-sent by default.

---

## 4. Platform → method matrix

R = read, W = write. "Best start" is the rung to suggest first.

| Platform | Best start (non-tech) | Technical option | R/W | Watch out |
|---|---|---|---|---|
| Gmail | Assistant connector + labels | Gmail API, Apps Script, Workspace MCP (preview) | R/W | Attachments not read by Claude connector [V] |
| Outlook.com / M365 | Connector (Copilot read-only), rules | Graph API, automation tools | R/W | Work/school tenant consent |
| Google Calendar | Connector | API | R/W | — |
| iCloud Mail/Calendar | Share calendar link | IMAP/CalDAV + app password [U] | R/W | No REST API |
| Proton | Calendar share link | Bridge (paid, local) [U] | R/W | E2EE blocks cloud automation |
| WhatsApp personal | Export chat (.txt) | Unofficial bridges (ToS risk) | R | Ban risk |
| Telegram | Bot + automation tool | Bot API | R/W | Bot sees only its chats |
| Slack / Discord | Connector (Slack) | Bot APIs | R/W | Rate limits [U] |
| LinkedIn | Data archive; job-alert emails | EEA portability API [S] | R | No posting API |
| X | Manual posting | Pay-per-use API [S] | R/W | Costs per call |
| Instagram | Manual | Graph API (professional only) [S] | R/W | Personal: none |
| YouTube | Channel RSS | Data API (quota) [U] | R/W | Quota |
| Substack | RSS + CSV | MCP (Bestseller only) [S] | R | No publish API |
| beehiiv | UI | API (all plans), MCP (Lite+) [V] | R/W | Draft endpoint unverified |
| Notion | Connector | API, official MCP | R/W | Export not re-importable |
| Todoist / TickTick / MS To Do / Google Tasks | Email-to-task, Zapier/Make | Official APIs [U] | R/W | API changes |
| Things / Apple Reminders | Shortcuts, Mail to Things | URL scheme, AppleScript [U] | W | Local only |
| Drive / OneDrive / Dropbox | Sync folder, connectors | APIs, Drive MCP (preview) | R/W | Online-only placeholders |
| Kindle | Readwise or notebook/Clippings importers | Readwise API [U] | R | No Kindle API |
| Pocket | — (closed) | — | — | Migrate [V] |
| EU/UK bank | CSV/PDF export | Enable Banking restricted mode → Actual/Firefly [V] | R | Re-consent; no GoCardless for new users |
| US bank | CSV export | SimpleFIN Bridge [V] | R | 25 institutions |
| Wise | Statement download | Token (business accounts) [V] | R/W | Tokens can move money |
| Italy e-invoices | AdE download (XML) [V] | — | R | ~2-year retention |
| Apple Health | Health Auto Export → cloud folder [V] | REST/MQTT push | R | Premium for auto-export |
| Health Connect | Scheduled ZIP export [V] | — | R | No medical records |
| Oura | Data download | OAuth API (membership) [V] | R | Membership needed |
| Garmin | Sync to Apple Health/Health Connect | Program closed to new applicants [S] | R | — |
| FSE (IT) / Carpeta Ciudadana (ES) | PDF download [S] | — | R | PDFs, not data |
| Google Classroom (parent) | Guardian summary emails [V] | API (admin-dependent) [U] | R | No grades |
| ClasseViva & other registers | Notifications, screenshots | Unofficial client [U] | R | Research at runtime |
| Moodle | Calendar "Get URL address" [V] | moodle-dl [V] | R | URL is a credential |
| Canvas | Calendar feed [U] | Token (30 days) + canvas-mcp [V] | R | Token policy |
| Brightspace / Blackboard | Calendar subscribe/share [V] | APIs (not checked) | R | Refresh rate unknown |
| Google Photos | Takeout, phone sync | Picker API [V] | R | No full-library read |
| Government portals | Manual PDF/XML | — | R | Keep logins manual |

---

## 5. Region notes

- **Spain:** bank exports and Norma 43 [U]; Enable Banking for the technical path [V]. Health documents as PDFs via Mi Carpeta Ciudadana [S]; regional health apps not researched. Tax data from AEAT via Cl@ve [U]; no consumer e-invoice inbox like Italy's [U]. School platforms (Raíces, PASEN, iEduca…) are a research gap → runtime.
- **Italy:** best verified consumer finance source: AdE B2C e-invoice download, ~2-year retention [V]. Health via FSE 2.0 PDFs [S]. Registri elettronici: no confirmed export [U]. First country where Meta let rival AI chatbots back onto the WhatsApp Business API [S]. University portals (e.g., Esse3) not covered.
- **EU-wide:** PSD2 account-information access is read-only, with periodic re-consent [U]. EHDS structured health exchange 2029–2031 [V]. DMA gives EEA LinkedIn members a portability API [S] — a rare case where EU users get *more* access than US users. Some ChatGPT apps are unavailable in the EEA/UK/Switzerland depending on the partner [V]; Gemini connected apps "vary by location" [V].
- **UK:** most developer-friendly banks for individuals (Monzo, Starling [U]) plus Enable Banking. FCA removed 90-day re-authentication for account-information providers in 2022 [U]. NHS App export route not found: screenshots, printing or a Subject Access Request are presumed routes [U].
- **US:** the most native integration: ChatGPT and Claude health connections [V], SimpleFIN [V], YNAB/Lunch Money community MCP [S], Wise statements via API [V].

## 6. Not researched or unconfirmed (check live before relying on them)

- Bank-by-bank Enable Banking coverage in Spain and Italy; Enable Banking paid terms.
- WHOOP, Fitbit Web API, Withings, Polar, Samsung Health; Spanish regional health apps; NHS exports.
- Regional school platforms in Italy and Spain; ClassDojo, Seesaw, family organisers.
- Whether the EU 12-month WhatsApp arrangement changed after March 2026.
- X per-call prices; beehiiv draft creation; Substack MCP.
- Whether consumer Gmail accounts work with Google's Workspace MCP servers.

---

## Sources

- Claude Google Workspace connectors: https://support.claude.com/en/articles/10166901-use-google-workspace-connectors
- Claude custom connectors (remote MCP): https://support.claude.com/en/articles/11175166-getting-started-with-custom-connectors-using-remote-mcp
- Copilot connectors: https://support.microsoft.com/en-us/Microsoft-Copilot/connecting-microsoft-copilot-to-other-services
- Gemini apps: https://support.google.com/gemini/answer/13695044
- Google Workspace MCP servers: https://developers.google.com/workspace/guides/configure-mcp-servers
- Zapier pricing: https://zapier.com/pricing · Composio: https://composio.dev/pricing.md
- WhatsApp chatbot ban: https://respond.io/blog/whatsapp-general-purpose-chatbots-ban · AGCM: https://en.agcm.it/en/media/press-releases/2025/12/A576 · EU 12 months: https://storyboard18.com/brand-makers/meta-to-allow-rival-ai-chatbots-on-whatsapp-in-europe-for-12-months-amid-eu-probe-2-91405.htm
- Telegram Bot API: https://core.telegram.org/bots/api
- LinkedIn portability API (secondary): https://singhamandeep.com/linkedin-member-data-portability-api/ · LinkedIn restricted uses: https://learn.microsoft.com/en-us/linkedin/marketing/restricted-use-cases?view=li-lms-2023-06
- X pay-per-use: https://www.gigazine.net/gsc_news/en/20260209-x-api-pay-per-use/
- beehiiv pricing: https://www.beehiiv.com/pricing · Substack (secondary): https://smtpedia.com/platforms/substack/api/
- Pocket: https://support.mozilla.org/en-US/kb/future-of-pocket · Readwise → Obsidian: https://help.readwise.io/article/125-how-does-the-readwise-to-obsidian-export-integration-work
- Google Photos API changes: https://developers.google.com/photos/support/updates
- GoCardless closed: https://actualbudget.org/docs/advanced/bank-sync/gocardless/ · Actual bank sync: https://actualbudget.org/docs/advanced/bank-sync/ · Enable Banking in Firefly III: https://docs.firefly-iii.org/tutorials/data-importer/eb/
- SimpleFIN: https://beta-bridge.simplefin.org/ · Wise tokens: https://docs.wise.com/guides/developer/auth-and-security/personal-api-token
- Italy e-invoices: https://www.idealista.it/news/node/436881
- ChatGPT Health: https://help-lb.openai.com/en/articles/20001036-health-in-chatgpt · Claude health: https://anthropic.com/news/healthcare-life-sciences
- Health Connect export: https://support.google.com/android/answer/15323271 · Health Auto Export: https://apps.apple.com/it/app/health-auto-export-json-csv/id1115567069
- Oura API: https://support.ouraring.com/hc/en-us/articles/4415266939155-The-Oura-API · Garmin pause (secondary): https://tryterra.co/blog/garmin-connect-developer-program-pause
- EHDS: https://health.ec.europa.eu/ehealth-digital-health-and-care/european-health-data-space-regulation-ehds_en
- Google Classroom guardians: https://support.google.com/edu/classroom/answer/6388136
- Moodle calendar export: https://docs.moodle.org/en/Calendar_export · moodle-dl: https://pypi.org/project/moodle-dl
- Canvas tokens: https://community.instructure.com/en/kb/articles/662901-how-do-i-manage-api-access-tokens-in-my-user-account · canvas-mcp: https://github.com/vishalsachdev/canvas-mcp
- Brightspace subscribe: https://wur-student.screenstepslive.com/m/brightspace_help_students/l/1272052-how-to-subscribe-to-a-calendar · Blackboard: https://blackboard.niu.edu/blackboard/students/calendar-ultra.shtml
- Entra ID consent: https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/user-admin-consent-overview
