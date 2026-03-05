---
name: learn-capture
description: Capture knowledge from any source into your Obsidian vault as structured learning nodes. Automatically extracts key concepts, creates wikilinks to related notes, and adds spaced repetition metadata. Use when a user shares content to learn, highlights text, or asks to save knowledge.
homepage: https://github.com/mathpresso/openclaw
metadata:
  {
    "openclaw":
      {
        "emoji": "🧠",
        "requires": { "bins": ["obsidian-cli"] },
        "install":
          [
            {
              "id": "brew",
              "kind": "brew",
              "formula": "yakitrak/yakitrak/obsidian-cli",
              "bins": ["obsidian-cli"],
              "label": "Install obsidian-cli (brew)",
            },
          ],
      },
  }
---

# Learn Capture

Capture knowledge into your Obsidian vault as structured learning nodes.

## What it does

When a user shares content (article, video summary, conversation insight, book highlight), this skill:

1. Extracts key concepts and creates a structured note
2. Auto-generates `[[wikilinks]]` to existing related notes in the vault
3. Adds spaced repetition frontmatter for the review engine
4. Tags the note with topic taxonomy

## Note Structure

Every captured note follows this template:

```markdown
---
created: YYYY-MM-DD
sr_due: YYYY-MM-DD
sr_interval: 1
sr_ease: 2.5
sr_reviews: 0
type: concept | fact | procedure | principle
source: user-input | article | book | video | conversation
tags: [topic1, topic2]
---

# [Title]

## Summary
[2-3 sentence summary]

## Key Points
- Point 1
- Point 2

## Connections
- Related to [[existing-note-1]]
- Builds on [[existing-note-2]]

## Review Questions
- Q: [Question about this concept]
  A: [Answer]
```

## Usage

Capture from text:
```
"Save this to my knowledge base: [content]"
"I learned that [concept]. Remember this."
"Add these notes from my reading: [highlights]"
```

Capture from URL (if browser skill available):
```
"Learn from this article: [url]"
"Extract key points from [url]"
```

## Vault Location

Uses the default Obsidian vault. Notes are saved to:
- `Knowledge/` folder for concepts
- `Knowledge/Sources/` for source material references
- `Knowledge/Questions/` for generated review questions

## Finding Related Notes

Before creating a new note, search the vault:
1. `obsidian-cli search-content "key concept"` to find related notes
2. Read top matches to generate accurate `[[wikilinks]]`
3. If a note on the same concept exists, update it instead of creating a duplicate

## Spaced Repetition Metadata

- `sr_due`: next review date (starts as creation date + 1 day)
- `sr_interval`: days until next review (starts at 1)
- `sr_ease`: difficulty multiplier (starts at 2.5, SM-2 algorithm)
- `sr_reviews`: total number of reviews completed
