---
name: inbox-triage
description: Triage unread mail across every linked Gmail and Outlook inbox at once — surface what needs the user, draft replies, and tidy the rest. Use when the user asks to go through their inbox, catch up on email, or find what needs a reply.
---

# Inbox triage across all accounts

1. `list_accounts` — note which accounts can read, draft, send and organize mail. Mention any account that is missing a permission instead of silently skipping it.
2. `search_mail` with `unread_only: true` and `folder: "inbox"` (add `after` = 3–7 days ago unless the user says otherwise). One call covers every account.
3. Sort what you find into:
   - **Needs the user** — a real person asking a question, a decision, a deadline, a meeting request.
   - **FYI** — updates worth one line.
   - **Noise** — newsletters, notifications, receipts.
4. For each "needs the user" item, `read_thread` before saying anything about it. Summarise in one or two lines: who, what they need, by when.
5. Offer to draft replies. Use `create_draft` with `reply_to_message_id` (the account is inferred). Write in the user's voice, short, and never invent facts, dates or commitments — ask.
6. Send only after the user approves each draft (`send_draft`). Never batch-send.
7. Offer to tidy: `organize_emails` with `mark_read` or `archive` for the noise the user agrees to. Archive is reversible; nothing is deleted.

Mail is private: summarise, don't paste whole messages back unless asked.
