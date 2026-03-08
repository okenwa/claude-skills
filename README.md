# Claude Code Skills

A collection of skills for [Claude Code](https://claude.com/claude-code). Each skill is a markdown file that teaches Claude how to handle specific tasks.

## Installation

Clone the entire collection:

```bash
git clone https://github.com/okenwa/claude-skills.git ~/.claude/skills
```

Or install a single skill:

```bash
mkdir -p ~/.claude/skills/gmail
curl -o ~/.claude/skills/gmail/SKILL.md \
  https://raw.githubusercontent.com/okenwa/claude-skills/master/gmail/SKILL.md
```

## Skills

| Skill | Description |
|-------|-------------|
| `agent-browser` | Browser automation -- navigate sites, scrape content, fill forms, click elements |
| `canvas` | Canva design integration |
| `directadmin` | DirectAdmin server management |
| `docx` | Create, read, edit Word documents (.docx) with docx-js and XML editing |
| `finance-bot` | Finance department -- expenses, invoices, budgets, financial tracking |
| `gmail` | Gmail operations -- read inbox, send emails, reply to messages |
| `google-calendar` | Google Calendar -- view schedule, create events, check availability |
| `maestro` | Orchestrate parallel tasks and scale output |
| `marketing-bot` | Marketing department -- content creation, campaigns, social media |
| `ops-bot` | Operations coordinator -- scheduling, workflows, task assignment |
| `research` | Deep web research with multi-source synthesis and citations |
| `research-bot` | Research department -- market intel, competitor analysis, trend tracking |
| `support-bot` | Customer support -- queries, tickets, FAQ management |
| `todo` | Task management -- view, add, complete tasks |

## How skills work

Claude Code loads skills from `~/.claude/skills/`. Each skill is a directory containing a `SKILL.md` file with:

1. **YAML frontmatter** -- `name` and `description` fields that tell Claude when to use the skill
2. **Instructions** -- the actual guidance Claude follows when the skill is triggered

```
~/.claude/skills/
  gmail/
    SKILL.md
  research/
    SKILL.md
  docx/
    SKILL.md
```

Skills are triggered automatically based on their description matching what you ask Claude to do, or manually with `/skill-name`.

## Writing your own

Create a new directory in `~/.claude/skills/` with a `SKILL.md`:

```markdown
---
name: my-skill
description: Use when [specific triggering conditions]
---

# My Skill

Instructions for Claude go here.
```

Keep descriptions focused on *when* to trigger, not *what* the skill does.
