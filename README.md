# Session Utils Plugin

Enhanced session management utilities for Claude Code with intelligent summarization capabilities. Builds on session memory concepts with autonomous agents for comprehensive analysis.

## Features

- **Manual Command Interface**: Clean user commands for session management operations
- **Autonomous Summarization Agent**: Advanced agent that analyzes conversations and creates structured summaries
- **Context Preservation**: Maintains strategic memory across development sessions
- **Template-Driven Structure**: Consistent, comprehensive session documentation
- **Local Project Storage**: Session files stored within your project directories

## Installation

Install globally in Claude Code:

```bash
/plugin install https://github.com/YOUR_USERNAME/session-utils
```

Replace `YOUR_USERNAME` with your GitHub username.

## Commands

### `/session:setup`
Initialize session management utilities in the current project by creating:
- `.claude/memory/sessions/` directory structure
- `session-summary-template.md` template file

### `/session:summarize`
Trigger the intelligent summarization agent to:
- Analyze the entire current session conversation
- Extract strategic decisions, technical work, and insights
- Generate a comprehensive summary following the template format
- Save to `.claude/memory/sessions/YYYY-MM-DD-topic-name.md`

### `/session:resume`
Display context from the most recent session to continue work:
- Shows the complete last session summary
- Highlights key sections (outstanding tasks, current state, critical context)
- Helps pick up where previous work left off

## Agent Architecture

### Session Summarizer Agent
- **Triggering**: Activates on `/session:summarize` commands or direct summarization requests
- **Capabilities**: Comprehensive conversation analysis, structured writing, file management
- **Scope**: Analyzes all session content to populate template sections
- **Output**: Formatted markdown summaries with technical and strategic insights

## Workflow

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

## Summary Template Sections

Each session summary includes:
- **Goals & Objectives**: Strategic objectives beyond coding tasks
- **Previous Session Analysis**: Learnings from prior work
- **Key Decisions Made**: Important choices and rationales
- **Work Completed**: ✅ Finished tasks and deliverables
- **Outstanding Tasks & Next Steps**: Prioritized action items
- **Issues & Blockers**: Challenges encountered
- **Technical Context**: Files modified, configurations, dependencies
- **Current State**: Assessment of project status

## Testing the Plugin

### Local Testing
```bash
# Test in current project
cc --plugin-dir /home/agrohe/projects/session-utils

# Or copy to global plugin location
cp -r /home/agrohe/projects/session-utils ~/.claude/plugins/
```

### Verification Checklist
- [ ] `/session:setup` creates directory and template file
- [ ] `/session:summarize` triggers agent and generates summary file
- [ ] `/session:resume` displays recent session context
- [ ] Summary file follows template structure
- [ ] Agent works autonomously in separate context

## Strategic Benefits

Unlike basic notes, this plugin captures:
- **Strategic discussions** and decision rationales
- **Mental context** from conversations
- **Technical continuity** across sessions
- **Executive thinking** about problems and solutions
- **Development workflow insights**

## Requirements

- Claude Code with Claude Opus 4.5 or later
- Projects using Git for version control recommended

## Differences from Original

- Commands prefixed with `session:` for clarity
- Intelligent agent for autonomous summarization
- Enhanced conversation analysis capabilities
- Focused on session management utility functions

## Next Steps

1. Test the plugin locally with sample conversations
2. Customize the summary template if needed
3. Publish to marketplace when ready
4. Consider extending with additional utilities

## License

MIT License - see LICENSE file for details.