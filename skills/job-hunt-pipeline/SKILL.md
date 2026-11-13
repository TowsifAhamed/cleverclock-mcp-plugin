---
name: job-hunt-pipeline
description: Run a job search from the user's mailboxes and calendars — find applications, recruiter messages and interviews across all accounts, keep a pipeline of every opportunity, schedule interviews and prepare follow-ups. Use when the user is job hunting or asks about applications, recruiters or interviews.
---

# Job hunt pipeline

## Build the pipeline
1. `list_outreach` with `pipeline: "job"` to see what's already tracked.
2. `search_mail` across all accounts for the last 60 days with queries such as `application OR applied OR "thank you for applying"`, `recruiter OR "talent acquisition" OR opportunity`, `interview OR "next steps" OR "phone screen" OR assessment`, and offers/rejections (`offer OR "unfortunately" OR "not moving forward"`).
3. For each real opportunity, `save_outreach_contact` with `pipeline: "job"`, the company as `organization`, the role as `title`, the recruiter as contact, the right `stage` (`contacted` = applied, `in_conversation`, `meeting_scheduled` = interview booked, `won` = offer, `lost` = rejected) and `add_thread`. It upserts by email, so re-running is safe.

## Keep it moving
4. `list_events` for the next two weeks with `q: "interview"` (and company names) — make sure every interview is on a calendar and linked to its pipeline item (`stage: "meeting_scheduled"`).
5. When a recruiter offers times, `find_free_time` across all calendars and draft a reply proposing slots.
6. `list_awaiting_replies` → nudge applications with no response after ~7 working days (see outreach-follow-ups).
7. Summarise for the user: active processes by stage, what's waiting on them, what's waiting on the company, and today's follow-ups (`list_outreach` with `follow_up_due_by: "today"`).

Never send an application or a reply to a recruiter without the user's explicit approval of the text.
