Step 1. Ticket Created

Purpose: Define scope & accountability

Checklist: Scope, impact, rollback documented

Responsibility: Author / Requester

Example: Ticket: “Fix P&L allocation query for Entity X Q2” → rollback plan = revert to last approved version

Step 2. Design Note Prepared

Purpose: Capture logic before coding

Checklist: Inputs/outputs, joins, edge cases, rollback plan

Responsibility: Author, sanity-checked by Peer

Example: Note: Input = FCT_GL, Join on cost_center_id, Output = P&L by CMG. Handle null period_id by defaulting to ‘9999’.

Step 3. Write SQL (Style Guide)

Purpose: Consistent, maintainable code

Checklist: Naming conventions, explicit JOINs, null handling, WHY comments, idempotent

Responsibility: Author

Example:
