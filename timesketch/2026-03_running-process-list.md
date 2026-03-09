# Running Process List at Event Time

## Summary
Surfaces all process execution events from logarchive within a defined time window, giving a snapshot of what was running on the device at the time of an incident.

## When to Use
Use this when you need to establish what processes were active on a device before, during, or after a suspicious event. Useful for malware triage and corroborating other findings.

## Query (Timesketch search string)

```
data_type:"logarchive:process_event" AND event_type:"process_start"
```

For a specific time window, apply Timesketch's timeline filter on top of this query.  
To narrow to a specific binary:
```
data_type:"logarchive:process_event" AND event_type:"process_start" AND process_name:"suspicious_binary"
```

## Key Fields

| Field | Description | Example Value |
|-------|-------------|---------------|
| `process_name` | Name of the executed binary | `launchd`, `com.apple.Safari` |
| `process_path` | Full path of the binary on disk | `/usr/bin/launchd` |
| `pid` | Process ID assigned at runtime | `1234` |
| `parent_pid` | PID of the parent process | `1` |
| `event_type` | Type of process event | `process_start`, `process_exit` |
| `data_type` | Logarchive data type — use to scope to process events | `logarchive:process_event` |

## Expected Output
- **Normal:** System binaries (`launchd`, `kernel_task`, `loginwindow`) with expected paths under `/usr/` or `/System/`.
- **Suspicious:** Binaries running from unusual paths (e.g. `/tmp/`, `/Users/<name>/Downloads/`), unknown names, or processes with `parent_pid` pointing to an unexpected parent.

## Story
Written to establish a process baseline during logarchive mapping. Discovered that `process_path` is only populated for `process_start` events, not `process_exit`. Used to identify a suspicious binary running from a user's temp directory during an incident review. The `parent_pid` field was key in reconstructing the execution chain.

## Notes / Gotchas
- `process_path` is absent on some `process_exit` events — always filter on `event_type:"process_start"` for reliable path data.
- Label interesting processes directly in Timesketch using the star/label feature so teammates can see your annotations without re-running the query.
- For deep process tree reconstruction, combine with the Splunk parent/child PID query (see `splunk/` folder).

---

**Author:** @analyst2  
**Created:** 2026-03-05  
**Last Validated:** 2026-03-05  
**Tags:** `process` `execution` `runtime`
