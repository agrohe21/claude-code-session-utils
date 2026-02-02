# Testing the Plugin

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