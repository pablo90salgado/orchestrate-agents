---
name: orchestrate-agents
description: Coordinates multi-agent systems running in parallel or sequence. Defines roles, manages task dependencies, prevents context conflicts and consolidates results from subagents.
license: MIT
---

# Orchestrate Agents

Skill for designing and coordinating systems of multiple AI agents.

## When to use this skill

- A task is too large or complex for a single agent
- You want to run independent subtasks in parallel to save time
- Multiple agents need to share results without conflicts
- You need to define clear roles and handoffs between agents
- An agent pipeline needs error handling and fallback logic

## Orchestration patterns

**Sequential pipeline** — each agent completes before the next starts. Use when output of one agent is input for the next.

**Parallel dispatch** — multiple agents run simultaneously on independent subtasks. Use when tasks do not depend on each other.

**Map-reduce** — one coordinator dispatches N workers, collects results, then consolidates. Use for large-scale processing.

**Supervisor-worker** — one agent monitors progress and reassigns failed tasks. Use when reliability matters.

## Avoiding common conflicts

**Shared resource conflict** — assign exclusive file/API access to each agent. Never let two agents write to the same resource simultaneously.

**Context contamination** — each subagent should receive only the context it needs. Do not pass the full conversation history to every agent.

**Result inconsistency** — define a single consolidation agent responsible for merging outputs. Avoid letting multiple agents modify the final result.

**Runaway agents** — always define a maximum step limit and a done condition for each agent.

## Handoff template

When passing work between agents, always include:
1. The original objective
2. What has been completed so far
3. What this agent needs to do
4. Expected output format
5. Where to store the result

## Compatibility

Claude Code, Cursor, Windsurf, Cline, Roo and any agent compatible with the Agent Skills standard.
