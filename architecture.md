# SmartStock architecture and business invariants

## Logical architecture
Browser (Bootstrap/jQuery/AJAX) → MVC router and controllers → authentication/RBAC/CSRF → domain services → PDO repositories/models → MySQL InnoDB. Use existing class/table names and conventions after inspection. Controllers validate and authorize; services own business transactions; models handle persistence; audit and reconciliation cross-cut domains. Do not infer exact file paths or routes from this conceptual design.

## Inventory and pricing
One business, multiple internal locations; product base stock unit and product-specific conversion factors, snapshotted on transactions. Barcodes and versioned retail/wholesale prices. Owner controls price overrides; below-cost sales require approval. Quantity ledger immutable; balance rows are transactional projections. Available stock excludes quarantine and other unavailable stock. Never use floating point for financial math. Company-wide moving weighted average: KHR carrying values at 4 decimals and average unit cost at 6 decimals per established policy; preserve existing rounding and base quantity precision. Lock balances and costing rows using shared deterministic order. No invented historical values.

## Transactions
Receipts increase quantity and value; sales decrease quantity and record COGS, with snapshots. Confirmations and reversals are atomic and idempotent. Financial credit notes do not themselves move stock. Physical returns are distinct from refunds; eligible resellable sales returns restore original COGS basis, damaged/expired goods follow writeoff policy, quarantine is unavailable. Purchase returns remove stock at locked current carrying basis; Phase 5.7 compensating physical restoration uses original return carrying-value snapshot. Linked supplier credits block restoration until exact eligible quantity is released by Phase 5.8 compensation. Phase 5.8 adjusts AP/recoverables only, never cash or stock. Preserve original documents and separate financial from physical correction.

## Purchasing and finance
PO draft/submission/Owner approval, partial receipt, three-way supplier invoice matching, payable and payment allocations. Goods receipt alone does not create payable. Prevent double matching. Support KHR/USD, historical FX snapshots and explicit rounding, partial/split allocations, manual verification of bank/KHQR. Customer credit limits, due dates and overdue tracking. Payments settle balances, not revenue. Credits and corrections must reconcile and never generate unsupported cash refunds or negative recoverables. Staff cannot view finance/cost/profit information.

## Phase 6 inventory operations
Internal transfers use paired source/destination movements in one transaction; net business quantity/value and average cost unchanged. No sales/COGS/expenses. No implicit reservation or in-transit workflow unless separately approved. Later adjustments require reason and owner approval; counts require explicit scope, snapshot/cutoff, variance review and controlled adjustment posting. Batch/expiry and quarantine transitions require explicit rules before implementation.

## Future expense and fuel modules
Expenses: categories, budgets, recurring drafts, trends; separate cash movement from accrual and profit reporting. Fuel: one pump, two nozzles, gasoline/diesel; tank count/capacity and mapping unknown. Flexible shifts, opening/closing meter readings, price segments, Owner discrepancy review, integrated shared stock/valuation, no duplicate revenue or stock posting. Define exact business rules with Owner before implementation.

## Future decision support
Reorder recommendations are advisory, not automatic purchases. Use available inventory, outstanding inbound orders, net sales history, supplier lead time, safety stock, minimum order sizes and unit conversion. Handle insufficient history, returns, seasonality and stockouts explicitly. Report assumptions and avoid presenting invented demand forecasts as facts.

## Deployment (deferred)
Secure HTTPS mobile access; private DB; least privilege; secrets outside web root; encrypted off-site backups and tested restoration; staging migration and smoke tests before any production cutover. Hosting selection is not a current backend task. Main database migration remains blocked pending backup and explicit Owner approval.
