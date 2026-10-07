# Interview Auto Arrangement

An interview-coordination agent for teams with no ATS. It runs on Claude with Gmail, Google Calendar and Google Drive connectors. The team keeps its existing tools: the hiring manager still screens CVs in a Drive folder, and HR keeps a spreadsheet tracker.

The agent takes over the rule-based coordination work: candidate records, batch invitations, reply tracking, calendar conflict checks, booking and tracker sync. Screening decisions and every outbound email stay with people.

## Results from the pilot
| | Manual | Agent |
|---|---|---|
| CV → invite sent (median) | 5.5 days | 19 hours |
| HR time per candidate | ≈37 min | ≈6 min |
| Hiring manager's shortlist rate | 34% | 58% |
| Double bookings | — | 0 |

Full data and method are in [`case-study/`](case-study/README.md).

## Skills
Each skill is a self-contained prompt (`SKILL.md`) for one job. Install them as Claude Code skills or scheduled tasks.

| Skill | When it runs | What it does | Sends email? |
|---|---|---|---|
| [`01-cv-intake-batch-invite`](skills/01-cv-intake-batch-invite/SKILL.md) | HR asks: "process this batch" | Reads shortlisted CVs, fills the tracker, drafts one batch of invitations | Only after HR approves the batch |
| [`02-reply-check-and-book`](skills/02-reply-check-and-book/SKILL.md) | Every 3 hours (scheduled) | Reads replies, checks conflicts, books events with a Meet link, syncs the tracker, escalates edge cases | Never; drafts only |
| [`03-second-round-invite`](skills/03-second-round-invite/SKILL.md) | HR asks for next-round interviews | In-person invitations, attachment-free drafts, books with a location, tracks `2nd Status` | Only after HR approves |
| [`04-reject-letter-drafting`](skills/04-reject-letter-drafting/SKILL.md) | A row turns `Reject` | Fills the rejection template and batches drafts for HR | Only after HR approves the batch |
| [`05-case-study-from-jd`](skills/05-case-study-from-jd/SKILL.md) | A JD is pasted | Turns the measured results into resume bullets or an interview story | No |

## Setup
1. Copy `config.example.md` to `config.md` and fill in your own IDs and addresses. `config.md` is git-ignored.
2. Connect Gmail, Google Calendar and Google Drive to Claude.
3. Install the skills. For skill 02, create a scheduled task (for example `7 */3 * * *`) whose prompt is the contents of its `SKILL.md`.
4. Keep [`docs/RULES.md`](docs/RULES.md) as the single source of truth. When you change a rule, update the skills that restate it.

## Design principles
- **People approve every outbound email.** Scheduled runs only draft.
- **Escalate instead of guessing.** Ambiguous replies go to HR with the key quote.
- **No migration.** Gmail, Drive, Calendar and the existing spreadsheet stay as they are.
