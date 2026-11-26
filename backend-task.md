# Codex — Phase 6.1 internal stock transfers

Read AGENTS.md, TASKS.md, architecture.md, actual Phase 1–5.8 code/docs and git status. If Phase 6.1 already exists, inspect and complete missing coverage rather than duplicate. Do not start Phase 6.2.

## Implementation
- Inspect shared inventory/valuation posting services, balance locking, units, locations, quarantine and availability policies. Document actual reusable APIs.
- Add forward-only migration and document/model/service/controller/routes following local patterns.
- Draft → submitted → approved → confirmed; rejection/cancellation before confirmation. Staff quantity-only draft/submit; Owner approve/confirm/reject/cancel and sensitive reconciliation. No stock changes before confirmation. Snapshot unit conversions and prevent unauthorized payload fields.
- Require distinct active eligible locations, eligible products and positive quantities. Reject insufficient available stock; handle repeated product lines by aggregating required base quantities. Do not let ordinary transfers bypass quarantine restrictions. Revalidate eligibility on posting; approval is not a reservation.
- Transactionally lock document, relevant balances and cost rows using existing shared deterministic order. Post paired immutable outbound/inbound movements with unique linkage and idempotency. Preserve total quantity, carrying value and moving average exactly; if valuation rows are required, offset at identical carrying basis, including rounding. No revenue, COGS, expenses or liability changes. Do not recalculate average from internal transfer legs. Roll back all business writes on failure.
- Read-only reconciliation: paired movement integrity, source/destination quantity, zero net valuation, duplicate/missing postings, audit trail. No silent repair.

## Acceptance tests
Single/multiple items, repeated product lines, conversions, same/inactive/ineligible locations, quarantine bypass, insufficient stock, approval without posting, duplicate posting, concurrent competing transfers and same-document race (independent connections), rollback after first movement, retry, quantity/value/average conservation, no financial side effects, actual route authentication/RBAC/CSRF/method restrictions, Staff privacy, reconciliation, full previous regression, fresh migration smoke, PHP syntax. Test only disposable schema with explicit safety checks; cleanup all fixtures.

## Handoff
Report actual files, migration order, API contract, business invariants, commands and results, concurrency/rollback proof, remaining gaps, test cleanup and main DB preservation. Update TASKS.md with evidence and request independent review. No UI redesign, in-transit transfers, transfer reversals, stock adjustment, counting, expenses or fuel implementation in this task. If posted transfer reversal is needed, document it as a separate proposed milestone.
