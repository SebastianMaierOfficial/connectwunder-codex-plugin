# ConnectWunder Codex Plugin

The official ConnectWunder plugin connects Codex to an OAuth-authorized ConnectWunder workspace.

It provides the hosted ConnectWunder MCP server for people, companies, boards, documents, meetings, communication vault, activity, and calendar workflows. The bundled skills add safe workspace guidance, a read-first onboarding flow for new users, and secure Sites-based intake forms. Workspace operations by Codex remain MCP-only; a deployed intake form may call the public API only from its guarded server route.

## How Codex accesses ConnectWunder

All ConnectWunder workspace reads and changes happen through the hosted ConnectWunder MCP server. Codex must not control or scrape the ConnectWunder web app, use browser automation, call an alternative API, or use web search as a fallback.

The browser is used only for OAuth sign-in, re-authorization, and workspace selection. The current Codex plugin view does not provide an in-chat **Connect** action for bundled MCP servers. It must not claim that it does, or send users to Developer Mode, technical MCP settings, or a manual Bearer-token field.

## Authentication

On first use, run the official one-time Codex OAuth login in Terminal. It opens the browser, where the user signs in, selects the intended workspace, and approves access:

```bash
/Applications/ChatGPT.app/Contents/Resources/codex mcp login connectwunder --scopes mcp.full
```

This does not require Developer Mode or a Bearer token. The plugin uses the hosted streamable HTTP MCP endpoint at `https://mcp.connectwunder.com/mcp`. After login, start a new Codex task before retrying the request.

## First prompt

After connecting, start with: “Give me a short overview of my ConnectWunder workspace and its enabled modules.”

## Development

Validate the plugin from the repository root:

```bash
python3 /Users/sebastiandev/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/connectwunder
```
