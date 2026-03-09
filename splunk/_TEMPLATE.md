# _TEMPLATE — Splunk Query

> Copy this file, rename it `YYYY-MM_short-description.md`, fill it in, open a PR.

---

## Summary
<!-- One sentence. What does this query find? -->
_e.g. "Finds all logarchive events where X happened to Y."_

## When to Use
<!-- What scenario or question triggers the use of this query? -->
_e.g. "Use this when investigating suspected account takeover on a device."_

## Query

```splunk
index=YOUR_INDEX sourcetype=YOUR_SOURCETYPE
| YOUR SPL HERE
| table _time field1 field2 field3
```

## Key Fields

| Field | Description | Example Value |
|-------|-------------|---------------|
| `field1` | What this field represents | `example_value` |
| `field2` | What this field represents | `example_value` |

## Expected Output
<!-- What does a normal result look like? What does a suspicious result look like? -->

## Story
<!-- Why was this query written? What incident or question prompted it? What did it find? -->

## Notes / Gotchas
<!-- Edge cases, known gaps, related queries -->

---

**Author:** @your-handle  
**Created:** YYYY-MM-DD  
**Last Validated:** YYYY-MM-DD  
**Tags:** `tag1` `tag2`
