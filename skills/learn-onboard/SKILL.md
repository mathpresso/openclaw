---
name: learn-onboard
description: Zero-config onboarding for LearnClaw learning system. Sets up the Knowledge folder structure in your Obsidian vault, initializes learning metadata, and walks you through your first capture-review cycle. Use on first run or when a user says "set up learning" or "get started with LearnClaw".
homepage: https://github.com/mathpresso/openclaw
metadata:
  {
    "openclaw":
      {
        "emoji": "🚀",
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

# Learn Onboard

Zero-config setup for the LearnClaw learning system.

## What it does

1. Detects your Obsidian vault location
2. Creates the Knowledge folder structure
3. Generates a welcome note with instructions
4. Walks you through your first knowledge capture
5. Schedules your first review for tomorrow

## Setup Process

### Step 1: Find Vault
```bash
obsidian-cli print-default --path-only
```
If no default vault, read `~/Library/Application Support/obsidian/obsidian.json` and list available vaults.

### Step 2: Create Folder Structure
```
Knowledge/
  Sources/        # Reference material
  Questions/      # Generated review questions
  Maps/           # Knowledge graph visualizations
  Plans/          # Learning plans
  Quizzes/        # Quiz results
  Analytics/      # Dashboards and reports
```

### Step 3: Create Welcome Note
Create `Knowledge/Welcome to LearnClaw.md`:

```markdown
---
created: [today]
sr_due: [tomorrow]
sr_interval: 1
sr_ease: 2.5
sr_reviews: 0
type: concept
source: system
tags: [learnclaw, getting-started]
---

# Welcome to LearnClaw

LearnClaw turns your Obsidian vault into an AI-powered learning engine.

## How it works

1. **Capture**: Tell me anything you want to learn. I'll create structured notes.
2. **Review**: I'll quiz you using spaced repetition (SM-2 algorithm).
3. **Connect**: I automatically find relationships between your notes.
4. **Analyze**: Track your learning progress with visual dashboards.

## Quick Commands

- "Save this to my knowledge base: [content]"
- "Let's review" or "Quiz me"
- "Find connections in my notes"
- "Show my learning stats"
- "I want to learn [topic]"

## Your First Task

Try capturing something! Tell me one thing you learned today.
```

### Step 4: First Capture Demo
Guide the user through capturing their first piece of knowledge.

### Step 5: Confirm Setup
```
LearnClaw is ready!

Vault: [vault-path]
Knowledge folder: [vault-path]/Knowledge/
First review scheduled: tomorrow

Say "let's review" tomorrow to start your first review session.
```

## Usage

```
"Set up LearnClaw"
"Get started with learning"
"Initialize my knowledge base"
```

## Existing Vault Detection

If `Knowledge/` folder already exists with sr_metadata notes:
- Skip setup
- Report current stats: X notes, Y due for review
- Offer to run a review or capture new knowledge
