# Flow card

Fill this in **before building** anything. It is the design of the flow. Save it as `_system/flows/<flow-name>/card.md` in every mode (in chat mode, give it as a file to save). The runbook's "Purpose and done" section summarizes it.

---

## Identity
- **Name:** (lowercase-with-hyphens, e.g., `morning-inbox-triage`)
- **One sentence:** "When ___ happens, ___ is done for me, so that ___."
- **Path:** light / standard / full

## The four labels
| Label | Answer |
|---|---|
| **What** moves | |
| **When** (schedule, event, or on demand; times in the owner's time zone — check what the scheduler uses) | |
| **Who** runs it (AI assistant, automation tool, script) and on which device | |
| **Checkpoint** (what the owner checks or approves; "none" is a valid choice) | |

## Places (by stable name from `places.md`)
- **From:** 
- **To:** 
- **Reads for context:** (profile, specific People files, project READMEs…)

## Inputs
| Input | Example | Trust level |
|---|---|---|
| | | trusted (written by the owner) / untrusted (emails, web, others' documents) |

## Output
- **Format:** (e.g., a Markdown file per day, a draft email, a calendar event, a row in a table)
- **Example of a good output:** (paste or describe one)

## Done means
How we'll know it works, in one or two checkable sentences (e.g., "every weekday by 07:00 there is a summary listing every new file in the inbox and where it went, with no file lost").

## Worth it?
- **How often:** 
- **Time or stress saved each time:** 
- **Rough value:** (e.g., 10 min/day ≈ 60 hours/year)

## Cost direction
- **Free / included in a plan / paid:** 
- **How cost grows** (per run, per item, per month): 
- **Estimate per month:** 

## Risks and choices
- **What happens if it goes wrong once?** 
- **Does it act outside the brain** (send, post, pay, share)? 
- **Sensitive data?** 
- **Owner's choices** (record them also in `AGENTS.md` section 5): 

## Dependencies
- **Needs these flows first:** 
- **Other flows that will use its output:** 
- **Shared files it writes, and who owns them:** 
