# CodingWorkflow
CodingWorkflow

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

WITH cost_by_period AS (
  SELECT cost_center_id, period_id, SUM(amount) AS total_cost
  FROM fct_gl
  WHERE period_id BETWEEN '2025Q1' AND '2025Q2'
  GROUP BY cost_center_id, period_id
)


Step 4. Self-Check

Purpose: Developer validates own work

Checklist: No SELECT *, clear aliases, edge case handling, performance-friendly, rollback defined

Responsibility: Author

Example: Found SELECT * → fixed to SELECT cost_center_id, amount. Added COALESCE(amount,0) for null safety.

Step 5. Peer Review

Purpose: Independent quality control

Checklist: 1 reviewer minimum (2 for critical SQL). Checks:

Code Quality (naming, formatting, readability, comments)

Business Logic (joins correct, null handling, aggregations accurate, no misuse of DISTINCT)

Performance & Safety (filters early, avoid Cartesian joins, runtime acceptable, re-run safe)

Responsibility: Peer Reviewer(s)

Example: Reviewer comment: “DISTINCT used to remove dupes. Should fix join condition instead.”

Step 6. Reviewer Approval

Purpose: Ensure peer validation loop

Checklist: Reviewer either approves or sends back with comments

Responsibility: Reviewer

Example: PR marked “Approved” in GitHub / Tagetik repo after issues fixed

Step 7. Static / Lint Checks

Purpose: Automated guardrails

Checklist: Style violations, anti-pattern detection

Responsibility: Reviewer / System

Example: SQL Linter flags: mixed casing → corrected to consistent UPPERCASE keywords

Step 8. Functional & Performance Tests

Purpose: Validate correctness & runtime

Checklist: Test matrix executed (happy path, edge cases, nulls, multi-entity). Runtime benchmarks recorded

Responsibility: Author + Reviewer

Example: Test: Input = 10 entities, 24 periods → runtime < 15 sec. Output totals match expected finance numbers.

Step 9. Approver Sign-off

Purpose: Final accountability

Checklist: Reviewer approval confirmed, tests passed, changelog entry updated

Responsibility: Approver (Team Lead / Module Owner)

Example: Approver notes: “Validated for Entity JP01 and CMG mapping. Safe to promote.”

End: Code Ready

Purpose: Safe for integration

Checklist: Traceability complete, documentation updated

Responsibility: Approver

Example: Change log entry: Ticket #1234 — Fixed CMG join logic in P&L query, reviewed & tested.
