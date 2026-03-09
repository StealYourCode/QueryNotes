# iCloud Account Name Lookup

## Summary
Extracts and deduplicates iCloud account names from logarchive events to identify which Apple ID was active on a device during a given timeframe.

## When to Use
Use this when you need to confirm which iCloud account was signed in at the time of an event, or when cross-referencing device activity with a known Apple ID.

## Query

```splunk
index=logarchive sourcetype=logarchive_events
    category="icloud" action="account_activity"
| stats count by _time, icloud_account_name, device_id, event_type
| sort - _time
| table _time device_id icloud_account_name event_type count
```

## Key Fields

| Field | Description | Example Value |
|-------|-------------|---------------|
| `icloud_account_name` | The Apple ID / iCloud email associated with the event | `john.doe@icloud.com` |
| `device_id` | Unique identifier of the device | `ABCD1234EFGH5678` |
| `event_type` | Type of iCloud account event observed | `sign_in`, `sign_out`, `token_refresh` |
| `category` | Log category — filter on `icloud` to scope results | `icloud` |

## Expected Output
- **Normal:** One or two account names per device, consistent over time.
- **Suspicious:** Multiple distinct Apple IDs on the same device in a short window, or an unknown Apple ID appearing around the time of an incident.

## Story
Written during initial logarchive mapping to understand what account identity fields were available. Confirmed that `icloud_account_name` is reliably populated for sign-in and token refresh events, but absent on some background sync events. Used to link a device to an account in subsequent investigations.

## Notes / Gotchas
- `icloud_account_name` may be null for background sync events — use `| where isnotnull(icloud_account_name)` to filter those out if needed.
- Field name may vary across logarchive versions — check `fields/README.md` for known aliases.
- For time-boxed investigations, always add an earliest/latest constraint to avoid scanning the full index.

---

**Author:** @analyst1  
**Created:** 2026-03-01  
**Last Validated:** 2026-03-01  
**Tags:** `icloud` `account` `identity`
