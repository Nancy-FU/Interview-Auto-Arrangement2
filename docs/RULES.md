# Rules (single source of truth)

Every skill reads this file first. Change a rule here, then update any skill that restates it.

## Scope
Automates interview coordination for teams without an ATS: CV intake → batch invitations → reply tracking → calendar conflict check → booking → tracker sync. Deciding who to interview stays with the hiring manager; onboarding and contracts are out of scope.

## Tracker format
One tracker per role, one tab per batch. Header rows carry the role, salary band, interviewer email and the offered availability window. Columns:

`No | Second round | Working Visa | Name | Available Date | Date to IV | CV | Status | 2nd Status | Contact | Email | Remark`

`Status` values are per-sheet dropdowns; check them before writing. Common set: `Emailed` (invited, awaiting reply), `Arranged` (scheduled), `Accept`, `Reject`, `Responded`.

## Decision rules
1. **Email is the source of truth for the chosen slot; the calendar is only for conflict checks.**
2. **Never guess.** If a reply cannot be pinned to at least a date, escalate to HR with the key quote.
3. **Date + broad time word inside the offered window is not ambiguous.** Book any conflict-free slot that day inside the window.
4. **Multiple options:** if one conflicts, use the next. Draft a reschedule email only when all options conflict.
5. **Latest contact wins.** If a candidate replies from a new address (for example after a bounce), use it from then on.
6. **Check before writing.** Update only the cells that need changing; never clear and rebuild a tracker.
7. **Check for duplicates before booking** so nobody is booked twice.
8. **Default duration 45 minutes.** Candidate and interviewer are guests; HR is an optional guest.

## Approval rules
- **Every outbound email needs HR's explicit approval in the live chat.** Batch invitations: one approval per batch. Reschedule and rejection emails: approved as a batch, never auto-sent. No exemption for scheduled runs.
- **Pre-approved without asking:** creating calendar events, syncing the tracker, applying the "arranged" label to a thread.

## Known technical limits
- Attachments larger than about 100 KB cannot be reliably base64-inserted. Create drafts without the attachment; HR attaches and sends.
- Browser-based spreadsheet editing: double-click a cell before typing; choose dropdown values from the list. If a login wall appears, skip that row's sync and report it.

## Second round
Trigger: `Second round = Yes` and `2nd Status` empty. In-person: no Meet link, set the location. Track in `2nd Status`; leave `Status` alone. The application form comes from the company folder HR annotated; never guess the company.
