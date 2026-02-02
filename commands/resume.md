---
name: session:resume
description: Display highlighted session context and automatically create actionable tasks from outstanding items to effectively resume previous work.
parameters: [{"name":"auto-confirm","description":"Skip user confirmation and automatically create all found tasks (default: false)","type":"boolean"}]
---

Help resume previous work sessions by displaying context, extracting actionable tasks, and launching analysis subagents.

**Step 1: Locate Most Recent Session**
Find the newest session summary file by listing files in `.claude/memory/sessions/` and selecting the most recent modification date.

**Step 2: Display Session Summary**
Read and display the complete session summary with clear section highlighting using markdown headers and emphasis.

**Step 3: Extract Outstanding Tasks**
Use Grep to find numbered or bulleted items in the "Outstanding Tasks & Next Steps" section of the session file.

**Step 4: Check Confirmation Settings**
Read `.claude-plugin/settings.local.json` to check the `plugins.session-utils.resume.autoConfirmTasks` setting.

**Step 5: User Confirmation Workflow**
If autoConfirmTasks is false, use AskUserQuestion to present extracted tasks for user approval with multi-select options.

**Step 6: Create Approved Tasks**
For each user-approved task, use TaskCreate to create actionable work items with appropriate subjects and descriptions.

**Step 7: Launch Analysis Subagents**
Execute analysis subagents to gather additional context:

**Launch Reference Analysis Subagent:**
Use Task tool with Explore subagent to examine referenced files and plans:
```
subagent_type: Explore
description: "Extract and analyze file references from session summary"
prompt: "Find all file paths, plan references, and technical context mentioned in: [session_content]"
```

**Launch Git Context Analysis:**
Use Bash commands to assess current repository state:
- **`git status --porcelain`** to check working directory changes
- **`git branch --show-current`** to identify current branch
- **`git log --oneline -3`** to review recent commits

**Launch Plan/Task Review Subagent:**
Use Task tool with general-purpose subagent to analyze plan and task state:
```
subagent_type: general-purpose
description: "Analyze referenced plans and evaluate task status"
prompt: "Check for any plans or task files referenced in this session and assess their current validity: [session_content]"
```

**Step 8: Coordinate Subagent Results**
Combine findings from all subagents to create a comprehensive resumption strategy:

**Integration Analysis:**
- Cross-reference file analysis with git status
- Validate plan references against current repository state
- Align task priorities with technical context findings

**Direct Next Work:**
Provide specific recommendations for highest priority actions based on:
- User-approved tasks from confirmation workflow
- Subagent analysis of technical state and referenced plans
- Integration of session context with current repository conditions
- Clear prioritization of high-value immediate actions

**Error Handling:**
If no session files exist, inform the user and suggest running `/session:summarize` after working on something first.