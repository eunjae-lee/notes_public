# Personal Notes

A structured personal notes repository organized by time periods (yearly, quarterly, weekly) with automation scripts for daily task management and GitHub activity tracking.

## Overview

This repository helps manage personal notes, tasks, and reflections using a time-based organizational structure. It includes:

- **Time-based notes**: Yearly, quarterly, and weekly notes following consistent naming conventions
- **Task management**: Structured approach to tracking daily and weekly tasks
- **GitHub integration**: Scripts to automatically fetch and summarize GitHub activities
- **Templates**: Reusable templates for creating new notes
- **Date utilities**: Helper scripts for consistent date calculations

## Quick Start

### View Available Commands

See [AGENTS.md](AGENTS.md) for detailed documentation on all available commands and workflows.

Key commands:
- `:tasks` - Show today's remaining tasks
- `:start today` - Plan today's tasks
- `:wrap up today` - Summarize the day's activities
- `:start this week` - Create a new weekly note
- `:wrap up this week` - Summarize the week and prepare for next week

### File Structure

```
.
├── .templates/          # Templates for new notes
│   ├── quarterly.md     # Quarterly note template
│   └── weekly.md        # Weekly note template
├── .vscode/             # VS Code configuration
├── YYYY.md              # Annual notes (e.g., 2025.md)
├── YYYY-QX.md           # Quarterly notes (e.g., 2025-Q3.md)
├── YYYY-WXX.md          # Weekly notes (e.g., 2025-W30.md)
└── *.sh                 # Utility scripts
```

## Naming Conventions

- `YYYY.md` - Annual notes (e.g., `2025.md`)
- `YYYY-QX.md` - Quarterly notes (e.g., `2025-Q1.md`)
- `YYYY-WXX.md` - Weekly notes (e.g., `2025-W08.md`)

## Utility Scripts

### Date Utilities

The `date-utils.sh` script provides consistent date calculations:

```bash
./date-utils.sh current-week      # Get current week (e.g., 2025-W29)
./date-utils.sh next-week         # Get next week (e.g., 2025-W30)
./date-utils.sh week-range        # Get current week range
./date-utils.sh today-date        # Get today's date
./date-utils.sh current-quarter   # Get current quarter
```

### GitHub Activity Scripts

- `github-activity.sh` - Fetch today's GitHub activities
- `github-activity-yesterday.sh` - Fetch yesterday's activities
- `github-activity-week.sh` - Fetch current week's activities

## Task Management Best Practices

- Keep main task items stable - avoid constantly changing task descriptions
- Use sub-items (indented) to track progress and updates
- Use strikethrough (`~~text~~`) for tasks that become irrelevant
- Only check off tasks (`- [x]`) that you personally completed
- Add status updates as indented sub-items, not by editing the main task

## Documentation

For detailed information about the repository structure, agent commands, and workflows, see [AGENTS.md](AGENTS.md).

## License

This is a personal notes repository.
