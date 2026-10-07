---
name: reject-letter-drafting
description: Draft rejection emails from a template for every candidate whose Status or 2nd Status turns Reject, and present them to HR as one batch for approval. Never sends on its own.
---

# Rejection letter drafting

## Trigger
A tracker row's `Status` or `2nd Status` becomes `Reject` and no rejection has been sent yet.

## Steps
1. Open the template at `REJECT_TEMPLATE_DOC_ID`.
2. Fill the blanks: position title (from the tab header), candidate name, company name (from HR's company annotation; never guess), sender name.
3. Create one Gmail draft per candidate, as a reply on the candidate's existing invitation thread where one exists.
4. List all drafts for HR in one message: recipient, subject, first line of the body.
5. Send only when HR approves the batch in chat. Approving one batch never approves future batches.

## Guardrails
- No automatic sending, even after the template has been used before.
- If a candidate withdrew on their own, write a short acknowledgement instead of a rejection.
- Attachments, if any, follow the no-attachment-draft rule in skill 03.
