# ConnectWunder Codex Plugin

The official ConnectWunder plugin connects Codex to an OAuth-authorized ConnectWunder workspace.

It provides the hosted ConnectWunder MCP server for people, companies, boards, documents, meetings, communication vault, activity, and calendar workflows. The bundled skills add safe workspace guidance, a read-first onboarding flow for new users, and a strict MCP-only boundary for workspace work.

## How Codex accesses ConnectWunder

All ConnectWunder workspace reads and changes happen through the hosted ConnectWunder MCP server. Codex must not control or scrape the ConnectWunder web app, use browser automation, call an alternative API, or use web search as a fallback.

The browser is used only for OAuth sign-in, re-authorization, and workspace selection. If the MCP tools are not available, Codex guides the user to install or reinstall the plugin and start a new Codex task. If OAuth is missing or expired, Codex guides the user through OAuth before retrying the operation through MCP.

## Authentication

On first use, Codex opens the ConnectWunder OAuth flow. Sign in, select the intended workspace, and approve access. The plugin uses the hosted streamable HTTP MCP endpoint at `https://mcp.connectwunder.com/mcp`. After an installation or reinstall, start a new Codex task so its MCP tools are available.

## First prompt

After connecting, start with: “Give me a short overview of my ConnectWunder workspace and its enabled modules.”

## Development

Validate the plugin from the repository root:

```bash
python3 /Users/sebastiandev/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/connectwunder
```
