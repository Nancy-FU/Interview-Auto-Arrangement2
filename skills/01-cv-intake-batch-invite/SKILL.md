---
name: cv-intake-batch-invite
description: Read shortlisted CVs, fill the candidate tracker, and draft one batch of interview invitations for HR to approve in a single step. Use when HR says "process this batch of CVs".
---

# CV intake and batch invitation

Read `config.md` and `docs/RULES.md` first. If they conflict with this file, `RULES.md` wins.

## Trigger
Manual only. HR names the shortlist folder **and** the tracker tab to use. Never guess the role or the tab.

## Steps
1. List the CVs in the shortlist folder. Every CV there is already approved for interview; do not re-screen.
2. For each CV, extract Name, Contact number, Email, and a one-line summary (degree and school, GPA if stated, most relevant experience). Write them into the tracker tab.
   - Check what is already in the tab first. Only fill empty cells; never clear and rebuild.
   - Leave `Status` empty until the invitation is sent.
3. Read the tab's header rows for the interviewer email and the offered availability window (dates and time range).
4. Draft one invitation per candidate using the fixed-slot template: state the window, ask the candidate to confirm a time inside it. Do not ask open-ended "when are you free".
5. Show HR the whole batch as one list: recipient, subject, date window, any missing data.
6. Send only after HR explicitly approves the batch in chat ("send all"). Then set each row's `Status` to the "invited, awaiting reply" value (check the tab's dropdown; commonly `Emailed`).

## Guardrails
- Sending email always requires HR's explicit approval in the live chat. One approval covers one batch, never future batches.
- If a CV lacks an email address, list it as missing; do not invent one.
- Check the Status dropdown values per tab before writing; they can differ between sheets.
- Spreadsheet edits through a browser: double-click a cell before typing; pick dropdown values from the list rather than typing.
