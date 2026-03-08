---
name: google-calendar
description: Manage Google Calendar - view schedule, create events, check availability. Triggers on: schedule, meeting, calendar, event, appointment, free time.
---

# Google Calendar Skill

Calendar operations via Google Calendar MCP server.

## Capabilities

- View today's/upcoming schedule
- Create new events
- Check availability
- Update or delete events
- Find free slots

## Process

1. **Identify action** - view, create, update, delete
2. **Gather params** - date, time, duration, attendees, title
3. **Execute** - use Calendar MCP tools
4. **Confirm** - report result with event details

## Rules

- Default to today if no date specified
- Use 24h format internally, display in user's preference
- For new events, confirm time and duration before creating
- Show schedule as compact list (time - title)
- When finding free time, check next 7 days unless specified
