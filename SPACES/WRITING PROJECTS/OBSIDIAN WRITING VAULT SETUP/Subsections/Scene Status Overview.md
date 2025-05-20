### Scene Status Overview

```
TABLE 
    chapter-number + "." + scene-number AS "Scene",
    chapter AS "Chapter", 
    title AS "Title",
    status AS "Status", 
    word-count AS "Words"
FROM "01-Projects/Your-Project/02-Manuscript/Chapters"
WHERE type = "scene"
SORT chapter-number ASC, scene-number ASC
```
