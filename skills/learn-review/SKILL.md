---
name: learn-review
description: AI-powered spaced repetition review engine. Finds notes due for review in your Obsidian vault using SM-2 algorithm, generates contextual quizzes, and updates review metadata based on recall quality. Use when a user wants to review, study, or practice what they've learned.
homepage: https://github.com/mathpresso/openclaw
metadata:
  {
    "openclaw":
      {
        "emoji": "🔄",
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

# Learn Review

Spaced repetition review engine powered by AI + SM-2 algorithm.

## What it does

1. Scans vault for notes with `sr_due` <= today
2. Presents review cards with AI-generated questions
3. Evaluates recall quality (0-5 scale)
4. Updates SM-2 metadata (interval, ease, due date)

## SM-2 Algorithm Implementation

After each review, update the note's frontmatter:

```
quality: 0-5 (user self-assessment or AI-evaluated)
  0 = complete blackout
  1 = incorrect, but recognized on reveal
  2 = incorrect, but easy to recall after reveal
  3 = correct with difficulty
  4 = correct with some hesitation
  5 = perfect recall

if quality >= 3 (pass):
  if reviews == 0: interval = 1
  if reviews == 1: interval = 6
  if reviews >= 2: interval = round(interval * ease)
  ease = max(1.3, ease + (0.1 - (5 - quality) * (0.08 + (5 - quality) * 0.02)))
  reviews += 1

if quality < 3 (fail):
  interval = 1
  reviews = 0
  (ease unchanged)

sr_due = today + interval days
```

## Review Session Flow

1. Find due notes:
   ```bash
   # Search for notes with sr_due in frontmatter
   obsidian-cli search-content "sr_due:"
   ```
   Then parse each result and compare `sr_due` with today's date.

2. For each due note:
   - Read the full note content
   - Generate a contextual question (not just the stored Q&A)
   - Present to user and wait for answer
   - Evaluate quality (AI judges correctness)
   - Update frontmatter with new SM-2 values

3. Session summary:
   ```
   Review Complete!
   - Reviewed: 12 notes
   - Passed: 10 (83%)
   - Failed: 2 (will review tomorrow)
   - Next review: 3 notes due tomorrow
   ```

## Usage

```
"Let's review" / "Study time" / "What should I review today?"
"Review my notes on [topic]"
"Quick review - 5 minutes"
"How many notes are due for review?"
```

## Smart Features

- **Contextual questions**: AI generates varied questions each review, not just repeating stored Q&A
- **Connection testing**: Sometimes asks "How does [[note-A]] relate to [[note-B]]?"
- **Difficulty adjustment**: If a note is consistently easy (ease > 3.0), reduces question complexity
- **Time-boxed sessions**: "5 minute review" limits to estimated number of cards

## Updating Notes

After review, update the note's YAML frontmatter in-place:
```bash
# Read the note, update frontmatter, write back
# Use direct file editing (read .md, modify, save)
```
Do NOT create new notes for reviews. Modify the existing note's frontmatter only.
