---
name: learn-quiz
description: Generate interactive quizzes from your Obsidian vault notes. Creates multiple-choice, fill-in-the-blank, and open-ended questions based on your knowledge base. Adapts difficulty based on review history. Use when a user wants to test themselves or practice for exams.
homepage: https://github.com/mathpresso/openclaw
metadata:
  {
    "openclaw":
      {
        "emoji": "❓",
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

# Learn Quiz

Generate adaptive quizzes from your knowledge base.

## What it does

1. Reads notes from your Obsidian vault
2. Generates varied question types based on note content
3. Adapts difficulty based on your review history (sr_ease)
4. Records results and updates spaced repetition metadata

## Question Types

### Multiple Choice
```
Q: Which design pattern uses a single instance shared across the application?
A) Observer  B) Singleton  C) Factory  D) Strategy
Answer: B
```

### Fill in the Blank
```
Q: The SM-2 algorithm uses an _____ factor that starts at 2.5 to determine review intervals.
Answer: ease
```

### Open-ended (AI-evaluated)
```
Q: Explain the difference between composition and inheritance. When would you prefer one over the other?
[User answers freely, AI evaluates completeness]
```

### Connection Questions
```
Q: How does [[Concept A]] relate to [[Concept B]]?
[Tests understanding of relationships in knowledge graph]
```

## Usage

```
"Quiz me on [topic]"
"Test my knowledge about [subject]"
"Give me 10 questions about [topic]"
"Hard quiz on everything I learned this week"
"Practice exam: [subject]"
```

## Difficulty Adaptation

Based on note's `sr_ease` value:
- ease > 3.0 (well-known): harder questions, connection-type, open-ended
- ease 2.0-3.0 (moderate): mix of multiple-choice and fill-in-blank
- ease < 2.0 (struggling): easier multiple-choice, more hints

## Quiz Session Flow

1. Determine scope (topic, folder, or all notes)
2. Select notes based on criteria (due for review, topic match, weak areas)
3. Generate questions with appropriate difficulty
4. Present one at a time, wait for answer
5. Evaluate and give immediate feedback with explanation
6. Update sr_metadata on the source note
7. Summary with score and recommendations

## Quiz Results

Save session results to `Knowledge/Quizzes/quiz-[date].md`:

```markdown
---
date: YYYY-MM-DD
topic: [topic or "mixed"]
score: 8/10
duration: 12min
---

# Quiz Results - [Date]

Score: 8/10 (80%)

## Correct
1. [Question] - from [[Note]]
...

## Needs Review
1. [Question] - from [[Note]] - Review this concept

## Recommendations
- Revisit [[weak-note-1]] - ease dropped to 1.8
- Strong on [[topic]] - consider advancing to related topics
```
