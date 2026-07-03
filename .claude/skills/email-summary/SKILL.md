---
name: email-summary
description: >-
  Generate Shu Yi's email summary / "Email Reply Digest" — the emails that still
  genuinely need HER reply, each with a ready-to-paste draft. Use when the user
  asks for their email summary, email digest, reply digest, "summarise my emails",
  "what emails do I need to reply to", inbox triage, "who am I waiting on", or to
  catch up on outstanding client/prospect replies. Works over the connected Outlook
  mailbox shuyi@thestrengthsco.com (The Strengths Co — a CliftonStrengths
  coaching/workshop consultancy).
---

# Email Summary (Reply Digest)

Produce a tight, skimmable digest of the emails Shu Yi still needs to reply to,
each with a ready-to-paste draft. Deliver it **in chat** — do NOT create a file
unless the user explicitly asks for one.

## Connector

Use the connected Outlook tools: `outlook_email_search`, `outlook_calendar_search`,
`read_resource`, `get_me` (Microsoft 365 MCP server). The mailbox is
**shuyi@thestrengthsco.com**. Note the mailbox also receives mail addressed to
**info@thestrengthsco.com** (website enquiries).

If the Outlook connector is not available in this run, say so plainly and stop —
do not fabricate a digest. (Scheduled/headless runs may lack interactively-
authenticated connectors; the fix is to reconnect Microsoft 365.)

## Steps

1. **Pull the inbox.** Search `folderName: "Inbox"`, `afterDateTime` = 5 days ago,
   `order: "newest"`, and **page through ALL results** (keep fetching with
   increasing `offset` until you've covered `totalResultCount`).

2. **Keep only what genuinely needs my reply:**
   - (a) Direct asks / questions / requests addressed to me, and
   - (b) client, prospect, or coaching/workshop threads.
   - IGNORE newsletters, marketing, and automated notifications — e.g. Circle.so,
     Dan/Key Person of Influence, HBR, Substack, IDEO U, Zoom, Eventbrite, CPF,
     DBS/OCBC/notify, ACRA/postman.gov, Pearson VUE, Gallup exports, TidyCal
     reminders, calendar auto-confirmations, and brizy **auto-acknowledgements**.
   - New inbound website enquiries (via `notifications@brizy.cloud`) that I have
     **not** replied to are **high priority**.

3. **Remove already-answered threads.** Search `folderName: "Sent Items"`, last
   ~7 days (a little wider than the inbox window to reliably catch my replies).
   **Drop any thread where my most recent message is the latest** in the
   conversation (ball is in their court). Keep only threads where the **other
   person's message is the latest** and needs a response from me. This is the most
   important filter — Shu Yi is usually on top of her inbox, so most active client
   threads are already handled and belong in "Already handled", not "Needs reply".

4. **Read full bodies.** For each email that survives, `read_resource` the full
   body so the draft is accurate (don't draft from the preview snippet alone).

5. **Calendar check (do this BEFORE drafting any date-specific reply).** Whenever a
   client/prospect proposes or references a specific date (workshop, session, call),
   check `outlook_calendar_search` for that date. Interpreting the calendar:
   - **Workshop / course / client-delivery blocks and named Learning programs
     (e.g. "Power to Train", "Development by Design") = REAL conflicts.**
   - **Family and Self-Care blocks (even if marked "busy") = FLEXIBLE** — do NOT
     treat as conflicts.
   - **Ambiguous all-day "Client Work / Meetings" blocks marked `free`** = don't
     assume; flag them and note I should confirm.
   - If a requested date is a real conflict, **FLAG it clearly** and write the draft
     to **ask about their flexibility** rather than confirming. Also surface a few
     genuinely open weekdays near their date **for my reference** (keep the client-
     facing draft asking about flexibility rather than naming those dates, unless
     they fit naturally).

## Output (in chat — tight and skimmable)

Address Shu Yi directly as **"you"/"your"** throughout the digest — she's the one
reading it. Never refer to her in the third person (not "Shu Yi sent a proposal",
say "you sent a proposal"). Third person is fine only *inside a draft reply*,
where "Shu Yi" is the signer writing to someone else.

- **Bottom line:** one line — how many truly need a reply; note if the inbox is
  mostly noise.
- **🔴 Needs a reply — act today:** highest priority (unanswered leads/client asks).
  For each: sender, company, email, how long it's been sitting, what they're asking,
  any calendar conflict, why it matters, and a ready-to-paste **draft reply**.
- **🟡 Optional — lower urgency:** nice-to-reply items (e.g. warm leads gone quiet →
  a follow-up nudge; community favours).
- **✅ Already handled — no action:** brief list of active client threads you've
  already replied to (so you know they were checked), noting who you're waiting on.

## Draft voice

Warm, concise, professional. Greet **"Hi [First name],"**. For enquiries: thank
them, note the fit, and propose a short call to scope the program and firm up a
proposal (offer to send a Teams invite). Sign off **"Shu Yi"** with the full
signature:

> Shu Yi Goh
> Founder and Principal Consultant
> The Strengths Co
> Harmony | Responsibility | Futuristic | Empathy | Focus
> E: shuyi@thestrengthsco.com
> P: +65 94779865
> W: www.thestrengthsco.com

## Notes

- A daily version of this runs as a scheduled routine ("Daily Email Reply Digest",
  8:00 AM SGT, push notification). This skill is the same workflow on demand.
- Keep the output in chat by default. Only write a file if the user explicitly asks.
