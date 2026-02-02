# Commands

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