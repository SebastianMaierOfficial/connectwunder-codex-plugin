---
name: connectwunder-workspace
description: Use ConnectWunder workspace tools to find and organize people, companies, boards, documents, meetings, calendar data, and workspace activity.
---

# ConnectWunder Workspace

Use the ConnectWunder MCP tools when a request concerns the authenticated ConnectWunder workspace.

## Operating principles

- Work only in the workspace selected during OAuth authorization.
- Start with search, list, or get tools when the target entity is uncertain.
- Before a create, update, move, or delete operation, state the intended change and confirm the affected record when the user has not already made it clear.
- Do not invent record IDs, people, companies, meeting details, or workspace facts. Ask for clarification or search first.
- Present a compact result summary after a successful mutation, including the affected entity and any returned link or identifier.

## Useful requests

- Find a person, company, board item, document, meeting, or activity by natural-language context.
- Summarize recent workspace activity, meetings, documents, or board progress.
- Turn explicit user instructions into a board item, document, follow-up, or other supported workspace update.
- Identify related records before preparing a concise status update.

## Authentication

The remote MCP server uses OAuth. If ConnectWunder is not connected, complete the browser sign-in and choose the intended workspace before continuing.
