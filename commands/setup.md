---
name: session:setup
description: Initialize session management utilities by creating the required directory structure and template file in the current project.
parameters: []
---

Initialize session management utilities for the current project by creating directory structure and template file.

Run the following sequence in bash to set up session tracking:

```bash
mkdir -p .claude/memory/sessions
```

Create the session summary template:

```bash
cat > .claude/memory/sessions/session-summary-template.md << 'EOF_TEMPLATE'
# Session: [YYYY-MM-DD] - [Topic Name]

## Goals & Objectives
[What we set out to accomplish in this session. Strategic objectives beyond just coding tasks.]

## Previous Session Analysis
[What was accomplished in previous sessions related to this work. Key learnings carried forward.]

## Key Decisions Made
- [Decision 1 and rationale]
- [Decision 2 and rationale]
- [etc.]

## Current Work Plan
1. [Immediate next action to address]
2. [Following prioritized action]
3. [Additional tasks for this session]
4. [etc.]

## Work Completed
- [✅ Task 1 that was finished]
- [✅ Task 2 that was finished]
- [etc.]

## Work In Progress
- [🔄 Task that's partially done]
- [🔄 etc.]

## Outstanding Tasks & Next Steps
1. [Immediate next action to take after this session]
2. [Second priority action]
3. [Third if needed]
4. [Future considerations]

## Issues & Blockers Encountered
- [Any challenges, errors, or strategic obstacles that impacted progress]
- [External dependencies or constraints discovered]
- [Or "None - smooth session" if applicable]

## Discussion Insights
- [Important concepts and strategic thinking that emerged during conversation]
- [Key learnings, patterns, or architectural insights discovered]
- [Strategic decisions or approaches that shaped the work]

## Technical Context to Remember
- **Files modified:** [list key files with brief impact]
- **Configuration changes:** [any config updates made]
- **Dependencies added:** [new libraries or external services]
- **Patterns/approaches established:** [coding patterns, architectural decisions implemented]
- **Important commands/scripts:** [frequently used commands or automation tools]
- **Infrastructure changes:** [environment, deployment, or tooling updates]
- **Related plans/tasks:** [Reference to plan files (~/.claude/plans/ or project plans/) and task storage locations (~/.claude/tasks/ or project tasks/)]

## Current State
[Brief description of where things stand - what works, what's tested, what's ready for integration/launch]
EOF_TEMPLATE
```

Usage: Run this command after installing the plugin to set up session management utilities in your project. The setup creates the `.claude/memory/sessions/` directory with the session summary template file.