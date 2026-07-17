# ConnectWunder Codex Plugin

The official ConnectWunder plugin connects Codex to an OAuth-authorized ConnectWunder workspace.

It provides the hosted ConnectWunder MCP server for people, companies, boards, documents, meetings, communication vault, activity, and calendar workflows. The bundled skills add safe workspace guidance, a read-first onboarding flow for new users, and secure Sites-based intake forms. Workspace operations by Codex remain MCP-only; a deployed intake form may call the public API only from its guarded server route.

## How Codex accesses ConnectWunder

All ConnectWunder workspace reads and changes happen through the hosted ConnectWunder MCP server. Codex must not control or scrape the ConnectWunder web app, use browser automation, call an alternative API, or use web search as a fallback.

The browser is used only for OAuth sign-in, re-authorization, and workspace selection. The current Codex plugin view does not expose the host-owned OAuth connection flow for this bundled MCP server. It must not claim that a **Connect** action exists, or send users to Terminal, Developer Mode, technical MCP settings, or a manual Bearer-token field.

## Authentication

The hosted streamable HTTP MCP endpoint is `https://mcp.connectwunder.com/mcp`. The OAuth server follows the Codex MCP OAuth protocol, but the current Codex plugin view does not provide the needed first-use connection journey. Do not treat this package as a user-ready OAuth integration until Codex exposes that native flow for bundled plugin MCP servers.

## First prompt

After connecting, start with: “Give me a short overview of my ConnectWunder workspace and its enabled modules.”

## Development

Validate the plugin from the repository root:

```bash
python3 /Users/sebastiandev/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/connectwunder
```
