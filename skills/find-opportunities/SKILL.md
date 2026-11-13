---
name: find-opportunities
description: Scan every linked inbox for collaboration, partnership, speaking, press, investment or sales opportunities that slipped through, rank them, and track the good ones. Use when the user asks for collaboration opportunities, leads, partnership requests or "what did I miss".
---

# Finding opportunities hiding in the inbox

1. Ask (or infer from context) what counts as an opportunity for this user: collaborations, partnerships, sponsorships, speaking/podcast invites, press, investors, customers.
2. `search_mail` across all accounts over the last 30–90 days with targeted queries, e.g. `collaborat* OR partnership OR "work together"`, `podcast OR "speaking" OR panel OR conference`, `sponsor* OR "brand deal"`, `investor OR "intro" OR "would love to chat"`, `pricing OR quote OR demo OR "interested in"`. Include `folder: "all"` so archived mail counts.
3. Filter out cold spam and mass marketing: read the thread (`read_thread`) for anything promising before judging it.
4. Rank by fit and freshness. For each, one line: who, what they propose, when, and whether the user ever replied.
5. Track the ones the user wants to pursue: `save_outreach_contact` with the right `pipeline` (`collaboration`, `partnership`, `investor`, `sales`, `networking`), `stage: "to_contact"` or `"in_conversation"`, and `add_thread`.
6. Offer reply drafts (`create_draft` in-thread) and, where a call makes sense, proposed times from `find_free_time`.
