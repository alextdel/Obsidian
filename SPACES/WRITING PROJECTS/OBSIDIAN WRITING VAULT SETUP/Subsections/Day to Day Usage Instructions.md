### Getting Started

1. **Open Obsidian** and select the "Fiction-Writers-Hub" vault.
2. Navigate to the **Dashboard** at "00-Hub/00-Dashboard.md" for a quick overview.
3. **Install recommended plugins** through Obsidian's plugin marketplace.

### Creating a New Project

1. **Navigate** to "01-Projects" folder.
2. **Duplicate** the "Project-Template" folder and rename it to your project name.
3. **Open** the "00-Project-Home.md" file in your new project folder.
4. **Update** the YAML frontmatter with your project details (title, genre, etc.).
5. **Fill in** the project overview section with a brief description.

### Working with Scenes and Chapters

1. **Creating a New Chapter**:
    
    - Navigate to your project's "02-Manuscript/Chapters" folder.
    - Create a new folder with the naming convention "XX-Chapter-Name".
    - Use Templater or QuickAdd to create a chapter file named "00-Chapter-Name.md" inside the folder.
    - Fill in the chapter details using the template structure.
2. **Creating New Scenes**:
    
    - Navigate to the appropriate chapter folder.
    - Use Templater or QuickAdd to create a new scene from the scene template.
    - Name it following the convention "XX-Scene-Name.md" (where XX is the scene number).
    - Fill in the scene details in the YAML frontmatter.
    - Write your scene content in the "Content" section.
3. **Updating Chapter Links**:
    
    - When you add a new scene, update the chapter file to include:
        - The scene in the YAML frontmatter's "scenes" list
        - A link to the scene in the "Scenes" section of the chapter
4. **Scene Management Workflow**:
    
    - Write individual scenes as discrete units.
    - Track status in the YAML frontmatter (outline → draft → revision → complete).
    - Update word counts in both the scene file and the chapter file when major writing is completed.
    - Use the chapter file as a hub to navigate between related scenes.

### Working with Characters and Locations

1. **Character Creation**:
    
    - Navigate to your project's "03-Characters" folder.
    - Use Templater or QuickAdd plugin to create a new character from template.
    - Fill in the character details using the template structure.
    - **Linking Characters to Scenes**:
        - In the character file, add scene references in the "related-scenes" YAML field.
        - In scene files, list the character in the "characters" YAML field.
2. **Location Creation**:
    
    - Navigate to your project's "04-World/01-Locations" folder.
    - Create a new location note using the location template.
    - Fill in the location details.
    - **Linking Locations to Scenes**:
        - In the location file, add scene references in the "related-scenes" YAML field.
        - In scene files, specify the location in the "location" YAML field.

### Using Canvas Files

1. **Open** a canvas file from your project's "06-Canvas" folder.
    
2. For **Story Structure Canvas**:
    
    - Add your story's central concept to the middle.
    - Add key plot points connected to the centre.
    - Drag and connect scene/chapter notes to relevant plot points.
3. For **Character Relationships Canvas**:
    
    - Add character nodes for each major character.
    - Draw connections between characters showing relationships.
    - Use colours to distinguish allies, enemies, and neutral relationships.
4. For **Timeline Canvas**:
    
    - Create a horizontal timeline with major events.
    - Link to actual scene files for each timeline event.
    - Use colour coding for different storylines or character arcs.
    - Use the timeline to ensure narrative consistency.

### Tracking Writing Progress

1. **Scene Word Count Tracking**:
    
    - Update the "word-count" field in each scene's YAML frontmatter.
    - Use the Novel Word Count plugin to automatically track scene word counts.
2. **Chapter Progress Tracking**:
    
    - Update the chapter's "word-count" and scene status information.
    - Use Dataview to create dynamic listings of scene completion status.
3. **Daily Writing Journal**:
    
    - Navigate to "03-Writing-Journal/02-Daily".
    - Create a new daily journal entry (or use Calendar plugin).
    - Record your word count, time spent, scenes completed, and reflections.
    - Record which specific scenes you worked on.
4. **Project Word Count**:
    
    - Update your total word count in your project's "07-Journal/00-Word-Count-Log.md".
    - Use the "Scene Progress" table to track scene completion status.
    - Use the Word Count Dashboard plugin for visual statistics.

### Using Dataview for Progress Tracking

Create a Dataview query in your project's journal to automatically track scene progress:

```
TABLE 
    scene-number AS "Scene", 
    status AS "Status", 
    word-count AS "Words"
FROM "01-Projects/Your-Project/02-Manuscript/Chapters"
WHERE type = "scene"
SORT chapter-number ASC, scene-number ASC
```

### Maintaining Shared Resources

1. **Adding Writing Craft Notes**:
    
    - Navigate to "02-Resources/01-Writing-Craft".
    - Create new notes with writing techniques, insights, or lessons learned.
2. **Adding Reference Materials**:
    
    - Navigate to "02-Resources/02-Reference".
    - Add research findings, name ideas, or other reference materials.
3. **Creating New Templates**:
    
    - If you create an improved template, save it to "02-Resources/00-Templates" to use across projects.
    - Update the template YAML fields to match your workflow needs.

### Writing Process Workflow

1. **Outlining Phase**:
    
    - Create chapter folders and initial chapter note files.
    - Add preliminary scene files with basic information.
    - Set all scene status to "outline".
    - Complete the "Summary" and "Goal" sections of each scene.
2. **Drafting Phase**:
    
    - Set scene status to "draft".
    - Write the full content of each scene.
    - Update word counts as you go.
    - Complete character and setting information.
3. **Revision Phase**:
    
    - Set scene status to "revision".
    - Review and revise scene content.
    - Check for consistency across linked scenes.
    - Ensure character and plot continuity.
4. **Completion Phase**:
    
    - Set scene status to "complete".
    - Final word count recorded.
    - Scene fully linked to characters, locations, etc.
    - Update project metrics.

### Compiling Your Manuscript

1. **Using Longform Plugin**:
    
    - Create a Longform project that points to your scene files.
    - Arrange scenes in order.
    - Compile into a single document for export.
2. **Manual Compilation**:
    
    - Use the "00-Complete-Manuscript.md" file to link to all chapters.
    - For final export, copy all scene content in proper order.
    - Use Obsidian's export features to create a final document.

### Completing a Project

1. **Finalise All Scenes**:
    
    - Ensure all scenes have status "complete".
    - Verify final word counts are accurate.
    - Check that all cross-references between notes are working.
2. **Archive the Project**:
    
    - Change the status in "00-Project-Home.md" to "Completed" or "Archived".
    - Update "00-Hub/01-Active-Projects.md" and "00-Hub/02-Archived-Projects.md".
    - Consider creating a final project retrospective note.

## Tips for Minimal Maintenance

1. **Focus on writing scenes first, metadata later** - Update YAML when you finish a writing session, not during creative flow.
    
2. **Use Templater for automatic values** - Configure Templater to automatically fill common YAML fields like date, sequential scene numbers, etc.
    
3. **Create a QuickAdd macro** for new scenes that:
    
    - Creates a new scene file in the correct chapter folder
    - Automatically numbers the scene
    - Adds basic YAML frontmatter
    - Updates the parent chapter's scene list
4. **Schedule a weekly "linking day"** to update relationships between characters, scenes, and locations instead of doing it with every writing session.
    
5. **Use Dataview queries for reports** rather than maintaining manual lists:
    
    - Scene status across the project
    - Word count by chapter
    - Character appearances in scenes
    - Locations used in the manuscript
6. **Create Canvas files for visual management** rather than trying to maintain complex written outlines.
    
7. **Automate backups with Obsidian Git** to maintain version history without manual intervention.
    
8. **Use a plugin like Workspaces** to save different configurations for:
    
    - Writing mode (focused on current scene)
    - Editing mode (showing multiple linked notes)
    - Planning mode (showing outline and canvas files)
