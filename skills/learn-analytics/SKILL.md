---
name: learn-analytics
description: Visualize your learning patterns and progress. Generates HTML dashboards showing knowledge growth, review streaks, topic distribution, and retention curves from your Obsidian vault data. Use when a user asks about their learning progress, stats, or wants to see a dashboard.
homepage: https://github.com/mathpresso/openclaw
metadata:
  {
    "openclaw":
      {
        "emoji": "📊",
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

# Learn Analytics

Visualize your learning journey with data-driven insights.

## What it does

1. Scans vault for all notes with learning metadata (sr\_\* frontmatter)
2. Calculates learning statistics and trends
3. Generates an HTML dashboard with interactive charts
4. Provides actionable recommendations

## Metrics Tracked

### Core Metrics

- **Total knowledge nodes**: count of notes with sr_metadata
- **Notes due today**: notes where sr_due <= today
- **Review streak**: consecutive days with at least 1 review
- **Retention rate**: % of reviews with quality >= 3

### Growth Metrics

- **Notes created per week**: knowledge acquisition rate
- **Connections per note**: average wikilinks (knowledge density)
- **Topic distribution**: breakdown by tags

### Health Metrics

- **Overdue notes**: notes past their sr_due date
- **Struggling notes**: notes with sr_ease < 2.0
- **Mature notes**: notes with sr_interval > 30 days

## Usage

```
"Show my learning stats"
"How am I doing?"
"Learning dashboard"
"What topics do I know best?"
"Show my review streak"
"Weekly learning report"
```

## Dashboard Generation

Use the template at `skills/learn-analytics/dashboard-template.html` to generate `Knowledge/Analytics/dashboard.html`.

1. Read the template file
2. Replace all `{{PLACEHOLDER}}` tokens with computed data:
   - `{{GENERATED_DATE}}`: current date/time
   - `{{VAULT_PATH}}`: detected vault path
   - `{{TOTAL_NOTES}}`, `{{NEW_THIS_WEEK}}`, `{{DUE_TODAY}}`, `{{OVERDUE}}`: note counts
   - `{{STREAK}}`, `{{BEST_STREAK}}`: review streak days
   - `{{RETENTION}}`, `{{MATURE_NOTES}}`: retention stats
   - `{{GROWTH_LABELS}}`, `{{GROWTH_VALUES}}`: weekly note counts (quoted strings, numbers)
   - `{{TOPIC_LABELS}}`, `{{TOPIC_VALUES}}`: tag distribution
   - `{{RETENTION_LABELS}}`, `{{RETENTION_VALUES}}`: weekly retention %
   - `{{UPCOMING_LABELS}}`, `{{UPCOMING_VALUES}}`: next 14 days review counts
   - `{{HEATMAP_VALUES}}`: 84 integers (12 weeks x 7 days, 0-4 scale)
   - `{{REC_FOCUS}}`, `{{REC_STREAK}}`, `{{REC_CONNECTIONS}}`: recommendation text
3. Write the filled template to `Knowledge/Analytics/dashboard.html`
4. Open it: `open Knowledge/Analytics/dashboard.html`

Charts included: Knowledge Growth (line), Topic Distribution (doughnut), Retention Curve (line), Upcoming Reviews (bar), Review Activity Heatmap (GitHub-style)

## Data Collection

To gather stats, scan the vault:

1. Find all notes with sr_metadata:

   ```bash
   obsidian-cli search-content "sr_due:"
   ```

2. For each note, read and parse frontmatter for:
   - `created`, `sr_due`, `sr_interval`, `sr_ease`, `sr_reviews`
   - `tags`, `type`, `source`

3. Read quiz results from `Knowledge/Quizzes/`

4. Count `[[wikilinks]]` in each note for connection density

## Weekly Report

Generate `Knowledge/Analytics/weekly-[date].md`:

```markdown
# Weekly Learning Report - [Date Range]

## Summary

- New notes: X (+Y% from last week)
- Reviews completed: X
- Retention rate: X%
- Streak: X days

## Top Topics This Week

1. [Topic] - X new notes, Y reviews
2. [Topic] - X new notes, Y reviews

## Struggling Areas

- [[Note]] (ease: 1.5) - reviewed X times, still difficult

## Recommendations

1. Focus on [topic] - several notes overdue
2. Great progress on [topic] - consider exploring [related-topic]
3. Review streak at risk - X notes due tomorrow
```

## Recommendations Engine

Based on analytics, suggest:

- **What to learn next**: topics with few notes but many references
- **What to review**: high-value notes that are overdue
- **What to connect**: isolated note clusters
- **When to study**: optimal review time based on past patterns
