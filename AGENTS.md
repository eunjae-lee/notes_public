# Notes Repository Structure

This is a personal notes repository organized by time periods.

## Folder Structure

- `.templates/` - Template files for creating new notes
  - `quarterly.md` - Template for quarterly notes
  - `weekly.md` - Template for weekly notes with backlog and daily to-do/done sections
- `.vscode/` - VS Code configuration
- `archives/` - Archived notes and old content
- `reviews/` - Performance reviews and feedback

## File Naming Convention

- `YYYY.md` - Annual notes (e.g., `2025.md`)
- `YYYY-QX.md` - Quarterly notes (e.g., `2025-Q1.md`)
- `YYYY-WXX.md` - Weekly notes (e.g., `2025-W08.md`)

## Weekly Notes Structure

Weekly notes include:
- Period dates (Monday to Friday work week)
- Backlog section for task management
- Daily sections for Monday through Friday
- Summary section for weekly reflection

**Important:** Weekly notes cover Monday-Friday only (5-day work week).

### Task Management Best Practices

- Keep main task items stable - avoid constantly changing the task description
- Use sub-items (indented with `- [x]` or `- [ ]`) to track progress and updates under the main task
- This maintains a clear audit trail while showing progress
- Use strikethrough (`~~text~~`) for tasks that become irrelevant or are completed by others, rather than checking them off
- Only check off tasks (`- [x]`) that you personally completed

## Usage

Use the templates in `.templates/` to create new quarterly and weekly notes following the established structure.

## Date Utilities

The `date-utils.sh` script provides consistent date calculations for note management:

```bash
./date-utils.sh current-week      # Get current week (e.g., 2025-W29)
./date-utils.sh next-week         # Get next week (e.g., 2025-W30)
./date-utils.sh week-range        # Get current week range (e.g., 2025-07-14 ~ 2025-07-18)
./date-utils.sh next-week-range   # Get next week range (e.g., 2025-07-21 ~ 2025-07-25)
./date-utils.sh today-date        # Get today's date (e.g., 2025-07-19)
./date-utils.sh current-quarter   # Get current quarter (e.g., 2025-Q3)
```

Use these commands instead of manual date calculations to ensure consistency across all note operations.

## Agent Commands

### "start a new week"
When the user says "start a new week":
1. Create a new weekly note using the template from `.templates/weekly.md`
2. Name it with the current week number (e.g., `2025-W29.md`)
3. Update the period dates in the new file (Monday to Friday of that week)
4. Find the current quarterly note (e.g., `2025-Q3.md`)
5. Add a link to the new weekly note in the quarterly's "Weeks" section

### "start today"
When the user says "start today":
1. Find the current week's note file
2. Scan all previous days in the week (up to yesterday) for incomplete tasks (unchecked `- [ ]` items)
3. Also check the backlog section for incomplete tasks
4. Present each incomplete task to the user one by one, asking: "Do you want to tackle '[task]' today?"
5. For each "yes" response, add the task to today's section
6. After reviewing incomplete tasks, ask interactive questions to help plan the day:
   - "What's your most important priority today?"
   - "Do you have any meetings or appointments? What preparation is needed?"
   - "What would make today feel successful?"
   - "Any urgent items that came up overnight?"
7. Add responses as tasks in today's section
8. Skip tasks the user says "no" to

### "wrap up today"
When the user says "wrap up today":
1. Run the `./github-activity.sh 2>&1` script to fetch today's GitHub activities
2. Summarize the GitHub activities and add them to the "### Summary" section under today's date in the weekly note
3. Ask reflective questions to help plan tomorrow **one by one interactively**:
   - "What went well today?"
   - "What didn't go as planned?"
   - "What should you prioritize tomorrow?"
   - "Any blockers or dependencies for tomorrow?"
   - "What preparation is needed for tomorrow's meetings/tasks?"
4. Add responses as tasks or notes for tomorrow or the backlog

### "wrap up this week"
When the user says "wrap up this week":
1. Run the `./github-activity-week.sh 2>&1` script to fetch this week's GitHub activities
2. Find the current week's note file
3. Scan all days in the week for incomplete tasks (unchecked `- [ ]` items)
4. Also check the backlog section for incomplete tasks
5. Summarize the GitHub activities and add them to the Summary section **including actual PR titles and links for team sharing** (do not group by day - use simple list format)
6. Create a summary of the week's accomplishments and add it to the Summary section
7. Create next week's note using the template from `.templates/weekly.md`
8. Add all incomplete tasks to the backlog section of the new week's note
9. Update the period dates in the new weekly file using: `./date-utils.sh next-week-range`
10. Find the current quarterly note and add a link to the new weekly note

## Performance Review Integration

The `reviews/` folder contains performance feedback that should guide daily and weekly planning:

- **During "start today"**: Occasionally suggest tasks that align with feedback areas for improvement
- **During "wrap up today"**: When relevant, connect completed work to feedback goals
- **During weekly planning**: Proactively suggest focusing on feedback areas that haven't been addressed recently
- **General guidance**: Reference feedback when user asks for career advice or improvement suggestions