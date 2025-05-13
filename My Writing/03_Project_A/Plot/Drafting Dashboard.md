# 🚧 Drafting Progress

## Chapters by Status

```dataview
TABLE title, number, status
FROM "Manuscript"
WHERE type = "chapter"
GROUP BY status
SORT number ASC
```
