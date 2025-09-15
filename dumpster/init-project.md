---
description: initialize the workspace for a new novel project
argument-hint: [project-title]
allowed-tools: Bash(mkdir:*), Bash(touch:*)
---

Initialize a new project workspace in the root `./projects` with the directory structure:

```
$1/
  author-notes/
  content/
    outlines/
    drafts/
    manuscript/
  workspace/
  story-bible.json
  README.md
```

## Story Bible

For the `story-bible.json` document, use the following template:

```json
{
  "storyBible": {
    "voiceSpec": {
      "comparables": ["string"],
      "do": ["string"],
      "dont": ["string"]
    },
    "canon": {
      "setting": "string",
      "era": "string",
      "tech": "string"
    },
    "constraints": {
      "pov": "string",
      "tense": "string",
      "max_tokens": "number"
    },
    "characters": {
      "characterProfiles": [
        {
          "name": "string",
          "role": "string",
          "storyGoal": "string",
          "age": "number",
          "gender": "string",
          "physicalTraits": {
            "eyeColor": "string",
            "hairStyle": "string",
            "scarsTattoos": "string",
            "mannerisms": "string"
          },
          "personality": {
            "strengths": "string",
            "flaws": "string",
            "fears": "string",
            "motivations": "string",
            "quirks": "string"
          },
          "backstory": "string",
          "relationships": [
            {
              "characterName": "string",
              "relationshipType": "string"
            }
          ],
          "characterArc": "string",
          "visuals": ["imageURL"]
        }
      ]
    },
    "settings": {
      "locations": [
        {
          "name": "string",
          "description": "string",
          "maps": ["imageURL"]
        }
      ],
      "culture": {
        "socialNorms": "string",
        "traditions": "string",
        "languages": ["string"],
        "government": "string"
      },
      "history": "string",
      "rules": {
        "magicSystem": "string",
        "technology": "string",
        "lawsOfNature": "string"
      },
      "uniqueTerms": {
        "term": "definition"
      }
    },
    "plot": {
      "storylines": {
        "AStory": "string",
        "BStory": "string",
        "CStory": "string"
      },
      "timeline": {
        "events": [
          {
            "eventName": "string",
            "dateOrSequence": "string",
            "description": "string"
          }
        ],
        "characterTimelines": [
          {
            "characterName": "string",
            "importantDates": [
              {
                "event": "string",
                "date": "string"
              }
            ]
          }
        ]
      },
      "narrativeSummary": "string"
    },
    "researchNotes": ["string"],
    "additionalElements": {
      "maps": ["imageURL"],
      "moodBoards": ["imageURL"],
      "photos": ["imageURL"],
      "referenceLinks": ["string"]
    }
  }
}
```

## README

For the `README.md` document, use the following template:

```md
# Project Title

A concise, descriptive title of the novel or series.

## Overview

A brief summary describing the novel's genre, themes, and central premise.

## Motivation

Why the novel is being written, its inspiration, or what makes it unique.

## Current Status

Progress update (e.g., planning, writing draft, editing, published).

## Recent Progress

A concise timeline of the work done on the novel thus far (example, a `git status --oneline` format)
```
