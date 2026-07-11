# ConnectWunder Skill Roadmap

The initial release contains two skills:

- `connectwunder-workspace`: safe general use of workspace tools.
- `connectwunder-onboarding`: a read-first first-session orientation.

The following additions are the highest-value next skills, based on the currently exposed MCP capabilities.

## 1. Meeting Follow-up

Turn a meeting, its artifacts, and stated decisions into a reviewable follow-up draft. It should read the meeting and existing artifacts first, identify action items and open questions, then ask for confirmation before creating board items or meeting artifacts.

Why: ConnectWunder exposes meetings, meeting artifacts, boards, board items, and board-item events. A single guided flow removes manual copying after meetings while retaining approval before writes.

## 2. Daily Workspace Briefing

Create a concise daily or weekly briefing from recent activity, open board items, upcoming meetings, and calendar events. It should be read-only by default and cite the underlying ConnectWunder records where available.

Why: This provides immediate recurring value without data changes and uses existing activity, board, meeting, and calendar tools.

## 3. Relationship Preparation

Prepare a person or company brief before a meeting or sales conversation: related people, companies, documents, meetings, boards, and recent events. It must use searches and returned records only, never invent relationship facts.

Why: The MCP server has dedicated people, company, relationship, event, document, and meeting retrieval tools.

## 4. Board Triage

Review a selected board, detect ambiguous or stale items, and propose a prioritized action plan. The skill should make no changes until the user approves each proposed move or update.

Why: ConnectWunder supports board/item listing, lifecycle changes, moves, tags, and events, making it suitable for a high-trust review-and-confirm workflow.

## Design principles for every new skill

- Start with the narrowest read-only search that can establish the target record.
- Keep workspace scope strictly within the OAuth-authorized tenant.
- Give users a preview before mutations and a concise read-back after successful writes.
- Avoid bulk changes by default; request an explicit scope and confirmation.
