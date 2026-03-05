# LearnClaw — AI-Powered Learning Agent

> OpenClaw for Every Learner. Capture, review, connect, and master knowledge from your messaging apps.

<p align="center">
  <a href="https://github.com/mathpresso/learnclaw"><img src="https://img.shields.io/badge/LearnClaw-v2026.3.3-58a6ff?style=for-the-badge" alt="LearnClaw"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
  <a href="https://github.com/openclaw/openclaw"><img src="https://img.shields.io/badge/Built_on-OpenClaw-f85149?style=for-the-badge" alt="Built on OpenClaw"></a>
</p>

**LearnClaw** is a fork of [OpenClaw](https://github.com/openclaw/openclaw) specialized for **learning optimization**. It combines a local-first AI agent with cognitive science (spaced repetition, knowledge graphs) to help every learner maximize retention and understanding.

Your data stays local in your Obsidian vault as plain Markdown.

## Why LearnClaw?

OpenClaw + Obsidian is powerful but requires manual setup. LearnClaw makes it **zero-config**:

| Feature            | OpenClaw + DIY           | LearnClaw                                   |
| ------------------ | ------------------------ | ------------------------------------------- |
| Knowledge capture  | Manual note-taking       | AI-structured notes with auto-linking       |
| Spaced repetition  | External app (Anki)      | Built-in SM-2 engine                        |
| Knowledge graph    | Obsidian graph view only | AI-discovered connections + gap analysis    |
| Learning analytics | None                     | Interactive HTML dashboard + weekly reports |
| Study planning     | Manual                   | AI-generated learning paths with milestones |
| Quizzes            | None                     | Adaptive AI-generated quizzes               |

## Quick Start

```bash
# Install (requires Node 22+)
npm install -g learnclaw@latest

# Onboard
learnclaw onboard --install-daemon

# Set up (in WhatsApp/Telegram/Slack)
> "Set up LearnClaw"
```

That's it. Your AI learning agent is ready.

## Built-in Learning Skills

### learn-capture

Capture knowledge from any source. AI extracts key concepts, creates structured Obsidian notes with wikilinks, and adds spaced repetition metadata.

### learn-review

SM-2 spaced repetition engine. Finds notes due for review, generates contextual questions, evaluates your recall, and optimizes review intervals.

### learn-connect

Knowledge graph builder. Discovers semantic relationships between notes, suggests missing connections, identifies knowledge gaps, generates Mermaid diagrams.

### learn-quiz

Adaptive quiz generator. Creates multiple-choice, fill-in-the-blank, and open-ended questions. Adjusts difficulty based on your history.

### learn-analytics

Learning dashboard. Generates interactive HTML visualizations: knowledge growth, review streaks, topic distribution, retention curves, and recommendations.

### learn-plan

Learning path creator. Breaks down goals into structured milestones, maps prerequisites, estimates time, and tracks progress.

### learn-onboard

Zero-config setup. Creates Knowledge folder structure in your Obsidian vault, generates welcome note, walks you through first capture-review cycle.

## Architecture

```
LearnClaw (OpenClaw fork)
+-- All OpenClaw features (messaging, tools, gateway)
+-- 7 built-in learning skills (SKILL.md format)
+-- Obsidian-native knowledge storage
+-- SM-2 spaced repetition engine

Your data stays local:
Obsidian Vault/
  Knowledge/
    [your notes with sr_metadata]
    Sources/
    Questions/
    Maps/        (Mermaid diagrams)
    Plans/       (learning paths)
    Quizzes/     (quiz results)
    Analytics/   (HTML dashboards)
```

## The Science

LearnClaw is built on proven learning science:

- **Spaced Repetition (SM-2)**: Review at optimal intervals to maximize long-term retention
- **Active Recall**: AI-generated questions force retrieval, strengthening memory
- **Elaborative Interrogation**: Connection discovery deepens understanding
- **Interleaving**: Mixed-topic reviews improve transfer learning
- **Knowledge Graphs**: Visual maps build structural understanding

## All OpenClaw Features Included

LearnClaw inherits everything from OpenClaw:

- Multi-channel support (WhatsApp, Telegram, Slack, Discord, Signal, iMessage, and more)
- Local-first architecture with full privacy
- Extensible skill system
- macOS/iOS/Android apps
- Web UI and Canvas

See the [OpenClaw docs](https://docs.openclaw.ai) for the full feature set.

## Contributing

LearnClaw is open source (MIT). We welcome contributions:

1. Fork the repo
2. Create a feature branch
3. Submit a PR

Areas we'd love help with:

- New learning skill ideas
- Language support (i18n)
- Integration with more note-taking apps
- Learning science research integration

## Credits

- Built on [OpenClaw](https://github.com/openclaw/openclaw) by Peter Steinberger
- Maintained by [Mathpresso](https://github.com/mathpresso)
- SM-2 algorithm by Piotr Wozniak

## License

MIT (same as OpenClaw)
