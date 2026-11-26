# SmartStock task board

Baseline: reported Phase 5.8 PASS. This board is reconstructed from owner-provided reports, not a direct repository inspection. Agents must reconcile with local evidence before changing status.

| Phase | Scope | Status |
|---|---|---|
| 1 | Authentication, staff lifecycle, RBAC, audit | Reported PASS |
| 2 | Products, categories, units, conversions, barcodes, prices | Reported PASS |
| 3.1 | Stock receipts, immutable movements, balances | Reported PASS |
| 3.2 | Moving weighted average valuation | Reported PASS |
| 4.1 | Sales, COGS, voids | Reported PASS |
| 4.2 | Customer credit, payments, allocations | Reported PASS |
| 4.3 | Credit notes and refunds | Reported PASS |
| 4.4 | Physical sales returns and quarantine | Reported PASS |
| 5.1 | Suppliers and purchase orders | Reported PASS |
| 5.2 | Partial goods receiving | Reported PASS |
| 5.3 | Supplier invoices, three-way matching | Reported PASS |
| 5.4 | Supplier payments | Reported PASS |
| 5.5 | Supplier credits and payment corrections | Reported PASS |
| 5.6 | Purchase returns | Reported PASS |
| 5.7 | Physical purchase return corrections | Reported PASS |
| 5.8 | Linked supplier credit corrections | Reported PASS |
| 6.1 | Internal stock transfers | READY / local status unverified |
| 6.2 | Stock adjustments | Planned |
| 6.3 | Physical stock counting | Planned |
| 6.4 | Batch, expiry and quarantine disposition | Planned |
| 7.1 | Expenses and budgets | Planned |
| 7.2 | Profit, cash, stock and business reports | Planned |
| 8 | Fuel tanks, nozzles, shifts and reconciliation | Planned |
| 9 | Smart reorder recommendations and demand analytics | Proposed, owner approval required |
| 10 | Mobile UX, staging, backup/restore and deployment | Proposed, owner approval required |

## Current assignments
- [ ] Codex: inspect current work, then implement or finish Phase 6.1 using backend-task.md; if already implemented, verify rather than duplicate.
- [ ] Gemini: read-only frontend contract assessment using frontend-task.md; implementation on HOLD.
- [ ] Antigravity: independent Phase 6.1 review after backend handoff using review-task.md.
- [ ] Owner: review findings and authorize phase closure / next phase.

## Last reported verification
Phase 5.8: 26/26 checks; Phase 5.6/5.7: 164/164; Phase 1–5.7 regression exit 0; fresh schema plus 17 migrations; 123 PHP files syntax passed. Main DB unchanged; test DB cleaned. Phase 5.7 route tests used CLI router/controller harness, not external browser-driven tests.

## Deferred or unresolved
Broader supplier-credit reversals and separate settlement corrections; partial payment corrections where unsupported; in-transit returns; landed costs; historical valuation remediation; batch/expiry and quarantine disposition; exact fuel tank capacity and nozzle mapping; production migration and backup/restore; external-server HTTP tests. Confirm dependencies before implementing. Do not quietly treat deferred features as completed.
