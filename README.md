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
