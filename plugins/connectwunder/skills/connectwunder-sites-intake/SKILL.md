---
name: connectwunder-sites-intake
description: Create and publish secure ConnectWunder-powered Sites forms for leads, contact requests, demo requests, support tickets, and software issue reports. Use when a user wants a public or access-controlled website form whose submissions create or update people and board items in ConnectWunder through the public API.
---

# ConnectWunder Sites Intake

Build an accessible Sites form with a server-side submission route. Configure the target workspace through ConnectWunder MCP and use the published ConnectWunder API only from the deployed Sites server runtime.

Canonical API specification: `https://app.connectwunder.com/openapi.yaml`. Use it to validate the generated integration; do not copy the specification into the site.

## Mandatory boundaries

- Use ConnectWunder MCP for every ConnectWunder action performed by Codex itself: inspect the workspace, identify or create the target board and column, and confirm the resulting configuration.
- Do not call the ConnectWunder public API directly from Codex, use browser automation against ConnectWunder, or use an API key to perform setup actions.
- The Sites application's server route is an authored external integration, not a Codex workspace action. It may call the public API only after all requirements below are met.
- Never put a ConnectWunder API key, token, or other secret in browser code, source files, Git history, screenshots, logs, error messages, HTML, query strings, or a prompt response.
- Never ask the user to paste a secret into chat. Use Sites runtime environment variables when the available Sites tooling permits it; otherwise guide the user through the Sites settings UI.
- Never create or publish an insecure fallback that submits directly from browser JavaScript to ConnectWunder.

## Safe workflow

1. Confirm the explicit outcome: lead, contact, demo, support ticket, or software issue. Ask only for missing essentials: target board and column, fields, legal links, intended audience, and whether publication should be public or restricted.
2. Use MCP to find the chosen board and an active target column. Do not invent IDs. Ask for confirmation before creating a board, column, tag, or other workspace record.
3. Build the site using the Sites capability path. Include a same-origin server submission route such as `POST /api/submit`; use Worker-compatible server code and the Sites runtime environment facility.
4. Configure the non-secret values `CONNECTWUNDER_API_BASE_URL` (`https://app.connectwunder.com`), `CONNECTWUNDER_BOARD_ID`, and `CONNECTWUNDER_COLUMN_ID`. Keep target IDs configurable outside the browser bundle.
5. Configure the secret `CONNECTWUNDER_API_KEY` only as a Sites runtime environment variable. Prefer a dedicated, clearly labelled ConnectWunder API key for this one site. Never reuse a personal key.
6. If the secret can be set with the authorised Sites environment-variable tool, set it without displaying the value. If not, pause before public deployment and guide the user through the UI: open the site's Settings, open the Environment/Runtime Variables section, add `CONNECTWUNDER_API_KEY` as a secret value, save it, and redeploy. Use the labels visible in the user's UI rather than guessing. Ask for a redacted screenshot if they get stuck.
7. Validate the site with synthetic test data only after telling the user that it will create one clearly labelled test person and board item. Remove or archive that test record only after explicit approval.
8. Publish privately by default. Publish publicly only when the user explicitly requests it and every release gate below passes.

## Server-side integration contract

In the Sites server route:

1. Accept only an expected JSON or form payload; reject unknown oversized fields, invalid content types, and bodies larger than the form needs.
2. Validate and normalize every submitted value server-side. Require a name and a contact method for flows that create a person. Never trust a board ID, column ID, tag ID, or API endpoint supplied by the browser.
3. Send `Authorization: Bearer ${CONNECTWUNDER_API_KEY}` only from server code. Use the configured API base URL, never a caller-provided URL.
4. Look up an existing person by normalized email before creating one with `POST /api/persons`. On a duplicate response, retrieve and reuse the existing person instead of creating a second record.
5. Create the board item through `POST /api/boards/{boardId}/items` using the configured board and column, the resolved person as primary subject, and a concise title. Add a board-item note/event for the validated form content only when the user wants the detail retained.
6. Return a generic success response. Keep ConnectWunder identifiers, provider responses, stack traces, and secrets out of the browser response.
7. Treat file uploads as unsupported unless the implementation also uses a server-authorized, server-finalized upload flow. Never accept or store arbitrary attachment URLs.

## Release gates

- Add an accessible form with labels, error summaries, keyboard support, and a success state.
- Collect only the fields needed for the stated purpose. Keep marketing consent separate from a support or contact request.
- Show working, user-supplied Privacy and Imprint links. Do not invent legal text or claim legal compliance.
- Require an unchecked privacy acknowledgement when it is the stated legal basis. Store the consent version and submission timestamp in the retained submission detail.
- Add server-side abuse controls: a honeypot field, minimum completion time, payload and field-size limits, durable rate limiting, and idempotency for retries. Do not permanently store a raw IP address solely for rate limiting when a short-lived or hashed representation suffices.
- Do not log form bodies, API credentials, or full upstream error bodies. Record only redacted operational events needed to diagnose failures.
- Do not add permissive CORS headers. The browser talks only to its same-origin Sites route; the server route calls ConnectWunder.
- Verify that the target board and column are active and that the dedicated API key works before public release.

## User guidance and recovery

- Explain manual steps in short numbered instructions, one screen at a time. State the exact environment-variable name but never request or repeat its value.
- When a step is blocked, ask for a screenshot with secrets, personal data, and URLs containing tokens redacted. Continue from the visible state.
- If Sites cannot host the required secret or server route, stop. Explain that publishing a client-side-key version is unsafe and offer a server-capable hosting alternative only after the user approves it.
- If ConnectWunder rejects the key or target configuration, do not work around the failure. Ask the user to verify the dedicated key, workspace, board, and column, then retry with synthetic data.
- After successful deployment, report the site URL, target board and column by name, and whether the secret was configured. Do not report the secret value.

## Relationship to the general workspace skill

The MCP-only rule remains in force for Codex's own ConnectWunder access. This skill is the narrow exception for authored, deployed Sites server code that implements the explicitly requested external form integration. It never authorizes direct API calls by Codex or browser-side API calls.
