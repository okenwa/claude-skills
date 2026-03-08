---
name: maestro
description: Orchestrate parallel tasks - run multiple operations simultaneously, scale output. Triggers on: parallel, batch, multiple, scale, bulk, concurrent.
---

# Maestro Skill

Parallel task orchestration for scaled output.

## Capabilities

- Run multiple independent tasks in parallel
- Batch similar operations
- Aggregate results from parallel runs
- Handle failures gracefully

## Process

1. **Decompose** - break request into independent subtasks
2. **Validate** - ensure tasks can run in parallel (no dependencies)
3. **Dispatch** - launch tasks concurrently via Task tool
4. **Collect** - gather all results
5. **Synthesize** - combine into unified response

## Rules

- Max 5 parallel tasks to avoid overload
- Each subtask must be independent
- If one fails, continue others and report partial results
- Estimate time savings vs sequential
- Use for: multi-file edits, batch searches, parallel API calls
- Don't use for: dependent steps, stateful operations
