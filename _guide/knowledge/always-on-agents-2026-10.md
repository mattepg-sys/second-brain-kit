# Always-on agents: a second brain that runs 24/7 (October 2026)

> The most powerful "who runs it" option: an AI agent that lives on a computer that is **always on** (a home server or a rented VPS), reachable from the phone, running scheduled flows and answering messages while the owner's laptop is off.
> **For technical people.** Offer it only when the person asks for it, or when they are technical and want flows that the simpler options can't run. It is never needed to have a good second brain.
> Facts checked in October 2026 (official Hermes Agent documentation and providers' pages). Tools and prices change quickly: verify before recommending.

---

## 1. The three levels of "who runs it"

| Level | Example | Runs with the computer off? | Effort | Typical cost |
|---|---|---|---|---|
| 1. AI app | Claude or ChatGPT with the folder connected; their cloud scheduled tasks | No, or only limited cloud tasks | Low | Included in the plan |
| 2. Cloud script for one job | Telegram + Google Apps Script (`recipes/telegram-voice-bot.md`); Zapier/Make/n8n cloud | Yes, for that job | Medium | Free to a few €/month |
| 3. Always-on agent | Hermes Agent (or a custom agent built with a framework such as Mastra) on a home server or VPS | Yes, for everything | High | Server 0–25 €/month + model usage |

Level 3 makes sense when the person wants **many** flows to run unattended, wants to **talk to the brain from the phone** (ask, capture, get summaries), and is comfortable with a terminal, SSH and basic server security. Real users (October 2026) reported it is powerful but needs time to set up "in a structured way", and that model usage can push even a 100 €/month plan to its limits.

## 2. The building blocks

1. **An always-on machine.**
   - **Home server:** an old laptop, a mini PC, a NAS. No monthly fee; data stays at home. Must stay on and online; power or network cuts stop it; remote access needs a secure tunnel (e.g., Tailscale), never an open port.
   - **VPS** (Virtual Private Server): a virtual computer rented in a data center, always on. Examples: Hostinger (one-click Hermes Docker template), Hetzner, DigitalOcean (Hermes in its marketplace), Railway (one-click template). Prices seen in October 2026: Hostinger KVM 2 (2 vCPU, 8 GB RAM, 100 GB) about $10/month the first year with a 1-year commitment, about $17–24/month after; small Hetzner servers start lower. Watch the **renewal price**, not only the promo.
2. **The agent.** Hermes Agent by Nous Research (MIT license, free software): persistent memory, skills it can create and improve, scheduled tasks in plain language, a messaging gateway (Telegram, WhatsApp, Slack, Signal, email and many others), MCP connectors, browser automation, voice transcription. Desktop apps for macOS, Windows and Linux (since June 2026), a terminal version, and server installs. Alternatives: frameworks for developers (Mastra in TypeScript and others) to build a custom agent.
3. **A model to think with.** One of: the agent vendor's subscription (Nous Portal: free pay-as-you-go, $20, $100, $200/month tiers in October 2026); the person's own API keys (Anthropic, OpenAI, OpenRouter…: pay per use); or, for some providers, logging in with an existing subscription (e.g., Hermes can use a ChatGPT/Codex subscription through OpenAI's login). **Check each provider's terms** before using a consumer subscription inside a third-party agent: some allow it, some don't (for Claude, use an API key unless Anthropic's current terms say otherwise).
4. **The brain where both the laptop and the server can reach it.** Usually a **private Git repository** (GitHub, GitLab): the laptop and the server each have a copy and sync with `pull`/`push`. A cloud drive mounted on a server is fragile, and Hermes skips context files that take more than 5 seconds to read (slow network drives).

## 3. How Hermes fits this kit (checked in its documentation)

| Kit piece | Hermes behavior | What to do |
|---|---|---|
| `AGENTS.md` (brain rules) | Loaded from the **working directory** at session start. Only one project file is loaded, first match wins: `.hermes.md`, `AGENTS.override.md`, `AGENTS.md`, `CLAUDE.md`, `.cursorrules`. Inside a Git repo, `AGENTS.md` files from the repo root down to the working directory are chained; subfolder `AGENTS.md` files load when the agent works there | Run Hermes **with the brain's root as working directory**: `terminal.cwd` in `~/.hermes/config.yaml` for the gateway and scheduled jobs; `--workdir` for each scheduled job. **Don't create `.hermes.md`** in the brain: it would replace `AGENTS.md` |
| Flow runbooks `_system/flows/<flow>/SKILL.md` | Hermes skills are folders with a `SKILL.md` (frontmatter `name` + `description`), compatible with the agentskills.io standard — the same shape as this kit's runbooks | Add the brain's flows folder to `skills.external_dirs` in `config.yaml`, then attach the flow's skill to its scheduled job (`--skill <flow-name>`) |
| Learning is proposed, then approved (`AGENTS.md` rule 9) | Hermes can **edit skills by itself** (`skill_manage`) and writes its own memory | Set `skills.write_approval: true` (skill edits wait for `/skills approve`), and `skills.create_dir` to a folder outside the brain for skills the agent invents. Optionally `memory.write_approval: true` |
| `_system/profile.md` (who the owner is) | Hermes keeps a small `USER.md` and `MEMORY.md` in `~/.hermes/memories/` (about 1,400 and 2,200 characters) | Keep the truth in the brain. In `USER.md`, a line such as "Full profile: `_system/profile.md` in the brain" is enough |
| Identity and tone | `~/.hermes/SOUL.md` (never in the project) | Optional: the owner's preferred tone and language |
| Scheduled flows | `hermes cron create "<when>" "<prompt>" --skill <flow> --workdir <brain path>`; each run starts fresh (like the kit's scheduler prompt); results go to the chat set with `/sethome` | Use the flow's scheduler prompt as the job prompt. The gateway must be running (it runs the scheduler) |
| Logs and backlog | Not automatic | The runbook's "After the run" section already says to append to `_system/logs/` and `BACKLOG.md`; keep it |
| Secrets | `~/.hermes/.env`, set with `hermes config set` | Never in the brain repository; never pasted in chat |
| Time zone | `HERMES_TIMEZONE` | Set it to the owner's time zone |

## 4. Risks and the advice that goes with them

- **The agent can run commands on the machine.** The default terminal backend (`local`) has no isolation. Options: run Hermes in Docker (the container is the boundary), keep command approval on, answer approvals with "session" rather than "always", and give the agent only the credentials it needs.
- **Who can talk to it.** The gateway denies unknown users by default. Keep it that way: allowlist the owner's ID (`TELEGRAM_ALLOWED_USERS`) or use DM pairing. **Never** set `GATEWAY_ALLOW_ALL_USERS` on a bot that can run commands.
- **Untrusted content** (emails, web pages, forwarded messages) can contain instructions: the kit's rule 6 applies to the agent too.
- **Self-improvement drifts.** Skills and memory edited by the agent need review (users reported many corrections in the first weeks). Write approvals and the kit's health check help.
- **Backups.** The brain is in Git (history = backup). Back up `~/.hermes/` too (config, memory, skills), without the `.env` secrets in any shared place.
- **Costs.** Model usage is the main cost and grows with every scheduled job and long conversation. Start with few jobs, check usage (`/usage`, `/insights`), use cheaper models for simple jobs.
- **Server security** (VPS): SSH keys instead of passwords, firewall, automatic updates. Confusing the Docker container's terminal with the server's terminal is a common mistake.
- **Sync conflicts:** each flow runs on **one** machine (the "Who runs it" column), and the laptop pulls before working and pushes after.

## Sources (October 2026)
- Hermes Agent documentation: context files, files overview, skills, scheduled tasks, messaging gateway, configuration, tips — hermes-agent.nousresearch.com/docs
- "What is Hermes Agent" (Dupple), Hermes desktop app coverage (Decrypt), VPS + Telegram setup guide (MindStudio)
- Hostinger Hermes Agent VPS page; VPSBenchmarks (Hostinger KVM 2 pricing); OpenAI Codex pricing overview (Jetadmin)
