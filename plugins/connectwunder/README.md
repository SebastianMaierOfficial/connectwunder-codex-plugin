# ConnectWunder Codex Plugin

The official ConnectWunder plugin connects Codex to an OAuth-authorized ConnectWunder workspace.

It provides the hosted ConnectWunder MCP server for people, companies, boards, documents, meetings, communication vault, activity, and calendar workflows. The bundled skills add safe workspace guidance, a read-first onboarding flow for new users, and secure Sites-based intake forms. Workspace operations by Codex remain MCP-only; a deployed intake form may call the public API only from its guarded server route.

## How Codex accesses ConnectWunder

All ConnectWunder workspace reads and changes happen through the hosted ConnectWunder MCP server. Codex must not control or scrape the ConnectWunder web app, use browser automation, call an alternative API, or use web search as a fallback.

The browser is used only for OAuth sign-in, re-authorization, and workspace selection. On the first OAuth-required MCP request, Codex starts the local OAuth command itself, opens the browser sign-in, waits for the user to select a workspace and approve access, then retries the request. The user must never be told to run a Terminal command, enable Developer Mode, open technical MCP settings, or enter a Bearer token. The plugin must not claim that a **Connect** action exists unless the host actually renders one.

## Authentication

The hosted streamable HTTP MCP endpoint is `https://mcp.connectwunder.com/mcp`. For first use, Codex opens the OAuth browser flow automatically; the user only signs in, selects the intended workspace, and approves access. After authorization, Codex retries the original request.

## First prompt

After connecting, start with: “Give me a short overview of my ConnectWunder workspace and its enabled modules.”

## Development

Validate the plugin from the repository root:

```bash
python3 /Users/sebastiandev/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/connectwunder
```
