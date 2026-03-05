---
name: learn-plan
description: Create personalized learning paths and study plans. Breaks down learning goals into structured milestones, maps prerequisites, estimates time, and tracks progress in your Obsidian vault. Use when a user wants to learn something new, plan their study, or set learning goals.
homepage: https://github.com/mathpresso/openclaw
metadata:
  {
    "openclaw":
      {
        "emoji": "🗺️",
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

# Learn Plan

Create and track personalized learning paths.

## What it does

1. Takes a learning goal from the user
2. Breaks it down into topics and subtopics
3. Maps prerequisite relationships
4. Creates a structured learning plan with milestones
5. Tracks progress as the user learns

## Usage

```
"I want to learn [topic]"
"Create a learning plan for [subject]"
"How should I study [topic] from scratch?"
"Plan 30 days of learning [subject]"
"What should I learn next to understand [advanced-topic]?"
```

## Learning Plan Structure

Creates `Knowledge/Plans/[topic]-plan.md`:

```markdown
---
goal: "[Learning goal]"
created: YYYY-MM-DD
target_date: YYYY-MM-DD
status: active
progress: 0
total_milestones: 8
completed_milestones: 0
---

# Learning Plan: [Topic]

## Goal
[What the user wants to achieve]

## Prerequisites
- [ ] [[Prerequisite 1]] - [status: known/unknown/in-progress]
- [ ] [[Prerequisite 2]]

## Learning Path

### Phase 1: Foundations (Week 1-2)
- [ ] **Milestone 1.1**: [Topic] - Est. 2 hours
  - Resources: [suggested resources]
  - Key concepts: [list]
  - Success criteria: Can explain [concept] in own words

- [ ] **Milestone 1.2**: [Topic] - Est. 3 hours
  ...

### Phase 2: Core Concepts (Week 3-4)
- [ ] **Milestone 2.1**: [Topic]
  - Prerequisite: Milestone 1.1, 1.2
  ...

### Phase 3: Application (Week 5-6)
- [ ] **Milestone 3.1**: [Project/Exercise]
  ...

## Progress Tracking
| Week | Target | Actual | Notes |
|------|--------|--------|-------|
| 1    |        |        |       |
```

## Smart Features

### Prerequisite Detection
- Checks existing vault notes to identify what the user already knows
- Adjusts plan difficulty based on existing knowledge
- Skips topics that are already well-reviewed (sr_ease > 3.0)

### Adaptive Scheduling
- If user falls behind, redistributes remaining milestones
- Suggests catch-up sessions for overdue milestones
- Adjusts pace based on quiz performance

### Resource Suggestions
- Searches web for high-quality free resources (if web search available)
- Prioritizes interactive/practical resources
- Suggests mix of theory and practice

## Progress Updates

When user completes a milestone:
1. Update the plan's checkbox and progress counter
2. Create knowledge notes for concepts learned (via learn-capture)
3. Schedule spaced repetition reviews
4. Suggest next milestone

```
"I finished milestone 1.1"
"Update my learning plan"
"How am I progressing on [topic]?"
```

## Integration with Other Learn Skills

- **learn-capture**: Creates notes for each milestone's key concepts
- **learn-review**: Schedules reviews for learned material
- **learn-connect**: Maps new knowledge to existing graph
- **learn-quiz**: Tests milestone completion
- **learn-analytics**: Shows plan progress in dashboard
