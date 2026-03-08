---
name: gmail
description: Handle Gmail operations - read inbox, send emails, reply to messages. Triggers on: emails, inbox, reply, send, compose, draft.
---

# Gmail Skill

Email operations via Gmail MCP server.

## Capabilities

- Read inbox and specific emails
- Send new emails
- Reply to existing threads
- Search emails by query
- List labels and folders

## Process

1. **Identify action** - read, send, reply, or search
2. **Gather params** - recipient, subject, body, or search query
3. **Execute** - use Gmail MCP tools
4. **Confirm** - report result briefly

## Rules

- Always confirm before sending emails
- For replies, include original context
- Keep email summaries concise (sender, subject, snippet)
- If reading inbox, show last 5-10 unless specified
- Never expose full email addresses in logs
