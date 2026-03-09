# _TEMPLATE - Timesketch Query

> Copy this file, rename it `YYYY-MM_short-description.md`, fill it in, open a PR.

---

## Summary
<!-- One sentence. What does this query surface in a Timesketch sketch? -->

## When to Use
<!-- What scenario triggers the use of this query? What question does it answer? -->

## Query (Elasticsearch / OpenSearch DSL)

```json
{
  "query": {
    "bool": {
      "must": [
        { "match": { "field_name": "value" } }
      ]
    }
  }
}
```

Or as a Timesketch search string:
```
field_name:"value" AND other_field:"other_value"
```

## Key Fields

| Field | Description | Example Value |
|-------|-------------|---------------|
| `field1` | What this field represents | `example_value` |

## Expected Output
<!-- What events should appear? What is a normal vs suspicious pattern? -->

## Story
<!-- Why was this query written? What did it uncover? -->

## Notes / Gotchas
<!-- Sketch setup requirements, label suggestions, timeline tips -->

---

**Author:** @your-handle  
**Created:** YYYY-MM-DD  
**Last Validated:** YYYY-MM-DD  
**Tags:** `tag1` `tag2`
