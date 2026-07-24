---
name: connectwunder-board-sites
description: Structure source data such as Excel, CSV, or JSON in a ConnectWunder board, configure its public JSON feed through ConnectWunder MCP, and build or update a Sites website or internal UI that stays synchronized with that feed. Use when a nontechnical user wants a directory, use-case gallery, catalog, resource hub, showcase, or custom board view backed by ConnectWunder.
---

# ConnectWunder Board Sites

Turn a ConnectWunder board into the editable data source for a Sites website. Perform ConnectWunder setup through MCP and make the deployed site read the public JSON feed at runtime.

## Mandatory boundaries

- Perform every ConnectWunder read and mutation through the `connectwunder` MCP server. Do not use browser automation, direct Firestore access, or direct ConnectWunder API calls for setup.
- A deployed site's runtime may fetch the user-approved public board feed. This is the only direct ConnectWunder request this skill authorizes.
- Do not build or request a special Excel-import endpoint. Read supplied Excel, CSV, JSON, or other local files with the appropriate local file capability, then use ordinary MCP tools to create or update board records.
- Never invent board, column, item, tag, field, document, or asset IDs. Resolve them with MCP.
- Treat the feed URL as an unlisted public credential: do not commit it, print it into source code, or expose it in logs. Store it as the Sites runtime variable `CONNECTWUNDER_BOARD_FEED_URL`.
- A Sites access restriction does not make the upstream feed private. Anyone who obtains an enabled feed URL can read its allowlisted data. Do not publish confidential or personal data through this workflow.

## Workflow

1. Clarify the desired output, intended audience, source data, filters, detail views, and whether all selected data may be public.
2. Read any supplied local data file yourself. Inspect headers, representative values, duplicates, missing values, and candidate identifiers.
3. Use MCP to inspect the target board, its columns, tags, items, custom fields, and current publication. If no board exists and the user requested setup, create one through MCP.
4. Present a compact mapping before material setup:
   - item title: the primary human-readable name;
   - columns: workflow or publication stages, not ordinary categories;
   - tags: reusable categories and website filters;
   - custom fields: typed attributes rendered in cards, filters, or detail pages;
   - resources: explicitly public documents or item assets;
   - stable source ID: a custom field such as `source_id` when the source has a durable key.
5. Ask only about choices that materially change the public schema or overwrite behavior. Once the user approves the mapping, create the required columns, tags, and fields through MCP.
6. Materialize the data with ordinary board tools:
   - list existing items first;
   - match by a stable source ID when available;
   - update matching items and create missing items;
   - do not duplicate rows on a rerun;
   - use `update_board_item_data` for complete typed `fieldValues` and `resources`;
   - work in bounded batches and summarize exceptions instead of silently dropping rows.
7. Configure public resources only when requested:
   - for a document, check `get_document_public_share`; enable it with `publish_document_public_share` only when the user authorized public access, then link the document resource;
   - for a local attachment, create an MCP asset-import session scoped to the exact board item, upload only to its returned signed URL, finalize it, then link the ready asset ID;
   - keep each resource's `public` flag false unless it is intended for the feed;
   - explain that revoking a document share makes that document disappear from the feed, while revoking the board feed disables feed-backed asset URLs.
8. Call `preview_board_publication` with the intended fields, columns, tags, and resource settings. Inspect the exact JSON for accidental internal, personal, or irrelevant data.
9. After the user has authorized public publication, call `publish_board_feed`. Regenerate the URL only when the user explicitly wants the previous URL invalidated.
10. Build and publish the website with the Sites building and hosting skills. Configure `CONNECTWUNDER_BOARD_FEED_URL` as a runtime environment variable and fetch it at request time through a same-origin server route.
11. Validate both the data and presentation, then report the feed state, board mapping, deployed URL, refresh behavior, and any rows or resources that need user attention.

## Schema design rules

- Use lowercase stable field keys with underscores. Labels may change; keys should not.
- Infer types from the source:
  - short string → `text`;
  - descriptive or Markdown content → `long_text`;
  - numeric measure → `number`;
  - true/false value → `boolean`;
  - date or timestamp → `date`;
  - HTTP(S) link → `url`;
  - controlled single category → `select`;
  - controlled category list → `multi_select`.
- Prefer tags for cross-cutting public filters. Prefer select fields when the value is part of the record's structured schema or must retain a stable field key.
- Preserve source values unless normalization is necessary and visible to the user. Report ambiguous dates, mixed numeric/text columns, unsupported options, and duplicate stable IDs.
- Include only fields that the website needs. A public feed is an allowlist, not a full board export.
- Never model workspace actors, event history, internal notes, permissions, or personal contact data into public custom fields merely because they exist in a source file.

## Sites integration contract

Create a same-origin route such as `GET /api/data` that:

1. reads `CONNECTWUNDER_BOARD_FEED_URL` only on the server;
2. fetches the feed with a short bounded timeout;
3. accepts the supported major `schemaVersion` and fails safely on an incompatible version;
4. returns only the fields used by the page;
5. uses a modest cache or revalidation interval, normally 60–300 seconds;
6. exposes a generic error without returning the feed URL or upstream response details.

The browser should call only the same-origin route. Do not bake a one-time feed snapshot into the site: board changes must become visible without rebuilding or redeploying.

Build accessible loading, empty, error, filter, and detail states. Use stable item IDs for routes or keys, handle missing optional fields/resources, and render only safe URL protocols. Every external-facing page must include working user-supplied Imprint and Privacy links.

## Release gates

- The feed preview contains only explicitly selected public data.
- A repeated source-file run updates existing records instead of creating duplicates.
- Invalid rows are reported with enough context for correction.
- Document resources expose the external share URL, never an internal document URL.
- Asset URLs work while the feed is enabled and fail after revocation.
- The feed URL is absent from source, Git history, browser logs, and error output.
- The site reflects a test board change after the configured revalidation interval without a redeploy.
- Filters, keyboard navigation, responsive layout, loading state, empty state, and failure state work.
- Imprint and Privacy links are present on external pages.

## Recovery

- If the MCP tools are missing, ask the user to update or reinstall the ConnectWunder plugin and open a new Codex task.
- If OAuth is required, follow the ConnectWunder workspace skill's OAuth recovery flow, then retry the original MCP call once.
- If the desired field or publication tool is unavailable, stop rather than using a direct API fallback.
- If Sites cannot store the feed URL as a server runtime variable or provide a same-origin server route, do not publish a source-embedded fallback. Explain the limitation and wait for approval of another server-capable approach.
- If the public feed returns 404, inspect publication state through MCP; never guess or reconstruct its token.
