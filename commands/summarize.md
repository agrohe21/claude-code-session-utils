---
name: session:summarize
description: Trigger the summarization agent to analyze the current session and create a structured summary file for future reference.
parameters: []
---

Please activate the session summarization agent to analyze the current conversation and generate a comprehensive session summary.

The summarization agent should:
1. Analyze the entire current session conversation
2. Extract all necessary content to populate the session summary template sections
3. Create and save a properly formatted summary file to `.claude/memory/sessions/[YYYY-MM-DD]-[topic-name].md`
4. Use the session-summary-template.md as a guide for what sections to include

The agent will work autonomously in its own context to ensure comprehensive analysis without disrupting the current conversation flow.

Once the summary file has been created, confirm completion to the user with the filename and location.