### Character Appearances

```
TABLE
    map(filter(file.outlinks, (link) => contains(link.path, "03-Characters")), (link) => link.displayName) AS "Characters"
FROM "01-Projects/Your-Project/02-Manuscript/Chapters"
WHERE type = "scene"
SORT chapter-number ASC, scene-number ASC
```
