---
name: session:resume
description: Display highlighted session context and automatically create actionable tasks from outstanding items to effectively resume previous work.
parameters: []
---

Please help resume work by displaying the most recent session summary, analyzing referenced materials through subagents, and directing resumption of the highest priority work.

## Session Resume Process

1. **Locate recent session file**: Find the most recent file in `.claude/memory/sessions/` with pattern `[YYYY-MM-DD]-*.md`

2. **Display full summary**: Show the complete content of the last session file

3. **Highlight key sections**: Add clear visual markers to emphasize important information:
   - **Outstanding Tasks & Next Steps** - what should be worked on next
   - **Current State** - where things stand currently
   - **Issues & Blockers Encountered** - any unresolved challenges
   - **Critical Context** and **Technical Context to Remember** - important background

4. **Extract and create tasks**: Parse the "Outstanding Tasks & Next Steps" section and create tasks using the TaskCreate tool for each identified next step, making them actionable work items

5. **Launch Analysis Subagents**: After displaying the summary and creating tasks, actively resume work by launching specialized subagents to analyze referenced files and task state:
   - **Reference Parser Agent**: Parses summary for file references, plan locations, and task references
   - **Task Creation Agent**: Extracts tasks from "Outstanding Tasks & Next Steps" section and creates them automatically
   - **Plan/Task Finder Agent**: Scans standard directories (~/.claude/plans/, ~/.claude/tasks/, project equivalents) for referenced materials
   - **Git Context Agent**: Checks current git status and recent commit history
   - **Content Reader Agent**: Reads all referenced plans, tasks, and context files autonomously

6. **Resume Work**: Based on subagent analysis and newly created tasks, direct Claude to begin working on the highest priority next steps identified from plans, tasks, and git context.

7. **If no session files exist**: Inform the user that no previous sessions are available and suggest using `/session:summarize` after doing some work.

## Subagent Design

### Task Creation Agent
- Input: Session summary content, specifically "Outstanding Tasks & Next Steps" section
- Task: Parse the Outstanding Tasks & Next Steps section to extract individual actionable items, and create tasks using TaskCreate tool for each one
- Output: List of created task IDs with their subjects and descriptions

### Reference Parser Agent
- Input: Session summary content
- Task: Extract file references, plan locations, task references
- Output: Structured list of files to read, plan files to find, task references to locate

### Plan/Task Finder Agent
- Input: Reference list from parser
- Task: Scan standard directories (~/.claude/plans/, ~/.claude/tasks/, project equivalents)
- Output: Found files with their locations and modification dates

### Git Context Agent
- Input: Current working directory, recent session context
- Task: Run git status, recent log (last 5-10 commits)
- Output: Current branch state, recent changes, uncommitted work

### Content Reader Agent
- Input: File list from finder agent
- Task: Read all referenced plans, tasks, and context files
- Output: Summarized content from all relevant materials

## Presentation Format

Structure the response to clearly indicate this is from a previous session, with the filename date/topic clearly identified at the top, followed by the full summary content with highlighted key sections. After displaying the summary and creating tasks from the outstanding items, launch the analysis subagents and provide direction for resuming the highest priority work.

The goal is to provide comprehensive context while actively resuming progress on pending work through task creation and subagent analysis.