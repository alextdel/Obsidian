### Location Usage

```
TABLE
    location AS "Location",
    chapter-number + "." + scene-number AS "Scene"
FROM "01-Projects/Your-Project/02-Manuscript/Chapters"
WHERE type = "scene"
FLATTEN location
SORT location ASC
GROUP BY location
```
