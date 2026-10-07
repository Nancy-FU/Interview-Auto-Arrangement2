---
name: interview-reply-check-and-book
description: Scheduled every 3 hours. Read candidate replies, check the interview calendar for conflicts, auto-book conflict-free slots and sync the tracker; draft (never send) a reschedule email when every requested slot is taken; escalate anything ambiguous.
---

# Reply check and booking (scheduled)

This runs unattended. Read `config.md` and `docs/RULES.md` first on every run; `RULES.md` wins on conflict. Scope = the tabs listed in `TRACKER_TABS`; new tabs are not discovered automatically.

Suggested schedule: `7 */3 * * *` (every 3 hours, off the hour).

## Each run
1. For each in-scope tab, find rows where `Status` is the "awaiting reply" value and `Date to IV` is empty. Ignore every other row.
2. For each row, search the mailbox for the candidate's reply to the invitation thread, and for a bounce (mailer-daemon) on that invitation.
   - Bounce found → list it under NEEDS HR and skip the candidate this run.
   - No reply → skip.
3. Reply found → read it in full and extract usable slot(s), checked against the window in the tab header:
   - Specific date + broad time word ("afternoon") inside the window → not ambiguous: any conflict-free slot that day inside the window is acceptable.
   - Several dates or times offered → all are candidates; take the first conflict-free one in the candidate's order of preference.
   - Cannot pin down even a date, or the candidate says nothing works → do not guess. List under NEEDS HR with the key quote.
   - Reply comes from a different address than the one on file (for example after a bounce) → treat the new address as correct; use it for the invite and update the tracker's Email cell. Mention it in the summary.
4. Check `INTERVIEW_CALENDAR_ID` for each candidate slot.
5. **All slots conflict** → draft (do not send) a short note asking the candidate to pick another time in the window. Put recipient, subject and full body under NEEDS HR so HR can approve with one word.
6. **Conflict-free slot found → BOOK** (pre-approved, no HR confirmation needed):
   - Create the event on the interview calendar: title `Interview: <Candidate> - <Role>`, duration `DEFAULT_DURATION_MIN`, Google Meet link.
   - Attendees: candidate (current email), interviewer from the tab header, `HR_EMAIL` as optional.
   - Before creating, check the calendar for an existing event for this candidate so nobody is booked twice.
   - Sync the tracker: `Date to IV` = booked date, `Status` = the "scheduled" value (commonly `Arranged`), fix Email if it changed. If the sheet cannot be reached (for example a login wall), skip the sync for that row only and say so in the summary.
   - Apply `ARRANGED_LABEL` to the whole invitation thread. Labelling is not sending, so it needs no approval.
7. **Summary**: replies processed, slots auto-booked, then a separate NEEDS HR section (ambiguous replies with quotes, conflict drafts, bounces). If nothing happened, one line only.

## Hard constraints
- Never send any email autonomously, including from a scheduled run.
- Never turn an ambiguous reply into a booking.
- A failed sheet sync never blocks the rest of the run.
- Never touch rows outside the "awaiting reply" status.
