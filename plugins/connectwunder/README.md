# ConnectWunder Codex Plugin

The official ConnectWunder plugin connects Codex to an OAuth-authorized ConnectWunder workspace.

It provides the hosted ConnectWunder MCP server for people, companies, boards, documents, meetings, communication vault, activity, and calendar workflows. The bundled skills add safe workspace guidance and a read-first onboarding flow for new users.

## Authentication

On first use, Codex opens the ConnectWunder OAuth flow. Sign in, select the intended workspace, and approve access. The plugin uses the hosted streamable HTTP MCP endpoint at `https://mcp.connectwunder.com/mcp`.

## First prompt

After connecting, start with: “Give me a short overview of my ConnectWunder workspace and its enabled modules.”

## Development

Validate the plugin from the repository root:

```bash
python3 /Users/sebastiandev/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/connectwunder
```
