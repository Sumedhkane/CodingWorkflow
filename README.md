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

Regression Pack (Maintenance)

Purpose: confirm the fix and nearby logic remain stable.

Checklist: original failing case passes; adjacent entities/periods stable; totals unchanged where expected.

Responsibility: Author + Reviewer.

Example: “Bug case JP01-Q2 fixed; JP02/US01 unaffected; total P&L equals prior release.”
