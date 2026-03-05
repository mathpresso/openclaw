# LearnClaw Design - 2026-03-05

## Vision
OpenClaw for Every Learner - 범용 학습자를 위한 AI 학습 최적화 에이전트

## Target
범용 학습자 (개발자, 학생, 지식 노동자) - 오픈소스 커뮤니티 성장 + Mathpresso 브랜드/채용 효과

## Core Differentiators
1. **Zero-config**: 설치 즉시 학습 에이전트 작동 (DIY 셋업 고통 제거)
2. **AI-Native Spaced Repetition**: SM-2 + LLM 기반 contextual review
3. **Knowledge Graph**: 자동 관계 발견 + gap analysis
4. **Learning Analytics**: HTML dashboard + weekly reports

## Architecture
- OpenClaw fork (TypeScript, MIT license)
- 7 built-in learning skills (SKILL.md format)
- Obsidian vault as local-first storage
- All data as plain Markdown with YAML frontmatter

## Skills Created

| Skill | Purpose | Key Feature |
|-------|---------|-------------|
| learn-capture | 지식 캡처 | Auto-wikilink + SR metadata |
| learn-review | 복습 | SM-2 algorithm + AI questions |
| learn-connect | 연결 발견 | Semantic analysis + Mermaid maps |
| learn-quiz | 퀴즈 | Adaptive difficulty |
| learn-analytics | 분석 | HTML dashboard + Chart.js |
| learn-plan | 학습 계획 | Prerequisite mapping + milestones |
| learn-onboard | 초기 설정 | Zero-config vault setup |

## Repo
- Fork: https://github.com/mathpresso/openclaw
- Branch: feat/learnclaw

## Next Steps
1. Rename repo to `learnclaw` (GitHub settings)
2. Update package.json name/description
3. Create onboarding CLI command
4. Build HTML analytics dashboard template
5. Community launch (README, social media)
