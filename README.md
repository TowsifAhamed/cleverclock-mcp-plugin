# CleverClock for Claude

**One login. Every inbox and calendar you have.**

AI assistants usually connect to a single Google account. CleverClock connects
your assistant to *all* of them at once: personal Gmail, work Google
Workspace, Outlook, Microsoft 365. Ask one question and it searches every
inbox, checks every calendar, and acts in the right account.

<p align="center"><img src="assets/logo.png" width="96" alt="CleverClock"></p>

Works in **Claude** (web, desktop, mobile), **Claude Cowork** and **Claude Code**.
The server is hosted by CleverClock, so there is nothing to install or run.

## What you can ask

- **"What needs my attention in my inboxes today?"** Unread mail across every account, sorted into what needs you, what's FYI and what's noise, with replies drafted.
- **"Find 45 minutes with Priya next week."** Free time checked against your work *and* personal calendars together, then an invite with a Meet or Teams link.
- **"Who hasn't replied to my outreach?"** Sent threads where you spoke last, how long they've waited, and polite follow-ups drafted in-thread.
- **"Track my job applications."** Applications, recruiter emails and interviews pulled from every inbox into one pipeline, with follow-up dates.
- **"Any collaboration or partnership requests I missed?"** Opportunities hiding in old or archived mail, ranked and tracked.
- **"How did I spend my time this week?"** CleverClock's meeting-load, focus-time and people insights, plus concrete recommendations.

## What's included

| Area | Tools |
| --- | --- |
| Accounts | `list_accounts`, `connect_account`, `get_connect_link_status`, `disconnect_account`, `get_my_profile` |
| Mail (all accounts) | `search_mail`, `read_email`, `read_thread`, `list_drafts`, `create_draft`, `send_draft`, `send_email`, `delete_draft`, `organize_emails`, `list_awaiting_replies` |
| Calendar (all accounts) | `list_calendars`, `list_events`, `get_event`, `find_free_time`, `create_event`, `update_event`, `delete_event`, `respond_to_invite` |
| Outreach tracker | `list_outreach`, `save_outreach_contact`, `update_outreach_contact`, `delete_outreach_contact` |
| CleverClock insights | `get_time_insights`, `get_people_insights`, `get_time_by_project`, `list_projects`, `list_recommendations`, `set_recommendation_status`, `ask_cleverclock`, `get_usage` |
| Support | `submit_report`, `list_connected_apps`, `revoke_connected_app` |

Skills bundled with the plugin teach Claude good playbooks for these tools:
`inbox-triage`, `schedule-across-calendars`, `outreach-follow-ups`,
`job-hunt-pipeline`, `find-opportunities` and `weekly-time-review`.

## Install

From the Claude plugin directory, once listed:

```
/plugin install cleverclock
```

Or add the connector directly. In **Claude** go to *Settings → Connectors → Add custom connector* and use:

```
https://cleverclock-mcp.daamdekhi.com/mcp
```

In **Claude Code**:

```bash
claude mcp add --transport http cleverclock https://cleverclock-mcp.daamdekhi.com/mcp
```

To try this plugin from source:

```bash
git clone https://github.com/TowsifAhamed/cleverclock-mcp-plugin
claude --plugin-dir ./cleverclock-mcp-plugin
```

## Getting started

1. Create a CleverClock account at <https://assistaudit.daamdekhi.com>.
2. Install the plugin or add the connector. The first time Claude uses it, you sign in to CleverClock and approve the connection (standard OAuth 2.1 with PKCE; your password never reaches Claude).
3. Ask Claude to *"connect my work Outlook"* or *"add my other Gmail"*. It gives you a one-time link; you confirm with your CleverClock password and sign in to the account in your browser. Repeat for every account.

## Safety by design

- **You stay in control of anything that reaches people.** Claude drafts first; sending mail and inviting guests happen when you say so. Sending has recipient caps and hourly limits, so a runaway loop can't spam your contacts.
- **Nothing is ever deleted from your mailbox.** Organizing means read/unread, archive and star only.
- **Ids can't be mixed up.** Every message, thread and event id is encrypted and bound to its account, so an action can't land in the wrong mailbox.
- **Tokens stay with CleverClock.** Claude only ever receives a revocable access token for your CleverClock account. Revoke it any time with `revoke_connected_app` or in the CleverClock app, and unlink any mailbox with `disconnect_account`.
- **No billing data in chats.** Plans and prices are never returned by any tool; `get_usage` shows only remaining allowances.

## Prefer to self-host?

[Open Calendar](https://github.com/TowsifAhamed/open-calendar) is our free,
open-source, self-hosted bridge for connecting multiple Gmail, Google
Calendar, Outlook and Teams accounts to your own assistant. CleverClock is the
hosted version, with sending, follow-up tracking, the outreach pipeline and
time insights built in.

## Links

- Product: <https://assistaudit.daamdekhi.com>
- Privacy: <https://assistaudit.daamdekhi.com/privacy>
- Terms: <https://assistaudit.daamdekhi.com/terms>
- Support and security: **support@daamdekhi.com**, or ask Claude to `submit_report`

## License

MIT, see [LICENSE](LICENSE). This repository contains the plugin
configuration and skills only; the CleverClock service is operated by
CleverClock.
