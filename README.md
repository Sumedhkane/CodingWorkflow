Row: Ticket Created

Purpose: establish scope, impact area(s), rollback.

Checklist: business context, affected forms/ETLs/reports, risk level, rollback path.

Responsibility: Author/Requester.

Example: “Bug: CMG mapping double counts for JP01 Q2; rollback = revert to tag v1.8.”

Row: Design Note (Enhancement)

Purpose: capture intended logic before coding.

Checklist: inputs (schema.table), joins/filters, outputs with 5–10 sample rows, edge cases, rollback.

Responsibility: Author; sanity check by peer.

Example: “Input fct_gl join dim_cmg on cmg_id; output P&L by cmg, period; handle NULL cmg_id → ‘UNASSIGNED’.”

Row: Reproduce Issue (Maintenance)

Purpose: prove the bug with minimal data.

Checklist: exact query, params (entity/period), expected vs actual, sample rows that fail.

Responsibility: Author.

Example: “For JP01 2025-Q2, cost_center 1102 appears twice after join to dim_proj.”

Row: Root Cause Isolation (Maintenance)

Purpose: pinpoint failing logic.

Checklist: row-count diffs per join, check DISTINCT usage, null/period boundary, non-sargable predicates.

Responsibility: Author + Reviewer (discussion).

Example: “LEFT JOIN on (cc_id, period_id) missing period predicate → dupes.”
