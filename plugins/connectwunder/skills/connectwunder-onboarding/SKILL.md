---
name: connectwunder-onboarding
description: Guide a new ConnectWunder user through a safe first-session orientation, then help them choose a useful first workflow.
---

# ConnectWunder Onboarding

Use this skill when a user is new to ConnectWunder, asks what ConnectWunder can do, wants help getting started, or asks for a first workspace tour.

## Goal

Make the first session useful without making unsolicited changes to the workspace.

## ConnectWunder access boundary

Use the ConnectWunder MCP server exclusively for all workspace information and actions. Never use browser automation, the ConnectWunder web app, web search, or direct HTTP/API calls as a substitute for MCP access. The browser is only for the OAuth sign-in or re-authorization flow initiated by Codex. This onboarding boundary does not cover explicitly requested, separately guarded deployed server integrations.

If MCP tools or resources are not available, do not continue the walkthrough by another route. For a missing OAuth connection, invoke `ping` once. The current Codex plugin view does not expose the native OAuth connection flow, so do not claim that it does or send the user to Terminal, Developer Mode, technical MCP settings, or a Bearer-token field. Stop the walkthrough until native plugin OAuth is available.

## First-session flow

1. Before discussing connection state, invoke `get_workspace_profile` or `ping`. If OAuth is required, report that the native OAuth connection flow is unavailable in this Codex plugin view and stop. Do not invent a Connect action or Terminal workaround.
2. Read the available workspace context before giving advice:
   - Read `connectwunder://workspace/profile`.
   - Read `connectwunder://workspace/modules`.
   - Read `connectwunder://owner/profile` when it is available.
3. Give a short orientation based only on returned data. Mention enabled modules and avoid assuming that a module, record, or workflow exists.
4. Ask the user to pick one first outcome:
   - understand recent activity;
   - find a person, company, board, document, or meeting;
   - prepare follow-ups from a meeting;
   - organize a board or document;
   - plan time in the calendar.
5. Use read-only tools for the first walkthrough unless the user explicitly asks for a change.
6. Before any create, update, move, or delete action, state exactly what will change and ask for confirmation unless the user has already given an unambiguous instruction.

## Helpful first prompts

- “Give me a short overview of my ConnectWunder workspace and its enabled modules.”
- “Summarize the most important activity from the last seven days.”
- “Find open board items that need my attention.”
- “Show the next meetings and prepare a short follow-up checklist.”

## Safety and privacy

- Keep all results within the OAuth-authorized workspace.
- Do not expose raw communication-vault content unless the user specifically asks for it and the tool returns it.
- Do not infer people, companies, owners, deadlines, or relationship facts that are not present in ConnectWunder.
- If the user’s objective is unclear, ask one concise clarification question rather than making a broad search or mutation.
