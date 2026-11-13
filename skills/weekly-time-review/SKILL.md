---
name: weekly-time-review
description: Review where the user's time went and plan the week ahead — CleverClock time insights, recommendations, upcoming meetings across every calendar, and focus time to protect. Use for a weekly review, "how was my week", or "plan my week".
---

# Weekly time review

1. `get_time_insights` with `period_type: "week"` — meeting load, focus time, back-to-backs, top people and categories, change vs last week.
2. `list_recommendations` — CleverClock's concrete suggestions (shorten, decline, batch, delegate, protect focus). Pick the 2–3 with the biggest time saved.
3. `list_events` for the coming week across all accounts. Flag: days with no focus block, back-to-back runs, double-bookings between accounts, meetings the user hasn't responded to (`my_response: "needsAction"`).
4. Propose a plan: which invites to answer (`respond_to_invite`), which meetings to move (`update_event`), and focus blocks to add (`create_event` on the right calendar, no attendees). Make changes only after the user agrees, and confirm before touching meetings other people are in.
5. Record recommendations the user acts on with `set_recommendation_status` so CleverClock learns what works for them.

Insights cover the calendar connected in the CleverClock app; live calendar tools cover every linked account.
