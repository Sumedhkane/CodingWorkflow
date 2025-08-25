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
