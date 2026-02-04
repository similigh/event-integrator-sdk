# Simili-Bot Integration Setup

This repository is configured for Simili-Bot automatic issue triage and similarity detection.

## Configuration
- **Config File**: `.github/simili.yaml`
- **Extends**: `similigh/simili-shared-config@main`
- **Workflow**: `.github/workflows/issue-triage.yml`

## Features Enabled
✅ Cross-Repository Similarity Search (cross_repo_search: true)
✅ Transfer Loop Prevention (EventAction field)
✅ Table-Formatted Similar Issues Display
✅ Markdown Table Format for Better UX

## Tested Scenarios

### Scenario 1: Cross-Repo Similarity
- Core Issue #94: "User authentication flow enhancement"
- CLI Issue #35: "Authentication system improvements"  
- SDK Issue #60: "API authentication enhancement"

These issues are matched as similar with ~80-85% similarity due to shared authentication context.

### Scenario 2: Transfer Loop Prevention
When an issue is transferred from one repo to another:
1. Bot detects "transferred" event action
2. Skips re-triage with message: "transferred from another repository"
3. Prevents 100% self-duplicate match

### Scenario 3: Table Formatting
Similar issues are displayed in clean markdown table format:
```
| Issue | Title | Similarity | State |
|-------|-------|------------|-------|
| [#35](url) | Authentication system improvements | 82% | open |
```

## Verification Checklist
- [x] Repository configured in simili.yaml
- [x] Workflow triggers on issue.opened and issue.edited
- [x] Cross-repo search enabled
- [x] Similar issues table formatting applied
- [x] Transfer loop prevention working

## Testing the Bot

To manually trigger the bot on an existing issue:
```bash
cd /Users/kaviru/Downloads/simili-bot
./simili-cli process --issue <json_event> --config /tmp/simili-integration/simili-shared-config/.github/simili.yaml --dry-run
```

## Repos in Integration
- event-integrator-core (main server engine)
- event-integrator-cli (CLI interface)
- event-integrator-sdk (Client libraries)
- event-integrator-docs (Documentation)
- event-integrator-vscode (VS Code extension)
