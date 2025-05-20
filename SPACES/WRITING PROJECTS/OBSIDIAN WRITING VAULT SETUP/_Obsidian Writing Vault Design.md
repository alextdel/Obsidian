
# Obsidian Fiction Writer's Hub: A Comprehensive Vault System

## Conceptual Overview

This vault structure is designed to be a streamlined workspace for fiction writers managing multiple projects simultaneously. The system prioritises creative flow over technical complexity with these core principles:

1. **Project Autonomy** - Each writing project exists as a self-contained unit
2. **Resource Sharing** - Common templates and reference materials available across all projects
3. **Visual Organisation** - Canvas files for intuitive plot and character relationship mapping
4. **Minimal Maintenance** - Automation and templates reduce repetitive setup tasks
5. **Progress Tracking** - Built-in journaling and metrics to monitor writing momentum
6. **Scene-Based Writing** - Granular scene files under chapters for flexible drafting and organisation

The design balances flexibility with structure, providing clear organisation without imposing rigid workflows that might interfere with your creative process.

## Folder Hierarchy

```
Fiction-Writers-Hub/
│
├── 00-Hub/
│   ├── 00-Dashboard.md
│   ├── 01-Active-Projects.md
│   └── 02-Archived-Projects.md
│
├── 01-Projects/
│   ├── Project-Template/
│   │   ├── 00-Project-Home.md
│   │   ├── 01-Outline/
│   │   │   ├── 00-Story-Synopsis.md
│   │   │   ├── 01-Plot-Structure.md
│   │   │   └── 02-Chapter-Outline.md
│   │   ├── 02-Manuscript/
│   │   │   ├── 00-Complete-Manuscript.md
│   │   │   └── Chapters/
│   │   │       ├── 01-Chapter-One/
│   │   │       │   ├── 00-Chapter-One.md
│   │   │       │   ├── 01-Scene-One.md
│   │   │       │   └── 02-Scene-Two.md
│   │   │       └── 02-Chapter-Two/
│   │   │           ├── 00-Chapter-Two.md
│   │   │           ├── 01-Scene-One.md
│   │   │           └── 02-Scene-Two.md
│   │   ├── 03-Characters/
│   │   │   ├── 00-Character-List.md
│   │   │   └── Templates/
│   │   │       ├── Main-Character.md
│   │   │       └── Supporting-Character.md
│   │   ├── 04-World/
│   │   │   ├── 00-World-Overview.md
│   │   │   ├── 01-Locations/
│   │   │   ├── 02-Items/
│   │   │   └── 03-Concepts/
│   │   ├── 05-Research/
│   │   │   └── 00-Research-Notes.md
│   │   ├── 06-Canvas/
│   │   │   ├── 00-Story-Structure.canvas
│   │   │   ├── 01-Character-Relationships.canvas
│   │   │   └── 02-Timeline.canvas
│   │   └── 07-Journal/
│   │       ├── 00-Project-Journal.md
│   │       └── 00-Word-Count-Log.md
│   ├── Example-Project/
│   │   └── ... (Same structure as Project-Template)
│   └── ... (Additional projects)
│
├── 02-Resources/
│   ├── 00-Templates/
│   │   ├── 00-Project-Templates/
│   │   │   └── New-Project.md
│   │   ├── 01-Character-Templates/
│   │   │   ├── Main-Character.md
│   │   │   └── Supporting-Character.md
│   │   ├── 02-Location-Templates/
│   │   │   └── Location.md
│   │   ├── 03-Chapter-Templates/
│   │   │   ├── Chapter.md
│   │   │   └── Scene.md
│   │   └── 04-Canvas-Templates/
│   │       └── ... (Canvas template files)
│   ├── 01-Writing-Craft/
│   │   ├── 00-Plot-Structures.md
│   │   ├── 01-Character-Development.md
│   │   └── 02-Dialogue-Techniques.md
│   └── 02-Reference/
│       ├── 00-Name-Ideas.md
│       └── 01-Common-Phrases.md
│
└── 03-Writing-Journal/
    ├── 00-Journal-Dashboard.md
    ├── 01-Goals-and-Progress.md
    ├── 02-Daily/
    │   └── ... (Daily journal entries)
    └── 03-Weekly/
        └── ... (Weekly reflections)
```

---

## Markdown Templates with YAML Frontmatter

[[1. Project Template (00-Project-Home.md)]]
[[2. Chapter Template (Chapter.md)]]
[[3. Scene Template (Scene.md)]]
[[4. Character Template (Main-Character.md)]]
[[5. Location Template (Location.md)]]
[[6. Writing Journal Template (Daily Journal)]]

---
## Bash Script for Automatic Vault Generation

The following is the script for automatically making a complete new vault with examples and templates etc

[[Vault Creation Script]]

---
## Recommended Obsidian Plugins

[[Suggested Obsidian Plugins]]

---
## Day-to-Day Usage Instructions

[[Day to Day Usage Instructions]]

---
## Example Dataview Queries for Fiction Writers

Include these in your dashboard notes to automatically track project status:

- [[Scene Status Overview]]
- [[Character Appearances]]
- [[Location Usage]]

---
This scene-based writing system provides granular organisation while maintaining the connections between chapters, characters, and world-building elements. The structured YAML front-matter makes it possible to track progress and relationships across your entire project with minimal maintenance overhead.