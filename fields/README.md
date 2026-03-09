# LogArchive Field Dictionary

Known fields observed in logarchive events. Update this as new fields are discovered.

| Field Name | Tool | Data Type | Description | Example Value | Confidence | Notes |
|------------|------|-----------|-------------|---------------|------------|-------|
| `icloud_account_name` | Splunk | string | Apple ID / iCloud email signed in at event time | `john.doe@icloud.com` | High | Null on background sync events |
| `device_id` | Splunk | string | Unique device identifier | `ABCD1234EFGH5678` | High | |
| `event_type` | Both | string | Type of event within its category | `sign_in`, `process_start` | High | Values vary by category |
| `category` | Splunk | string | High-level log category | `icloud`, `system` | High | |
| `process_name` | Timesketch | string | Name of the executed binary | `launchd` | High | |
| `process_path` | Timesketch | string | Full on-disk path of the binary | `/usr/bin/launchd` | High | Only populated on `process_start` |
| `pid` | Timesketch | integer | Process ID at runtime | `1234` | High | |
| `parent_pid` | Timesketch | integer | PID of the spawning process | `1` | High | Key for process tree reconstruction |
| `data_type` | Timesketch | string | Logarchive data type identifier | `logarchive:process_event` | High | Use to scope Timesketch queries |

---

**Confidence levels:** High = verified in multiple events · Medium = observed once or twice · Low = inferred / unverified
