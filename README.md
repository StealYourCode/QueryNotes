# LogArchive Query Catalog

Central index of all documented queries for LogArchive investigation.  
Each query lives in its own file under `splunk/` or `timesketch/`.

> **How to contribute:** Duplicate a template file, fill it in, open a PR.  
> **Naming convention:** `tool/YYYY-MM_short-description.md`

---

## Query Index

| # | Tool | Query Name | Tags | Last Validated | Author |
|---|------|------------|------|---------------|--------|
| 1 | Splunk | [iCloud Account Name Lookup](splunk/2026-03_icloud-account-name.md) | `icloud` `account` `identity` | 2026-03-01 | @analyst1 |
| 2 | Timesketch | [Running Process List at Event Time](timesketch/2026-03_running-process-list.md) | `process` `execution` `runtime` | 2026-03-05 | @analyst2 |

---

## Folder Structure

```
/
├── README.md
├── splunk/
│   ├── _TEMPLATE.md
│   └── 2026-03_icloud-account-name.md
├── timesketch/
│   ├── _TEMPLATE.md
│   └── 2026-03_running-process-list.md
└── fields/
    └── README.md
```

---

## Tag Reference

| Tag | Meaning |
|-----|---------|
| `icloud` | Queries related to iCloud account activity |
| `account` | Account identity / authentication events |
| `process` | Process execution and listing |
| `execution` | Code/binary execution events |
| `identity` | User or account identification |
| `runtime` | System state at a point in time |
