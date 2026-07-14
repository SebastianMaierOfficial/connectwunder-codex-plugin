---
name: connectwunder-workspace
description: Use ConnectWunder workspace tools to find and organize people, companies, boards, documents, meetings, calendar data, and workspace activity.
---

# ConnectWunder Workspace

Use the ConnectWunder MCP tools when a request concerns the authenticated ConnectWunder workspace.

## Mandatory MCP boundary

- Perform every ConnectWunder workspace operation through the `connectwunder` MCP server: reads, searches, summaries, and mutations alike.
- Do **not** control, inspect, scrape, or automate the ConnectWunder web app with a browser, Chrome, web search, direct HTTP calls, or any other fallback. Do not use those routes to work around unavailable MCP tools.
- A browser is permitted only to complete, resume, or re-authorize the ConnectWunder OAuth flow that Codex initiates. Once OAuth is complete, return to the MCP tools for all workspace work.
- If the MCP server, its tools, or its workspace resources are unavailable, stop the requested workspace operation and guide the user through recovery below. Do not attempt an alternative route.

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

## MCP recovery guide

When ConnectWunder MCP access is unavailable, explain the relevant next step concisely and wait for the user to complete it:

1. **Plugin or tools are missing:** Ask the user to install or reinstall the ConnectWunder plugin, then open a **new Codex task**. A new task is required for Codex to load the plugin's updated skills and MCP tools.
2. **OAuth is missing, expired, cancelled, or denied:** Ask the user to start or resume the ConnectWunder OAuth flow in the browser, sign in, select the intended workspace, and approve access. Then retry the same MCP operation.
3. **The MCP connection still fails after OAuth:** Tell the user that the MCP service is not currently available in this task and ask them to start a new task. If it persists, ask them to share the exact Codex error so it can be diagnosed.
4. **Access is denied for a specific workspace or action:** State the returned access limitation and ask the user to authorize the correct workspace or obtain the required ConnectWunder permission. Never seek the data through the web app instead.

Do not claim that a connection, OAuth authorization, workspace selection, or an operation succeeded unless the MCP result confirms it.
