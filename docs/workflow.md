# Workflow

1. **Install Plugin**: `/plugin install <repository-url>`
2. **Setup Project**: In your project: `/session:setup`
3. **Work Session**: Have discussions, make technical progress, strategize
4. **Generate Summary**: Run `/session:summarize` when reaching natural breakpoints
5. **End Session**: Clear context, exit Claude Code
6. **Resume Later**: Start new session with `/session:resume` to regain full context

## Directory Structure

```
.claude/
├── plugin.json                          # Plugin manifest
└── memory/sessions/                     # (created after setup)
    ├── session-summary-template.md      # Comprehensive template
    └── YYYY-MM-DD-topic-name.md         # Generated summaries
```