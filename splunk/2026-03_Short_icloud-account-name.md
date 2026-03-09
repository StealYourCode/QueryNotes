## Q3 - [One line: what it finds]
**Tool:** Splunk
**Tags:** `icloud` `account` `identity`
**Author:** @handle · **Date:** 2026-03-09

**When to use:** When searching for logged Icloud Account

**Query:**
\```
index=logarchive sourcetype=logarchive_events
    category="icloud" action="account_activity"
| stats count by _time, icloud_account_name, device_id, event_type
| sort - _time
| table _time device_id icloud_account_name event_type count
\```

**Gotcha:** Only able to recover the account that were recently verify by a GS Token

---
<!-- Optional: key fields, story, expected output - add when you have time -->
