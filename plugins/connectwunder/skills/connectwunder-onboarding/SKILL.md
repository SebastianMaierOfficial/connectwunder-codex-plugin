---
name: connectwunder-onboarding
description: Guide a new ConnectWunder user through a safe first-session orientation, then help them choose a useful first workflow.
---

# ConnectWunder Onboarding

Use this skill when a user is new to ConnectWunder, asks what ConnectWunder can do, wants help getting started, or asks for a first workspace tour.

## Goal

Make the first session useful without making unsolicited changes to the workspace.

## First-session flow

1. Confirm that ConnectWunder OAuth is connected. If it is not, tell the user to connect the plugin and select the intended workspace.
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
