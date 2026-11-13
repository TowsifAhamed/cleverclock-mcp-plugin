---
name: outreach-follow-ups
description: Find outreach emails nobody has answered across all linked mailboxes and prepare polite, specific follow-ups. Use when the user asks who hasn't replied, what needs chasing, or to follow up on pitches, applications or intros.
---

# Following up on unanswered outreach

1. `list_awaiting_replies` (default window: sent 3–30 days ago; widen with `newer_than_days` if the user is chasing older threads).
2. Drop what shouldn't be chased: automated addresses (no-reply, notifications, support desks), threads the user closed themselves, and anything where `follow_ups_already_sent` is already 2+ unless the user insists.
3. Present the rest grouped by urgency (`days_waiting`), one line each: who, subject, sent when, how many nudges so far.
4. For each one the user wants to chase: `read_thread`, then `create_draft` replying in the thread (`reply_to_message_id` = `last_message_id`). A good follow-up is 2–4 sentences, references the original ask, adds something new (a result, a link, a simpler ask), and makes replying easy. Second follow-ups should be shorter than the first.
5. Show the drafts; send each only after approval with `send_draft`.
6. Keep the pipeline current: `save_outreach_contact` (or `update_outreach_contact`) with `stage: "follow_up_due"` → `"contacted"`, `last_contacted_at`, a `next_follow_up_at` about a week out, and `add_thread` so the thread is one click away next time.
