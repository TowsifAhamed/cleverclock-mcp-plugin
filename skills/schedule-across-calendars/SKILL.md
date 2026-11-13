---
name: schedule-across-calendars
description: Schedule a meeting while checking every linked Google and Outlook calendar for conflicts — find mutual free time, propose slots, create the event with a Meet or Teams link, and invite guests. Use when the user asks to book, schedule, move or find time for a meeting.
---

# Scheduling across all calendars

1. Confirm the essentials: length, rough window (this week? before Friday?), the user's time zone (ask if unknown; never assume UTC), working hours, and who should attend.
2. `find_free_time` with `duration_minutes`, `start`/`end`, `time_zone`, and `day_start_hour`/`day_end_hour`. It checks **all** linked calendars at once — work and personal. If the result has a `warning`, tell the user which account couldn't be read.
3. Offer 3 good options, spread across days, not three adjacent slots. Prefer slots with breathing room (`free_minutes` well above the meeting length) and avoid the first minutes after another meeting unless the user is fine with back-to-backs (`buffer_minutes` helps).
4. Ask which calendar/account the event belongs on (work events on the work account). `list_calendars` shows the options.
5. Before inviting anyone, confirm title, time and guest list — invitations email real people. Then `create_event` with `attendees`, `add_video_meeting: true` if it's remote, and a short agenda in `description`.
6. To reschedule: `list_events` (filter with `q`) → `update_event` with new `start`/`end`; guests are notified. To decline someone else's meeting use `respond_to_invite`, not `delete_event`.

Reply-by-email scheduling: if the request came in an email, draft the reply with the proposed times (`create_draft` with `reply_to_message_id`) instead of creating the event before they agree.
