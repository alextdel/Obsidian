To run this file
- make a copy
- edit to remove  these instructions and the beginning and ending lines of the code block eg. the backtick lines
- make the file executable `chmod +x filename`

```bash
#!/bin/bash

# Fiction Writer's Hub - Obsidian Vault Generator
# Creates a comprehensive Obsidian vault structure for fiction writing

# Configuration
VAULT_NAME="Fiction-Writers-Hub"
AUTHOR_NAME="Your Name"
DATE=$(date +"%Y-%m-%d")

# Create base vault directory
echo "Creating Fiction Writer's Hub vault..."
mkdir -p "$VAULT_NAME"
cd "$VAULT_NAME"

# Create main folder structure
echo "Generating main folder structure..."
mkdir -p "00-Hub"
mkdir -p "01-Projects/Project-Template"
mkdir -p "02-Resources/00-Templates/00-Project-Templates"
mkdir -p "02-Resources/00-Templates/01-Character-Templates"
mkdir -p "02-Resources/00-Templates/02-Location-Templates"
mkdir -p "02-Resources/00-Templates/03-Chapter-Templates"
mkdir -p "02-Resources/00-Templates/04-Canvas-Templates"
mkdir -p "02-Resources/00-Templates/05-Journal-Templates"
mkdir -p "02-Resources/01-Writing-Craft"
mkdir -p "02-Resources/02-Reference"
mkdir -p "03-Writing-Journal/02-Daily"
mkdir -p "03-Writing-Journal/03-Weekly"

# Create Project Template structure
echo "Creating Project Template structure..."
mkdir -p "01-Projects/Project-Template/01-Outline"
mkdir -p "01-Projects/Project-Template/02-Manuscript/Chapters/01-Chapter-One"
mkdir -p "01-Projects/Project-Template/02-Manuscript/Chapters/02-Chapter-Two"
mkdir -p "01-Projects/Project-Template/03-Characters/Templates"
mkdir -p "01-Projects/Project-Template/04-World/01-Locations"
mkdir -p "01-Projects/Project-Template/04-World/02-Items"
mkdir -p "01-Projects/Project-Template/04-World/03-Concepts"
mkdir -p "01-Projects/Project-Template/05-Research"
mkdir -p "01-Projects/Project-Template/06-Canvas"
mkdir -p "01-Projects/Project-Template/07-Journal"

# Create Example Project (copy of template)
echo "Creating Example Project..."
cp -r "01-Projects/Project-Template" "01-Projects/Example-Project"

# Create Hub dashboard files
echo "Creating dashboard files..."
cat > "00-Hub/00-Dashboard.md" << EOL
---
title: "Fiction Writer's Hub Dashboard"
created: $DATE
---

# Fiction Writer's Hub

Welcome to your Obsidian Fiction Writer's Hub! This dashboard provides quick access to all your writing projects and resources.

## Quick Navigation

- [[01-Active-Projects|Active Projects]]
- [[02-Archived-Projects|Archived Projects]]
- [[00-Journal-Dashboard|Writing Journal]]

## Recent Projects

*Links to your most recently accessed projects will appear here*

## Writing Stats

*Overall writing statistics across projects*

## Notes and Reminders

*Important notes and upcoming deadlines*
EOL

cat > "00-Hub/01-Active-Projects.md" << EOL
---
title: "Active Projects"
created: $DATE
---

# Active Projects

This is a list of all your current active writing projects.

## Projects In Progress

- [[../01-Projects/Project-Template/00-Project-Home|Project Template]]
- [[../01-Projects/Example-Project/00-Project-Home|Example Project]]

## Project Status Overview

| Project | Status | Current Word Count | Goal | Progress |
|---------|--------|-------------------|------|----------|
| Project Template | Planning | 0 | 80,000 | 0% |
| Example Project | Planning | 0 | 80,000 | 0% |
EOL

cat > "00-Hub/02-Archived-Projects.md" << EOL
---
title: "Archived Projects"
created: $DATE
---

# Archived Projects

This is a list of all your completed or on-hold writing projects.

## Completed Projects

*List of finished projects will appear here*

## On Hold Projects

*List of projects currently paused will appear here*
EOL

# Create Project Template files
echo "Creating Project Template files..."

# Project Home
cat > "01-Projects/Project-Template/00-Project-Home.md" << EOL
---
title: "Project Title"
author: "$AUTHOR_NAME"
created: $DATE
status: "Planning" # Options: Planning, In Progress, Revising, Completed, Archived
genre: ""
wordcount-goal: 80000
current-wordcount: 0
---

# Project Title

## Project Overview

*Brief summary of the project (1-3 paragraphs)*

## Key Information

- **Status:** Planning
- **Genre:** Fiction
- **Word Count Goal:** 80,000 words
- **Current Word Count:** 0 words

## Quick Links

- [[01-Outline/00-Story-Synopsis|Story Synopsis]]
- [[01-Outline/01-Plot-Structure|Plot Structure]]
- [[01-Outline/02-Chapter-Outline|Chapter Outline]]
- [[03-Characters/00-Character-List|Character List]]
- [[04-World/00-World-Overview|World Overview]]
- [[07-Journal/00-Project-Journal|Project Journal]]
- [[02-Manuscript/00-Complete-Manuscript|Complete Manuscript]]

## Project Canvas Files
- [[06-Canvas/00-Story-Structure|Story Structure Canvas]]
- [[06-Canvas/01-Character-Relationships|Character Relationships Canvas]]
- [[06-Canvas/02-Timeline|Timeline Canvas]]

## Project Notes

*Any additional notes about the project*
EOL

# Story Synopsis
cat > "01-Projects/Project-Template/01-Outline/00-Story-Synopsis.md" << EOL
---
type: synopsis
title: "Story Synopsis"
created: $DATE
modified: $DATE
---

# Story Synopsis

## Elevator Pitch

*One-paragraph summary of your story (2-3 sentences)*

## Extended Synopsis

*Expanded summary of the story (3-5 paragraphs)*

## Key Themes

- Theme 1
- Theme 2
- Theme 3

## Core Conflict

*What is the central conflict that drives the story?*

## Notes

*Additional notes about the synopsis*
EOL

# Plot Structure
cat > "01-Projects/Project-Template/01-Outline/01-Plot-Structure.md" << EOL
---
type: plot-structure
title: "Plot Structure"
created: $DATE
modified: $DATE
---

# Plot Structure

## Story Structure

### Act 1: Setup

#### Inciting Incident

*What event kicks off the story?*

#### First Plot Point

*What event forces the protagonist into the main conflict?*

### Act 2: Confrontation

#### First Pinch Point

*A reminder of the antagonistic force*

#### Midpoint

*Major revelation or shift in the story*

#### Second Pinch Point

*Another reminder of the antagonistic force*

### Act 3: Resolution

#### Second Plot Point

*Final piece of information needed before climax*

#### Climax

*The final confrontation*

#### Resolution

*How the story wraps up*

## Subplots

- Subplot 1: *Brief description*
- Subplot 2: *Brief description*

## Notes

*Additional notes about plot structure*
EOL

# Chapter Outline
cat > "01-Projects/Project-Template/01-Outline/02-Chapter-Outline.md" << EOL
---
type: chapter-outline
title: "Chapter Outline"
created: $DATE
modified: $DATE
---

# Chapter Outline

## Act 1

### Chapter 1: *Chapter Title*

- Scene 1: *Brief summary of scene events*
- Scene 2: *Brief summary of scene events*

### Chapter 2: *Chapter Title*

- Scene 1: *Brief summary of scene events*
- Scene 2: *Brief summary of scene events*

## Act 2

### Chapter 3: *Chapter Title*

- Scene 1: *Brief summary of scene events*
- Scene 2: *Brief summary of scene events*

### Chapter 4: *Chapter Title*

- Scene 1: *Brief summary of scene events*
- Scene 2: *Brief summary of scene events*

## Act 3

### Chapter 5: *Chapter Title*

- Scene 1: *Brief summary of scene events*
- Scene 2: *Brief summary of scene events*

### Chapter 6: *Chapter Title*

- Scene 1: *Brief summary of scene events*
- Scene 2: *Brief summary of scene events*

## Notes

*Additional notes about chapter structure*
EOL

# Complete Manuscript
cat > "01-Projects/Project-Template/02-Manuscript/00-Complete-Manuscript.md" << EOL
---
type: manuscript
title: "Complete Manuscript"
created: $DATE
modified: $DATE
---

# Complete Manuscript

*This file is for combining all chapters into a complete manuscript.*

## Table of Contents

1. [[Chapters/01-Chapter-One/00-Chapter-One|Chapter 1: Chapter Title]]
2. [[Chapters/02-Chapter-Two/00-Chapter-Two|Chapter 2: Chapter Title]]

## Notes

*Use the Longform plugin to manage the complete manuscript more effectively.*
EOL

# Chapter files
cat > "01-Projects/Project-Template/02-Manuscript/Chapters/01-Chapter-One/00-Chapter-One.md" << EOL
---
type: chapter
title: "Chapter Title"
chapter-number: 1
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-period: ""
scenes:
  - "01-Scene-One"
  - "02-Scene-Two"
tags:
  - chapter
created: $DATE
modified: $DATE
---

# Chapter 1: Chapter Title

## Summary

*Brief chapter summary (1-2 paragraphs)*

## Scenes

- [[01-Scene-One|Scene 1]] - *Brief description*
- [[02-Scene-Two|Scene 2]] - *Brief description*

## POV Character

*Notes about POV character experience in this chapter*

## Purpose

*What this chapter accomplishes in the story*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

# Scene files for Chapter One
cat > "01-Projects/Project-Template/02-Manuscript/Chapters/01-Chapter-One/01-Scene-One.md" << EOL
---
type: scene
title: "Scene Title"
scene-number: 1
chapter: "Chapter Title"
chapter-number: 1
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-of-day: ""
weather: ""
characters:
  - "Character Name"
  - "Character Name"
tags:
  - scene
created: $DATE
modified: $DATE
---

# Scene 1: Scene Title

## Summary

*Brief scene summary (1-2 sentences)*

## Goal

*What this scene needs to accomplish*

## Setting

**Location:** *Where the scene takes place*
**Time:** *Time of day*
**Weather:** *Weather conditions*

## Characters Present

- Character Name
- Character Name

## Emotional Changes

- **Beginning emotion:** *Character's emotional state at beginning*
- **Ending emotion:** *Character's emotional state at end*

## Content

*The actual scene text goes here*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

cat > "01-Projects/Project-Template/02-Manuscript/Chapters/01-Chapter-One/02-Scene-Two.md" << EOL
---
type: scene
title: "Scene Title"
scene-number: 2
chapter: "Chapter Title"
chapter-number: 1
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-of-day: ""
weather: ""
characters:
  - "Character Name"
  - "Character Name"
tags:
  - scene
created: $DATE
modified: $DATE
---

# Scene 2: Scene Title

## Summary

*Brief scene summary (1-2 sentences)*

## Goal

*What this scene needs to accomplish*

## Setting

**Location:** *Where the scene takes place*
**Time:** *Time of day*
**Weather:** *Weather conditions*

## Characters Present

- Character Name
- Character Name

## Emotional Changes

- **Beginning emotion:** *Character's emotional state at beginning*
- **Ending emotion:** *Character's emotional state at end*

## Content

*The actual scene text goes here*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

# Chapter Two with scenes
cat > "01-Projects/Project-Template/02-Manuscript/Chapters/02-Chapter-Two/00-Chapter-Two.md" << EOL
---
type: chapter
title: "Chapter Title"
chapter-number: 2
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-period: ""
scenes:
  - "01-Scene-One"
  - "02-Scene-Two"
tags:
  - chapter
created: $DATE
modified: $DATE
---

# Chapter 2: Chapter Title

## Summary

*Brief chapter summary (1-2 paragraphs)*

## Scenes

- [[01-Scene-One|Scene 1]] - *Brief description*
- [[02-Scene-Two|Scene 2]] - *Brief description*

## POV Character

*Notes about POV character experience in this chapter*

## Purpose

*What this chapter accomplishes in the story*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

# Scene files for Chapter Two
cat > "01-Projects/Project-Template/02-Manuscript/Chapters/02-Chapter-Two/01-Scene-One.md" << EOL
---
type: scene
title: "Scene Title"
scene-number: 1
chapter: "Chapter Title"
chapter-number: 2
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-of-day: ""
weather: ""
characters:
  - "Character Name"
  - "Character Name"
tags:
  - scene
created: $DATE
modified: $DATE
---

# Scene 1: Scene Title

## Summary

*Brief scene summary (1-2 sentences)*

## Goal

*What this scene needs to accomplish*

## Setting

**Location:** *Where the scene takes place*
**Time:** *Time of day*
**Weather:** *Weather conditions*

## Characters Present

- Character Name
- Character Name

## Emotional Changes

- **Beginning emotion:** *Character's emotional state at beginning*
- **Ending emotion:** *Character's emotional state at end*

## Content

*The actual scene text goes here*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

cat > "01-Projects/Project-Template/02-Manuscript/Chapters/02-Chapter-Two/02-Scene-Two.md" << EOL
---
type: scene
title: "Scene Title"
scene-number: 2
chapter: "Chapter Title"
chapter-number: 2
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-of-day: ""
weather: ""
characters:
  - "Character Name"
  - "Character Name"
tags:
  - scene
created: $DATE
modified: $DATE
---

# Scene 2: Scene Title

## Summary

*Brief scene summary (1-2 sentences)*

## Goal

*What this scene needs to accomplish*

## Setting

**Location:** *Where the scene takes place*
**Time:** *Time of day*
**Weather:** *Weather conditions*

## Characters Present

- Character Name
- Character Name

## Emotional Changes

- **Beginning emotion:** *Character's emotional state at beginning*
- **Ending emotion:** *Character's emotional state at end*

## Content

*The actual scene text goes here*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

# Character List
cat > "01-Projects/Project-Template/03-Characters/00-Character-List.md" << EOL
---
type: character-list
title: "Character List"
created: $DATE
modified: $DATE
---

# Character List

## Main Characters

- [[Templates/Main-Character|Protagonist Name]] - *Brief description*
- [[Templates/Supporting-Character|Antagonist Name]] - *Brief description*

## Supporting Characters

- [[Templates/Supporting-Character|Character Name]] - *Brief description*
- [[Templates/Supporting-Character|Character Name]] - *Brief description*

## Minor Characters

- Character Name - *Brief description*
- Character Name - *Brief description*

## Notes

*Additional notes about characters*
EOL

# Character templates
cat > "01-Projects/Project-Template/03-Characters/Templates/Main-Character.md" << EOL
---
type: character
name: "Character Name"
role: "protagonist" # Options: protagonist, antagonist, supporting, minor
status: "active" # Options: active, inactive, deceased
age:
occupation: ""
location: ""
related-characters:
  - name: ""
    relationship: ""
related-scenes:
  - scene: ""
    chapter: ""
tags:
  - character
  - protagonist
created: $DATE
---

# Character Name

## Overview

*Brief character summary in 1-2 paragraphs*

## Physical Description

*What does the character look like?*

## Personality

*Core personality traits, strengths, flaws, etc.*

## Background

*Relevant backstory and history*

## Motivation

*What drives this character? What do they want?*

## Arc

*How does this character change throughout the story?*

## Relationships

- **Character Name**: Relationship description
- **Character Name**: Relationship description

## Scenes

{% for scene_ref in related-scenes %}
- [[{{scene_ref.chapter}}/{{scene_ref.scene}}|{{scene_ref.scene}}]] in Chapter [[{{scene_ref.chapter}}]]
{% endfor %}

## Notes

*Additional notes about the character*
EOL

cat > "01-Projects/Project-Template/03-Characters/Templates/Supporting-Character.md" << EOL
---
type: character
name: "Character Name"
role: "supporting" # Options: protagonist, antagonist, supporting, minor
status: "active" # Options: active, inactive, deceased
age:
occupation: ""
location: ""
related-characters:
  - name: ""
    relationship: ""
related-scenes:
  - scene: ""
    chapter: ""
tags:
  - character
  - supporting
created: $DATE
---

# Character Name

## Overview

*Brief character summary in 1-2 paragraphs*

## Physical Description

*What does the character look like?*

## Personality

*Core personality traits, strengths, flaws, etc.*

## Background

*Relevant backstory and history*

## Motivation

*What drives this character? What do they want?*

## Relationships

- **Character Name**: Relationship description
- **Character Name**: Relationship description

## Scenes

{% for scene_ref in related-scenes %}
- [[{{scene_ref.chapter}}/{{scene_ref.scene}}|{{scene_ref.scene}}]] in Chapter [[{{scene_ref.chapter}}]]
{% endfor %}

## Notes

*Additional notes about the character*
EOL

# World Overview
cat > "01-Projects/Project-Template/04-World/00-World-Overview.md" << EOL
---
type: world-overview
title: "World Overview"
created: $DATE
modified: $DATE
---

# World Overview

## Setting

*Brief overview of the story's setting*

## Time Period

*When does the story take place?*

## Key Locations

- [[01-Locations/Location|Location Name]] - *Brief description*
- [[01-Locations/Location|Location Name]] - *Brief description*

## Key Concepts

- Concept Name - *Brief description*
- Concept Name - *Brief description*

## Rules of the World

*What special rules, if any, govern this world?*

## Notes

*Additional notes about the world*
EOL

# Research Notes
cat > "01-Projects/Project-Template/05-Research/00-Research-Notes.md" << EOL
---
type: research
title: "Research Notes"
created: $DATE
modified: $DATE
---

# Research Notes

## Topics Researched

- Topic 1
  - *Notes and findings*
  - *Sources*

- Topic 2
  - *Notes and findings*
  - *Sources*

## Questions to Research

- *Question 1*
- *Question 2*

## Sources

- Book/Article/Website title
- Book/Article/Website title

## Notes

*Additional research notes*
EOL

# Project Journal
cat > "01-Projects/Project-Template/07-Journal/00-Project-Journal.md" << EOL
---
type: project-journal
title: "Project Journal"
created: $DATE
modified: $DATE
---

# Project Journal

## Project Timeline

- $DATE - Project started

## Milestones

- [ ] Complete outline
- [ ] Finish first draft
- [ ] Complete first revision
- [ ] Complete final draft

## Development Notes

*Project-specific thoughts and development notes*

## Challenges

*Challenges encountered during the writing process*

## Insights

*Insights gained while working on this project*

## Notes

*Additional project notes*
EOL

# Word Count Log
cat > "01-Projects/Project-Template/07-Journal/00-Word-Count-Log.md" << EOL
---
type: word-count-log
title: "Word Count Log"
created: $DATE
modified: $DATE
---

# Word Count Log

## Summary

- **Total Words:** 0
- **Goal:** 80,000
- **Progress:** 0%

## Daily Logs

| Date | Starting Word Count | Ending Word Count | Words Written | Total |
|------|---------------------|-------------------|---------------|-------|
| $DATE | 0 | 0 | 0 | 0 |

## Scene Progress

| Chapter | Scene | Status | Word Count |
|---------|-------|--------|------------|
| Chapter 1 | Scene 1 | Outline | 0 |
| Chapter 1 | Scene 2 | Outline | 0 |
| Chapter 2 | Scene 1 | Outline | 0 |
| Chapter 2 | Scene 2 | Outline | 0 |

## Weekly Summary

| Week | Words Written | Daily Average | Scenes Completed |
|------|---------------|---------------|------------------|
| Week 1 | 0 | 0 | 0 |

## Notes

*Additional notes about writing progress*
EOL

# Create Canvas files (placeholders)
echo "Creating Canvas file placeholders..."
cat > "01-Projects/Project-Template/06-Canvas/00-Story-Structure.canvas" << EOL
{
  "nodes": [],
  "edges": []
}
EOL

cat > "01-Projects/Project-Template/06-Canvas/01-Character-Relationships.canvas" << EOL
{
  "nodes": [],
  "edges": []
}
EOL

cat > "01-Projects/Project-Template/06-Canvas/02-Timeline.canvas" << EOL
{
  "nodes": [],
  "edges": []
}
EOL

# Create shared templates
echo "Creating shared templates..."
cat > "02-Resources/00-Templates/00-Project-Templates/New-Project.md" << EOL
---
type: new-project-template
title: "New Project Template"
created: $DATE
---

# New Project Template

This is a template for creating a new project. To use it:

1. Create a new folder in the 01-Projects directory
2. Copy the structure from the Project-Template folder
3. Update the project details in 00-Project-Home.md

## Project Structure

- 00-Project-Home.md
- 01-Outline/
- 02-Manuscript/
  - Chapters/
    - Chapter folders containing scene files
- 03-Characters/
- 04-World/
- 05-Research/
- 06-Canvas/
- 07-Journal/

## Initial Setup Tasks

- [ ] Update project title
- [ ] Create an initial synopsis
- [ ] Set word count goal
- [ ] Define main characters
- [ ] Outline story structure
- [ ] Create initial chapters and scenes
EOL

# Create other shared templates (copy from project templates)
cp "01-Projects/Project-Template/03-Characters/Templates/Main-Character.md" "02-Resources/00-Templates/01-Character-Templates/"
cp "01-Projects/Project-Template/03-Characters/Templates/Supporting-Character.md" "02-Resources/00-Templates/01-Character-Templates/"

cat > "02-Resources/00-Templates/02-Location-Templates/Location.md" << EOL
---
type: location
name: "Location Name"
category: "" # E.g., city, building, natural landmark, etc.
importance: "major" # Options: major, minor
related-scenes:
  - scene: ""
    chapter: ""
tags:
  - location
created: {{date:YYYY-MM-DD}}
---

# Location Name

## Description

*Physical description of the location*

## Significance

*What makes this location important to the story?*

## Key Features

- Feature 1
- Feature 2
- Feature 3

## Characters Associated

*Characters who live here or are strongly connected to this place*

## Scenes

{% for scene_ref in related-scenes %}
- [[{{scene_ref.chapter}}/{{scene_ref.scene}}|{{scene_ref.scene}}]] in Chapter [[{{scene_ref.chapter}}]]
{% endfor %}

## Notes

*Additional details and notes*
EOL

# Copy chapter and scene templates
cat > "02-Resources/00-Templates/03-Chapter-Templates/Chapter.md" << EOL
---
type: chapter
title: "Chapter Title"
chapter-number: 1
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-period: ""
scenes:
  - "01-Scene-One"
  - "02-Scene-Two"
tags:
  - chapter
created: {{date:YYYY-MM-DD}}
modified: {{date:YYYY-MM-DD}}
---

# Chapter {{chapter-number}}: {{title}}

## Summary

*Brief chapter summary (1-2 paragraphs)*

## Scenes

{% for scene in scenes %}
- [[{{scene}}|{{scene}}]] - *Brief description*
{% endfor %}

## POV Character

*Notes about POV character experience in this chapter*

## Purpose

*What this chapter accomplishes in the story*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

cat > "02-Resources/00-Templates/03-Chapter-Templates/Scene.md" << EOL
---
type: scene
title: "Scene Title"
scene-number: 1
chapter: "Chapter Title"
chapter-number: 1
status: "outline" # Options: outline, draft, revision, complete
word-count: 0
pov-character: ""
location: ""
time-of-day: ""
weather: ""
characters:
  - "Character Name"
  - "Character Name"
tags:
  - scene
created: {{date:YYYY-MM-DD}}
modified: {{date:YYYY-MM-DD}}
---

# Scene {{scene-number}}: {{title}}

## Summary

*Brief scene summary (1-2 sentences)*

## Goal

*What this scene needs to accomplish*

## Setting

**Location:** {{location}}
**Time:** {{time-of-day}}
**Weather:** {{weather}}

## Characters Present

{% for character in characters %}
- {{character}}
{% endfor %}

## Emotional Changes

- **Beginning emotion:**
- **Ending emotion:**

## Content

*The actual scene text goes here*

## Notes

*Additional notes for revision, things to address, etc.*
EOL

# Create daily journal template
cat > "02-Resources/00-Templates/05-Journal-Templates/Daily-Journal.md" << EOL
---
type: daily-journal
date: {{date:YYYY-MM-DD}}
project: ""
word-count: 0
time-spent: 0 # in minutes
scenes-completed: 0
scenes-worked-on:
  - chapter: ""
    scene: ""
    words-added: 0
mood: "" # Options: motivated, neutral, struggling
tags:
  - journal
  - daily
---

# Writing Journal: {{date:YYYY-MM-DD}}

## Today's Progress

**Project:** {{project}}
**Word Count:** {{word-count}} words
**Time Spent:** {{time-spent}} minutes
**Scenes Completed:** {{scenes-completed}}

## Scenes Worked On

{% for scene_ref in scenes-worked-on %}
- [[{{scene_ref.chapter}}/{{scene_ref.scene}}|{{scene_ref.scene}}]] - **Words Added:** {{scene_ref.words-added}}
{% endfor %}

## What I Worked On

*Brief description of today's writing accomplishments*

## Challenges

*Any struggles or roadblocks encountered*

## Insights

*New ideas or revelations about the project*

## Tomorrow's Plan

*What I aim to accomplish during the next writing session*

## Notes

*Any additional thoughts or observations*
EOL

# Create weekly journal template
cat > "02-Resources/00-Templates/05-Journal-Templates/Weekly-Journal.md" << EOL
---
type: weekly-journal
week: "{{date:YYYY}}-W{{date:ww}}"
start-date: {{date:YYYY-MM-DD}}
end-date: ""
total-word-count: 0
total-time-spent: 0 # in minutes
scenes-completed: 0
projects-worked-on:
  - ""
tags:
  - journal
  - weekly
---

# Weekly Writing Summary: {{date:YYYY}}-W{{date:ww}}

## Weekly Progress

**Week:** {{week}}
**Total Words:** {{total-word-count}} words
**Total Time:** {{total-time-spent}} minutes
**Scenes Completed:** {{scenes-completed}}

## Projects Worked On

{% for project in projects-worked-on %}
- {{project}}
{% endfor %}

## Accomplishments

*What I accomplished this week*

## Challenges

*What challenges I faced this week*

## Insights and Lessons

*What I learned about my writing or projects*

## Next Week's Goals

*What I aim to accomplish next week*

## Notes

*Additional thoughts or reflections*
EOL

# Create Writing Craft notes
echo "Creating Writing Craft notes..."
cat > "02-Resources/01-Writing-Craft/00-Plot-Structures.md" << EOL
---
type: writing-craft
title: "Plot Structures"
created: $DATE
---

# Plot Structures

## Three-Act Structure

- **Act 1: Setup** (25%)
  - Introduce protagonist and world
  - Inciting incident
  - First plot point

- **Act 2: Confrontation** (50%)
  - Rising action
  - Midpoint
  - Complications and obstacles

- **Act 3: Resolution** (25%)
  - Climax
  - Falling action
  - Resolution

## Hero's Journey

- **Ordinary World**
- **Call to Adventure**
- **Refusal of the Call**
- **Meeting the Mentor**
- **Crossing the Threshold**
- **Tests, Allies, Enemies**
- **Approach to the Inmost Cave**
- **Ordeal**
- **Reward**
- **The Road Back**
- **Resurrection**
- **Return with the Elixir**

## Five-Act Structure

- **Act 1: Exposition**
- **Act 2: Rising Action**
- **Act 3: Climax**
- **Act 4: Falling Action**
- **Act 5: Denouement**

## Save the Cat Beat Sheet

- **Opening Image**
- **Theme Stated**
- **Setup**
- **Catalyst**
- **Debate**
- **Break into Two**
- **B Story**
- **Fun and Games**
- **Midpoint**
- **Bad Guys Close In**
- **All Is Lost**
- **Dark Night of the Soul**
- **Break into Three**
- **Finale**
- **Final Image**

## Scene Structure

- **Goal**: What the POV character wants
- **Conflict**: Obstacles preventing the goal
- **Disaster/Outcome**: Result (usually not what was wanted)
- **Reaction**: Emotional response to outcome
- **Dilemma**: New choices presented
- **Decision**: Choice made, leading to next scene

## Notes

*Additional notes about plot structures*
EOL

cat > "02-Resources/01-Writing-Craft/01-Character-Development.md" << EOL
---
type: writing-craft
title: "Character Development"
created: $DATE
---

# Character Development

## Character Arc Types

### The Change Arc
*Character overcomes flaws and transforms*

### The Growth Arc
*Character grows without fundamental change*

### The Fall Arc
*Character changes for the worse*

### The Flat Arc
*Character remains steadfast, changes the world*

## Character Development Questions

- What does your character want? (External goal)
- What does your character need? (Internal goal)
- What is your character's primary motivation?
- What is your character's greatest fear?
- What is your character's fatal flaw?
- What is your character's moral code?
- What event in your character's past shaped them most?
- How does your character change by the end of the story?

## Character Dimensions

- **Physical** - appearance, mannerisms, health
- **Sociological** - background, education, status, relationships
- **Psychological** - fears, desires, values, temperament

## Notes

*Additional notes about character development*
EOL

cat > "02-Resources/01-Writing-Craft/02-Dialogue-Techniques.md" << EOL
---
type: writing-craft
title: "Dialogue Techniques"
created: $DATE
---

# Dialogue Techniques

## Functions of Dialogue

- Reveal character
- Advance the plot
- Provide information
- Create conflict
- Establish tone and mood
- Build relationships

## Writing Effective Dialogue

- Make each character sound distinct
- Use subtext - what's not being said
- Avoid excessive dialogue tags
- Use action beats instead of tags
- Keep it concise - dialogue is typically more focused than real speech
- Avoid excessive exposition in dialogue ("As you know, Bob...")

## Formatting Dialogue

- New speaker, new paragraph
- Use quotation marks correctly
- Punctuation goes inside quotation marks
- Use dialogue tags sparingly

## Notes

*Additional notes about dialogue techniques*
EOL

# Create Reference files
echo "Creating Reference files..."
cat > "02-Resources/02-Reference/00-Name-Ideas.md" << EOL
---
type: reference
title: "Name Ideas"
created: $DATE
---

# Name Ideas

## Character Names

### Male Names
- Alexander
- Benjamin
- Christopher
- Daniel
- Ethan

### Female Names
- Amelia
- Beatrice
- Charlotte
- Diana
- Eleanor

### Last Names
- Anderson
- Bennett
- Clarke
- Davies
- Evans

## Location Names

### Cities/Towns
- Brightwater
- Crestfall
- Dunbridge
- Eastholm
- Fairhaven

### Natural Locations
- Amber Forest
- Blackwood
- Crystal Lake
- Mistral Mountains
- Whispering Valley

## Notes

*Additional name ideas and resources*
EOL

cat > "02-Resources/02-Reference/01-Common-Phrases.md" << EOL
---
type: reference
title: "Common Phrases"
created: $DATE
---

# Common Phrases

## Weather Descriptions

- The rain drummed against the window panes
- Sunlight filtered through the canopy of leaves
- A bitter wind cut through their coats
- The fog clung to the ground like a shroud
- Heat rose in shimmering waves from the pavement

## Emotional Expressions

- His heart pounded in his chest
- A lump formed in her throat
- Butterflies danced in his stomach
- Her blood ran cold
- A weight lifted from his shoulders

## Time Transitions

- Later that evening
- As dawn broke
- The next morning
- Hours later
- In the days that followed

## Notes

*Additional phrases and transitions*
EOL

# Create Writing Journal
echo "Creating Writing Journal files..."
cat > "03-Writing-Journal/00-Journal-Dashboard.md" << EOL
---
type: journal-dashboard
title: "Writing Journal Dashboard"
created: $DATE
---

# Writing Journal Dashboard

## Current Goals

- Daily goal: 500 words
- Weekly goal: 3,500 words
- Monthly goal: 15,000 words

## Recent Progress

*Recent writing statistics will appear here*

## Current Projects

*Links to active projects*

## This Week's Focus

*What to focus on this week*

## Notes

*Additional notes about writing goals and progress*
EOL

cat > "03-Writing-Journal/01-Goals-and-Progress.md" << EOL
---
type: goals
title: "Goals and Progress"
created: $DATE
---

# Goals and Progress

## Writing Goals

### Short-term Goals
- [ ] Goal 1
- [ ] Goal 2
- [ ] Goal 3

### Medium-term Goals
- [ ] Goal 1
- [ ] Goal 2
- [ ] Goal 3

### Long-term Goals
- [ ] Goal 1
- [ ] Goal 2
- [ ] Goal 3

## Progress Tracker

### Word Count Progress

| Month | Goal | Actual | Difference |
|-------|------|--------|------------|
| January | 15,000 | 0 | -15,000 |
| February | 15,000 | 0 | -15,000 |
| March | 15,000 | 0 | -15,000 |

### Project Progress

| Project | Status | Progress |
|---------|--------|----------|
| Project 1 | Planning | 0% |
| Project 2 | Planning | 0% |

### Scene Progress

| Project | Scenes Completed | Scenes Outlined | Total Scenes | Completion % |
|---------|------------------|-----------------|--------------|--------------|
| Project 1 | 0 | 4 | 4 | 0% |
| Project 2 | 0 | 0 | 0 | 0% |

## Notes

*Additional notes about goals and progress*
EOL

# Create daily journal entry example
cat > "03-Writing-Journal/02-Daily/$(date +"%Y-%m-%d")-Daily.md" << EOL
---
type: daily-journal
date: $DATE
project: "The Forgotten Key"
word-count: 850
time-spent: 90 # in minutes
scenes-completed: 0
scenes-worked-on:
  - chapter: "01-Chapter-One"
    scene: "02-Scene-Two"
    words-added: 850
mood: "motivated" # Options: motivated, neutral, struggling
tags:
  - journal
  - daily
---

# Writing Journal: $DATE

## Today's Progress

**Project:** The Forgotten Key
**Word Count:** 850 words
**Time Spent:** 90 minutes
**Scenes Completed:** 0

## Scenes Worked On

- [[../01-Projects/Example-Project/02-Manuscript/Chapters/01-Chapter-One/02-Scene-Two|02-Scene-Two]] - **Words Added:** 850

## What I Worked On

Made good progress on the scene where Eleanor discovers the key. Really focused on building the mystery and her emotional reaction to finding something unexpected from her grandmother's past. I'm trying to balance the historical elements with the personal connection.

## Challenges

Had some trouble getting the right pacing - the discovery needed to feel significant without becoming melodramatic. Also struggled a bit with historically accurate details about Melbourne in the 1920s.

## Insights

I realized that Eleanor's academic background provides a natural way for her to investigate historical mysteries. This gives me a plausible mechanism for her to dig into archives and records that might otherwise be inaccessible.

## Tomorrow's Plan

Complete Scene Two and begin drafting Chapter One, Scene Three where Eleanor begins researching the Blackwood family history.

## Notes

Need to research more about university archives and historical records available in Melbourne. Also should develop more background on Eleanor's academic career and specialization.
EOL

# Copy templates to Example Project (to show how it would look populated)
echo "Customising Example Project..."

# Update Example Project home
cat > "01-Projects/Example-Project/00-Project-Home.md" << EOL
---
title: "The Forgotten Key"
author: "$AUTHOR_NAME"
created: $DATE
status: "In Progress" # Options: Planning, In Progress, Revising, Completed, Archived
genre: "Mystery"
wordcount-goal: 75000
current-wordcount: 2500
---

# The Forgotten Key

## Project Overview

A historical mystery set in Melbourne during the 1920s. When historian Eleanor Wright discovers a mysterious key among her late grandmother's possessions, she's drawn into a decades-old mystery that involves the city's most powerful family and a secret that could change everything.

## Key Information

- **Status:** In Progress
- **Genre:** Historical Mystery
- **Word Count Goal:** 75,000 words
- **Current Word Count:** 2,500 words

## Quick Links

- [[01-Outline/00-Story-Synopsis|Story Synopsis]]
- [[01-Outline/01-Plot-Structure|Plot Structure]]
- [[01-Outline/02-Chapter-Outline|Chapter Outline]]
- [[03-Characters/00-Character-List|Character List]]
- [[04-World/00-World-Overview|World Overview]]
- [[07-Journal/00-Project-Journal|Project Journal]]
- [[02-Manuscript/00-Complete-Manuscript|Complete Manuscript]]

## Project Canvas Files
- [[06-Canvas/00-Story-Structure|Story Structure Canvas]]
- [[06-Canvas/01-Character-Relationships|Character Relationships Canvas]]
- [[06-Canvas/02-Timeline|Timeline Canvas]]

## Project Notes

Need to research more about Melbourne in the 1920s, particularly the social hierarchies and the layout of the city during that period.
EOL

# Add a populated example chapter and scenes
cat > "01-Projects/Example-Project/02-Manuscript/Chapters/01-Chapter-One/00-Chapter-One.md" << EOL
---
type: chapter
title: "The Discovery"
chapter-number: 1
status: "draft" # Options: outline, draft, revision, complete
word-count: 2500
pov-character: "Eleanor Wright"
location: "Melbourne"
time-period: "1925"
scenes:
  - "01-Scene-One"
  - "02-Scene-Two"
tags:
  - chapter
created: $DATE
modified: $DATE
---

# Chapter 1: The Discovery

## Summary

Eleanor Wright receives a mysterious package containing her late grandmother's possessions, including an ornate key with an unusual symbol. As she examines the items, she finds a cryptic note that hints at a connection to the influential Blackwood family and a long-buried secret.

## Scenes

- [[01-Scene-One|Scene 1: The Package]] - Eleanor receives the package from her grandmother's estate
- [[02-Scene-Two|Scene 2: The Key]] - Eleanor discovers the key and note hidden in a false bottom of a jewelry box

## POV Character

Eleanor is curious but skeptical at first. By the end of the chapter, she's intrigued and slightly unnerved by what she's found.

## Purpose

Introduces the protagonist, establishes the central mystery, and provides the inciting incident that launches Eleanor into the investigation.

## Notes

Consider adding more historical details about 1920s Melbourne to establish the setting more firmly.
EOL

cat > "01-Projects/Example-Project/02-Manuscript/Chapters/01-Chapter-One/01-Scene-One.md" << EOL
---
type: scene
title: "The Package"
scene-number: 1
chapter: "The Discovery"
chapter-number: 1
status: "draft" # Options: outline, draft, revision, complete
word-count: 1200
pov-character: "Eleanor Wright"
location: "Eleanor's Apartment"
time-of-day: "Morning"
weather: "Rainy"
characters:
  - "Eleanor Wright"
  - "Delivery Person"
tags:
  - scene
created: $DATE
modified: $DATE
---

# Scene 1: The Package

## Summary

Eleanor receives an unexpected package containing her grandmother's belongings.

## Goal

Introduce Eleanor and establish her connection to her grandmother, while setting up the arrival of the mysterious items.

## Setting

**Location:** Eleanor's small but tidy apartment in a converted Victorian building
**Time:** Early morning, just after breakfast
**Weather:** A dreary, rainy autumn day

## Characters Present

- Eleanor Wright
- Delivery Person (brief appearance)

## Emotional Changes

- **Beginning emotion:** Routine, slightly bored with daily life
- **Ending emotion:** Curious, nostalgic, slightly apprehensive

## Content

The rain tapped against the windows of Eleanor's apartment, creating a soothing rhythm as she sipped her morning tea. Her research notes lay scattered across the dining table—pages of half-formed theories about Melbourne's architectural history that refused to coalesce into a coherent narrative. The dissertation deadline loomed, but inspiration remained elusive.

A sharp knock at the door broke her concentration. She wasn't expecting anyone, especially not at half-past eight on a Tuesday morning.

"Delivery for Eleanor Wright," announced a damp-looking courier when she opened the door. He thrust a clipboard toward her. "Sign here, please."

Eleanor scrawled her signature and accepted a weathered cardboard box bearing her grandmother's solicitor's return address. It wasn't particularly heavy, but something inside shifted when she set it down on the table.

"Three months since the funeral," she murmured, running her fingers along the sealed edge. She hadn't expected anything from her grandmother's estate. The house and most possessions had gone to relatives in Sydney, with Eleanor receiving only a modest sum that barely covered a term's university fees.

Using a letter opener, she carefully sliced through the packaging tape. Inside, nestled among crumpled newspaper, lay a collection of items that immediately transported Eleanor back to childhood visits to her grandmother's Victorian terrace house.

A framed photograph of her grandmother as a young woman, standing proudly outside the University of Melbourne. A small leather-bound journal with faded gilt edges. A wooden jewelry box inlaid with mother-of-pearl that Eleanor had always admired as a child. And an envelope with her name written in her grandmother's elegant, sloping handwriting.

Eleanor picked up the envelope first, sliding her finger under the flap and extracting a single sheet of cream-colored stationery.

*My dearest Eleanor,*

*If you're reading this, then I have passed on, and these few treasures have found their way to you. Of all my grandchildren, you alone inherited my passion for history and its secrets. I've always seen something of myself in you—that same curiosity, that same determination to uncover truths others would prefer remained buried.*

*The items in this box may seem like mere sentimental trinkets, but look deeper. There's more here than meets the eye, especially in the jewelry box. What you find might surprise you. It certainly surprised me, all those years ago.*

*The past is never truly gone, Eleanor. Sometimes it waits patiently to be rediscovered.*

*With all my love,*
*Grandma Margaret*

Eleanor set the letter down, her hands trembling slightly. She reached for the jewelry box, memories of childhood fascination flooding back. The box had always been off-limits then—"Not a toy," her grandmother would gently scold. Now it sat before her, waiting to be opened.

The brass hinges creaked as she lifted the lid. Inside, arranged on faded velvet, lay a modest collection of jewelry—pearl earrings, a cameo brooch, a silver bracelet. Nothing that seemed particularly valuable or mysterious.

Yet her grandmother's letter had hinted at something more.

"Look deeper," Eleanor whispered, remembering the words. She ran her fingers along the edges of the velvet lining, searching for any irregularity. In the back corner, she felt it—a slight give in the material, different from the rest.

Rain continued to drum against the windows as Eleanor carefully lifted the velvet lining, revealing a hidden compartment underneath. Her breath caught in her throat.

What secrets had her grandmother kept hidden all these years? And why pass them to Eleanor now?

## Notes

Need to work on the transition between Eleanor reading the letter and examining the jewelry box—it feels a bit rushed. Also consider adding more sensory details about the items from her grandmother.
EOL

cat > "01-Projects/Example-Project/02-Manuscript/Chapters/01-Chapter-One/02-Scene-Two.md" << EOL
---
type: scene
title: "The Key"
scene-number: 2
chapter: "The Discovery"
chapter-number: 1
status: "draft" # Options: outline, draft, revision, complete
word-count: 1300
pov-character: "Eleanor Wright"
location: "Eleanor's Apartment"
time-of-day: "Morning"
weather: "Rainy"
characters:
  - "Eleanor Wright"
tags:
  - scene
created: $DATE
modified: $DATE
---

# Scene 2: The Key

## Summary

Eleanor discovers a hidden key and cryptic note in the false bottom of the jewelry box.

## Goal

Reveal the central mystery object (the key) and provide the first clue that connects to the Blackwood family.

## Setting

**Location:** Eleanor's apartment, at her dining table
**Time:** Mid-morning, continuing from the previous scene
**Weather:** Rain intensifying outside

## Characters Present

- Eleanor Wright

## Emotional Changes

- **Beginning emotion:** Curious, intrigued
- **Ending emotion:** Excited, determined, slightly anxious

## Content

The false bottom of the jewelry box lifted away easily, revealing a small hollow space beneath. Eleanor held her breath as she peered inside. Two objects lay nestled in the hidden compartment: a brass key unlike any modern design she'd seen, and a folded piece of yellowed paper.

She lifted the key first, turning it over in her palm. Heavy and ornate, it featured an unusual symbol worked into its bow—something like a tree with intertwined branches forming an almost circular pattern. The shaft was long, with complex notches and ridges that suggested a sophisticated locking mechanism. This was no ordinary house key; it had been crafted for something special.

"What did you unlock?" Eleanor whispered, as if the key might answer. She set it gently on the table and reached for the folded paper.

The sheet had been folded many times into a tight square, the creases deep and well-worn as though it had been opened and refolded countless times over the years. Eleanor carefully unfolded it, afraid the brittle paper might tear along the creases.

It was a handwritten note, the ink faded to a sepia tone, dated June 17, 1899:

*M—*

*I've secured it where no one will think to look. The key enclosed opens the compartment. Should anything happen to me, you must retrieve what's inside and keep it hidden from the Blackwoods. They must never know what their father did. The truth would destroy everything they've built, but more importantly, it would put you in grave danger.*

*Trust no one with this information. Not even James. Especially not James.*

*When the time is right, you'll know what to do with what you find.*

*—H*

Eleanor read the note twice more, her historian's mind already cataloguing the questions it raised. Who was H? And who was James? The Blackwoods, though—that name she recognized immediately. Even now, the Blackwood family remained one of Melbourne's most prominent dynasties, their name adorning university buildings, hospital wings, and cultural institutions throughout the city.

In the 1890s, when this note was apparently written, Harold Blackwood would have been at the height of his influence—a shipping magnate who'd diversified into banking and real estate just in time to weather the economic depression that had ruined so many others. Her grandmother would have been just a child then, so how did this note and key come into her possession?

Rain pounded against the windows with renewed intensity as Eleanor reached for her laptop. Her dissertation could wait; this mystery demanded immediate attention. If the note was authentic—and she had no reason to doubt it was—then it suggested the revered Blackwood family patriarch had done something so terrible that knowledge of it posed a threat to whoever possessed it.

"What did you do, Harold Blackwood?" Eleanor murmured as she typed his name into a search engine. "And why was my grandmother keeping your secret?"

As results populated her screen—the sanitised, celebratory biography of a philanthropist and visionary businessman—Eleanor felt a thrill that had been absent from her academic work for months. This wasn't just history; this was a mystery reaching forward through time, with her grandmother as an unwitting—or perhaps deliberate—bridge between past and present.

The key felt suddenly heavier in her hand, its metal warming against her skin. It wasn't just an antique curiosity; it was quite literally the key to uncovering whatever Harold Blackwood had hidden over a century ago.

Eleanor glanced at the framed photograph of her grandmother, the young woman's confident smile revealing nothing of the secrets she would eventually keep.

"I don't know what you've gotten me into, Grandma," Eleanor said to the photograph, "but I'm going to find out."

She placed the key and note carefully back into the jewelry box, her mind already formulating a research plan. The university archives would be her first stop, followed by the State Library's historical newspaper collection. She needed context, connections, anything that might illuminate the relationship between her grandmother's family and the Blackwoods.

The rain showed no signs of abating, but Eleanor hardly noticed as she gathered her research materials. For the first time in months, she felt the familiar fire of intellectual curiosity blazing within her. Whatever secrets lay buried in the past, she was determined to unearth them—regardless of who might prefer they remain hidden.

## Notes

The transition into Eleanor's research planning feels slightly rushed. Consider expanding on her emotional reaction to discovering a potential family connection to historical events. Also, might need to clarify the timeframe—if grandmother was a child in the 1890s, she'd be quite elderly when Eleanor was growing up.
EOL

# Update Example Project's Chapter Outline
cat > "01-Projects/Example-Project/01-Outline/02-Chapter-Outline.md" << EOL
---
type: chapter-outline
title: "Chapter Outline"
created: $DATE
modified: $DATE
---

# Chapter Outline

## Act 1

### Chapter 1: The Discovery

- Scene 1: The Package - Eleanor receives a package containing her grandmother's possessions
- Scene 2: The Key - Eleanor discovers a mysterious key and cryptic note hidden in a jewelry box

### Chapter 2: The Archive

- Scene 1: University Records - Eleanor researches the Blackwood family history
- Scene 2: The Photograph - Eleanor discovers an old photograph showing her grandmother with the Blackwood family

## Act 2

### Chapter 3: The Mansion

- Scene 1: Initial Visit - Eleanor visits the old Blackwood mansion, now a historical museum
- Scene 2: Meeting James - Eleanor meets James Blackwood, the family's current patriarch

### Chapter 4: Hidden Connections

- Scene 1: The Diary - Eleanor finds her grandmother's diary with more details about the past
- Scene 2: Midnight Research - Eleanor discovers disturbing information about Harold Blackwood

## Act 3

### Chapter 5: The Confrontation

- Scene 1: The Revelation - Eleanor confronts James with what she's learned
- Scene 2: The Hidden Room - Eleanor finally uses the key to open a secret compartment

### Chapter 6: The Truth

- Scene 1: Historical Justice - Eleanor decides what to do with the information she's uncovered
- Scene 2: New Beginnings - Eleanor completes her dissertation with a new understanding of history

## Notes

The outline balances the historical mystery with Eleanor's personal journey and academic growth. Consider adding a subplot involving another researcher or a potential romantic interest to add dimension.
EOL

echo "Vault generation complete!"
echo "Your Fiction Writer's Hub vault has been created in the '$VAULT_NAME' directory."
echo "Open this folder with Obsidian to start using your writing system."
```