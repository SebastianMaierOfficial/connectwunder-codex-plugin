# ConnectWunder Codex Plugin

The official ConnectWunder plugin connects Codex to an OAuth-authorized ConnectWunder workspace.

It provides the hosted ConnectWunder MCP server for people, companies, boards, documents, meetings, communication vault, activity, and calendar workflows. The bundled skills add safe workspace guidance, a read-first onboarding flow for new users, and secure Sites-based intake forms. Workspace operations by Codex remain MCP-only; a deployed intake form may call the public API only from its guarded server route.

## How Codex accesses ConnectWunder

All ConnectWunder workspace reads and changes happen through the hosted ConnectWunder MCP server. Codex must not control or scrape the ConnectWunder web app, use browser automation, call an alternative API, or use web search as a fallback.

The browser is used only for OAuth sign-in, re-authorization, and workspace selection. When OAuth is required, Codex must first invoke the requested ConnectWunder MCP tool (or `ping`), so that the host can display its native **Connect** action. It must not send users to Developer Mode, technical MCP settings, or a manual Bearer-token field.

## Authentication

On first use, invoke a ConnectWunder request. Codex should show its native **Connect** flow; sign in, select the intended workspace, and approve access. The plugin uses the hosted streamable HTTP MCP endpoint at `https://mcp.connectwunder.com/mcp`. After this plugin update, start a new Codex task so its updated skills and MCP configuration are loaded.

## First prompt

After connecting, start with: “Give me a short overview of my ConnectWunder workspace and its enabled modules.”

## Development

Validate the plugin from the repository root:

```bash
python3 /Users/sebastiandev/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/connectwunder
```
