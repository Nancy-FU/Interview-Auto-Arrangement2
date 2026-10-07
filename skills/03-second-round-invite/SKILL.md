---
name: second-round-invite
description: Invite candidates marked for a later in-person round, book the slot once they confirm, and track progress in a separate 2nd Status column. Use when HR asks to arrange next-round interviews.
---

# Second-round (in-person) invitation

Same shape as skills 01 + 02, with these differences.

## Trigger
A tracker row has `Second round = Yes` **and** `2nd Status` is empty. Do not require the round-1 `Status` to say `Accept`; HR often marks the next round before updating round 1. If the tab has no `2nd Status` column yet, stop and ask HR to add it.

## Steps
1. Get the candidate slots and the interviewer for this round from HR. If either is missing, stop and ask; do not reuse round-1 values.
2. Draft the invitation: fixed date/time options, `ONSITE_ADDRESS` with the nearest transit stop, and a note that the application form is attached.
3. **Attachments:** create the email as a Gmail **draft without the attachment**. HR attaches the form manually and sends. Base64-inserting files larger than about 100 KB is unreliable and can corrupt the file, so do not attempt it.
4. Which company's application form to use: take it from HR's annotation in the tracker and pick the file from that company's subfolder in `APPLICATION_FORM_FOLDER`. Never guess the company.
5. When the candidate confirms, check conflicts exactly as in skill 02. Book the event **without** a Meet link, with `location` set to `ONSITE_ADDRESS`.
6. Update `2nd Status` only; leave the round-1 `Status` untouched.

## Guardrails
- Sending is always HR's explicit decision.
- Ambiguous or all-conflict replies go to NEEDS HR, as in skill 02.
